# Dockerfile for Java-based web application

FROM maven:3.6.3-jdk-8

# Copy the project files to the Docker image
COPY . /app

# Set the working directory
WORKDIR /app

# Build the project
RUN mvn clean install

# Expose the application port
EXPOSE 8080

# Run the application
CMD ["java", "-jar", "target/legacy-app-1.0-SNAPSHOT.jar"]