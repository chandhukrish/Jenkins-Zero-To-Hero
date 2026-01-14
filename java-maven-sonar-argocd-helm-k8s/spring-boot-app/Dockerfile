# You can change this base image to anything else
# But make sure to use the correct version of Java
#FROM adoptopenjdk/openjdk11:alpine-jre

#RUN apt-get update && apt-get install -y maven

# Simply the artifact path
#ARG artifact=target/spring-boot-web.jar

#WORKDIR /opt/app

#COPY ${artifact} app.jar

# This should not be changed
#ENTRYPOINT ["java","-jar","app.jar"]







# Use Alpine-based OpenJDK 11 image
FROM eclipse-temurin:11-jdk-alpine

# Install Maven and bash (bash is optional, but helpful for debugging)
RUN apk add --no-cache maven bash


# Set the working directory inside the container
WORKDIR /opt/app

# Pass the artifact path as a build argument
ARG artifact=target/spring-boot-web.jar

# Copy your Spring Boot JAR into the container
COPY ${artifact} app.jar

# Run the JAR
ENTRYPOINT ["java","-jar","app.jar"]

