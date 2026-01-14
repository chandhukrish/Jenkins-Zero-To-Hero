# You can change this base image to anything else
# But make sure to use the correct version of Java
#FROM adoptopenjdk/openjdk11:alpine-jre

# Simply the artifact path
#ARG artifact=target/spring-boot-web.jar

#WORKDIR /home/app

#COPY ${artifact} app.jar

# This should not be changed
#ENTRYPOINT ["java","-jar","app.jar"]




# -------- BUILD STAGE --------
FROM maven:3.9.6-eclipse-temurin-11 AS build

WORKDIR /build
COPY pom.xml .
RUN mvn dependency:go-offline

COPY src ./src
RUN mvn clean package -DskipTests

# -------- RUNTIME STAGE --------
FROM adoptopenjdk/openjdk11:alpine-jre

WORKDIR /opt/app
COPY --from=build /build/target/spring-boot-web.jar app.jar

ENTRYPOINT ["java","-jar","app.jar"]


