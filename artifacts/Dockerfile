# Use an official maven runtime as a parent image
FROM maven:3.6.3-jdk-8

# Set the working directory in the container to /app
WORKDIR /app

# Add the current directory contents into the container at /app
ADD . /app

# Package the application
RUN mvn package

# Use an official Tomcat runtime as a base image
FROM tomcat:9.0.37-jdk8-openjdk

# Set the working directory in the container to /usr/local/tomcat/webapps
WORKDIR /usr/local/tomcat/webapps

# Copy the WAR file from the maven container
COPY --from=0 /app/target/*.war ./

# Make port 8080 available to the world outside this container
EXPOSE 8080

# Run the app when the container launches
CMD ["catalina.sh", "run"]