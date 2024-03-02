FROM maven:3.6.3-jdk-11-slim AS build

COPY ./pom.xml /tmp/
COPY ./src /tmp/src/

WORKDIR /tmp/

RUN mvn package -DskipTests

FROM openjdk:11-jre-slim


COPY --from=build /tmp/target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]
