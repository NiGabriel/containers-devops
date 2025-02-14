# Use Maven as the base image
FROM maven:3.8.4-jdk-8-slim AS build

# Set working directory inside the container
WORKDIR /app

# Copy the source code to the container
COPY . .

# Build the application using Maven
RUN mvn clean package -DskipTests

# Use OpenJDK as the runtime environment
FROM openjdk:8-jre-slim

# Set working directory inside the container
WORKDIR /app

# Copy the compiled JAR file from the build stage
COPY --from=build /app/target/*.jar profile-service.jar

# Expose the application port
EXPOSE 8000

# Command to run the application
CMD ["java", "-jar", "profile-service.jar"]
