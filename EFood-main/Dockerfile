# Use an official OpenJDK image as a parent image
FROM openjdk:17-jdk
# Set the working directory in the container
WORKDIR /app

# Copy only necessary files for Maven build
COPY pom.xml mvnw ./  
COPY .mvn .mvn

# Grant execution permission to the Maven wrapper script
RUN chmod +x mvnw

# Resolve dependencies (this step will cache dependencies)
RUN ./mvnw dependency:resolve

# Copy the rest of the application code
COPY src src

# Build the Spring Boot application
RUN ./mvnw clean package

# Expose the application port (default Spring Boot port is 8080)
EXPOSE 8080

# Run the Spring Boot application
CMD ["java", "-jar", "target/EFood-0.0.1-SNAPSHOT.jar"]
