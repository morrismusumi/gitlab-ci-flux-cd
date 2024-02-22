# Use an official Maven image as the base image
FROM eclipse-temurin:17-jdk-jammy AS build
# Set the working directory in the container
WORKDIR /app
# Copy the project files to the container
ADD . .
# Build the application using Maven
RUN ./mvnw package
# RUN --mount=type=cache,target=/root/.m2 ./mvnw -f pom.xml clean package

# Use an official OpenJDK image as the base image
FROM openjdk:23-ea-5-jdk-slim-bookworm

# FROM alpine:3.19.0
# Set the working directory in the container
WORKDIR /app
# Copy the built JAR file from the previous stage to the container
COPY --from=build /app/target/*.jar .
# Set the command to run the application
CMD ["java", "-jar", "/app/spring-petclinic-3.2.0-SNAPSHOT.jar"]
