FROM maven:3.9.6-amazoncorretto-17-debian as build

COPY src /app/src
COPY pom.xml /app

WORKDIR /app
RUN mvn clean install

FROM amazoncorretto:17

COPY --from=build /app/target/service-main-0.0.1-SNAPSHOT.jar /app/app.jar

WORKDIR /app

EXPOSE 8888

CMD ["java", "-jar", "app.jar"]