FROM maven:3.9.9-eclipse-temurin-17 AS build
WORKDIR /app
COPY pom.xml .
COPY ingest-service/pom.xml ingest-service/pom.xml
COPY ingest-service/src ingest-service/src
RUN mvn -pl ingest-service -am package -DskipTests
FROM eclipse-temurin:17-jre
COPY --from=build /app/ingest-service/target/ingest-service-1.0.0.jar /app.jar
EXPOSE 8082
ENTRYPOINT ["java","-jar","/app.jar"]
