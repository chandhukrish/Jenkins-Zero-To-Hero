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


# Stage 1: Build with Maven
FROM maven:3.9.11-eclipse-temurin-11 AS build

WORKDIR /workspace

# Copy the project files
COPY pom.xml .
COPY src ./src

# Build the jar
RUN mvn clean package -DskipTests

# Stage 2: Runtime minimal image
FROM eclipse-temurin:11-jre-alpine

WORKDIR /opt/app

# Copy the jar from the build stage
COPY --from=build /workspace/target/spring-boot-web.jar app.jar

# Run the application
ENTRYPOINT ["java","-jar","app.jar"]

