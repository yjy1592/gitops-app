FROM eclipse-temurin:17-jdk-jammy
WORKDIR /app

COPY pom.xml .
COPY .mvn .mvn
COPY mvnw .
RUN ./mvnw dependency:go-offline -B

COPY src ./src

RUN ./mvnw package -DskipTests

COPY ./ops-app/target/*.jar app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]