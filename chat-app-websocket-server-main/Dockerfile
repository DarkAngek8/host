# Етап 1: Збираємо додаток
FROM maven:3.9.6-eclipse-temurin-22-jammy AS build

WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

# Етап 2: Створюємо образ для запуску
FROM openjdk:22-jdk

WORKDIR /app

# ТУТ ЗАМІНИ НАЗВУ jar файлу НА ПРАВИЛЬНУ!
COPY --from=build /app/target/chat-app-websocket-server-main-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]
