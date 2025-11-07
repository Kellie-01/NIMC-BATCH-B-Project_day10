FROM maven:3.8.6-openjdk-11 as build

WORKDIR /app

COPY pom.xml .

COPY src ./src

RUN maven clean package -DskipTests

#Stage 2

FROM openjdk:11-jre-slim

WORKDIR /app

COPY --from=build /app/target/demo-1.0.0.jar app.jar
#COPY --from=build /app/target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT [ "java", "-jar", "app.jar" ]