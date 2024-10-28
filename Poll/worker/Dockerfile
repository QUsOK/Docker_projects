# First stage - Compilation
FROM maven:3.8.4-jdk-11-slim AS builder

# Set working directory
WORKDIR /app

# Copy only the pom.xml to optimize dependency resolution caching
COPY pom.xml .

# Resolve dependencies
RUN mvn dependency:resolve

# Copy the rest of the application source code
COPY src ./src

# Package the application
RUN mvn package

# Second stage - Runtime
FROM openjdk:11-jre-slim

# Set working directory
WORKDIR /app

# Copy the JAR file from the builder stage
COPY --from=builder /app/target/worker-jar-with-dependencies.jar .

# Command to run the application
CMD ["java", "-jar", "worker-jar-with-dependencies.jar"]
