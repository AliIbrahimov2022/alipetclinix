# Use the Ubuntu base image
FROM ubuntu

# Set the working directory in the container
WORKDIR /app

# Update package list and install necessary packages
RUN apt-get update && \
    apt-get install -y default-jdk maven git

# Set the JAVA_HOME environment variable
ENV JAVA_HOME /usr/lib/jvm/java-17-openjdk-amd64

# Clone the Spring Petclinic repository
RUN git clone https://github.com/spring-projects/spring-petclinic.git

# Change the working directory to the cloned repository
WORKDIR /app/spring-petclinic

# Modify the mvnw script to use the correct JAVA_HOME
RUN sed -i 's@/usr/lib/jvm/default-java@$JAVA_HOME@' mvnw

# Build the Spring Petclinic project using Maven
RUN ./mvnw package

# Expose port 8080 for the Spring Boot application
EXPOSE 8080

# Start the Spring Boot application when the container runs
CMD ["java", "-jar", "target/spring-petclinic-3.1.0-SNAPSHOT.jar"]
