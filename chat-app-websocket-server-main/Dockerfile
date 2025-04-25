FROM maven:3.9.6-eclipse-temurin-22-jammy AS build

WORKDIR /app
COPY . .
RUN mvn -f /app/chat-app-websocket-server-main/pom.xml clean package -DskipTests

FROM openjdk:22-jdk

WORKDIR /app
COPY --from=build /app/target/websocket_demo-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]