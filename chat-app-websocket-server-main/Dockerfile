# Етап 1: Складання
FROM maven:3.9.6-eclipse-temurin-22-jammy AS build

WORKDIR /app

# Копіюємо ВСЕ (у випадку, якщо в тебе вкладена структура)
COPY chat-app-websocket-server-main/ .

# Явно вказуємо шлях до POM
RUN mvn -f pom.xml clean package -DskipTests

# Етап 2: Запуск
FROM openjdk:22-jdk

WORKDIR /app

# Копіюємо зібраний jar
COPY --from=build /app/target/websocket_demo-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]
