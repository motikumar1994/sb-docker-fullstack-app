FROM maven:3.9.6-eclipse-temurin-17-alpine AS build

WORKDIR /app

COPY pom.xml .
RUN mvn dependency:go-offline -B

COPY src ./src
RUN mvn clean package -DskipTests

FROM eclipse-temurin:17-jre-alpine

RUN addgroup -S appgroup && adduser -S appuser -G appgroup

WORKDIR /app

COPY --from=build /app/target/sb-jpa-crud-0.0.1-SNAPSHOT.jar app.jar

RUN chown -R appuser:appgroup /app
USER appuser

EXPOSE 8088

ENTRYPOINT ["java", "-jar", "app.jar"]