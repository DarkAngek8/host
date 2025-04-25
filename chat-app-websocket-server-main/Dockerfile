FROM maven:3.9.6-eclipse-temurin-22-jammy as build
COPY . .
RUN mvn -f /app/chat-app-websocket-server-main/pom.xml clean package -DskipTests

FROM openjdk:22-jdk
COPY --from=build /target/chat-app-websocket-server-main-0.0.1-SNAPSHOT.jar websocket_demo.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "websocket_demo.jar"]