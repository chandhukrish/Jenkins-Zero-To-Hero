# You can change this base image to anything else
# But make sure to use the correct version of Java
#FROM adoptopenjdk/openjdk11:alpine-jre

# Simply the artifact path
#ARG artifact=target/spring-boot-web.jar

#WORKDIR /opt/app

#COPY ${artifact} app.jar

# This should not be changed
#ENTRYPOINT ["java","-jar","app.jar"]



FROM adoptopenjdk/openjdk11:alpine-jre

# Added for Jenkins Docker agent support
RUN apk add --no-cache \
    bash \
    coreutils \
    procps \
    shadow \
    docker-cli

ARG artifact=target/spring-boot-web.jar

WORKDIR /opt/app

COPY ${artifact} app.jar

# Added to keep container alive for Jenkins
CMD ["tail","-f","/dev/null"]

ENTRYPOINT ["java","-jar","app.jar"]

