# Use a base image with OpenJDK
FROM openjdk:17-jdk-slim

# Set the working directory inside the container
WORKDIR /app

# Copy the Maven wrapper files and source code to the container
COPY mvnw mvnw.cmd pom.xml ./
COPY .mvn .mvn
COPY src src

# Make the Maven wrapper executable
RUN chmod +x mvnw

# Build the application
RUN ./mvnw clean package -DskipTests

# Copy the JAR file to the container
RUN cp target/*.jar app.jar

# Expose the application's port
EXPOSE 8080

# Set the entry point for the container
ENTRYPOINT ["java", "-jar", "app.jar"]
