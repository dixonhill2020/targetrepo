# Dockerfile for Java Web Application

FROM maven:3.6.3-jdk-8

# Copy the project files to the Docker image
COPY . /usr/src/app

# Set the working directory
WORKDIR /usr/src/app

# Build the project
RUN mvn clean install

# Use Tomcat to run the application
FROM tomcat:8.5.61-jdk8-openjdk

# Remove the default Tomcat applications
RUN rm -rf /usr/local/tomcat/webapps/*

# Copy the WAR file to the Tomcat webapps directory
COPY --from=0 /usr/src/app/target/*.war /usr/local/tomcat/webapps/ROOT.war

# Expose the Tomcat port
EXPOSE 8080

# Start Tomcat
CMD ["catalina.sh", "run"]