FROM maven:3.9.9-eclipse-temurin-17 AS build
WORKDIR /app
COPY pom.xml .
COPY search-service/pom.xml search-service/pom.xml
COPY search-service/src search-service/src
RUN mvn -pl search-service -am package -DskipTests
FROM eclipse-temurin:17-jre
COPY --from=build /app/search-service/target/search-service-1.0.0.jar /app.jar
EXPOSE 8081
ENTRYPOINT ["java","-jar","/app.jar"]
