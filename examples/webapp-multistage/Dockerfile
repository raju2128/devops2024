FROM ubuntu:latest AS build
WORKDIR /app
RUN apt-get update && \
    apt-get install -y openjdk-11-jre maven
COPY . /app
RUN mvn clean package && \
    cp ./target/spring-boot-web.jar .

FROM adoptopenjdk/openjdk11:latest
WORKDIR /app
COPY --from=build /app /app
EXPOSE 8080
ENTRYPOINT ["java","-jar","spring-boot-web.jar"]
