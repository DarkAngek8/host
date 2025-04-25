FROM maven:3.9.6-eclipse-temurin-22-jammy AS build

WORKDIR /app

# Копіюємо тільки ВСЕ що всередині проекту
COPY chat-app-websocket-server-main/ .

RUN mvn clean package -DskipTests

FROM openjdk:22-jdk

WORKDIR /app

COPY --from=build /app/target/chat-app-websocket-server-main-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]
