FROM eclipse-temurin:17-jdk-jammy
WORKDIR /app

COPY ops-app/pom.xml .
COPY ops-app/.mvn ./.mvn
COPY ops-app/mvnw .

RUN chmod +x mvnw
RUN ./mvnw dependency:go-offline -B
COPY ops-app/src ./src

RUN ./mvnw package -DskipTests

COPY ./ops-app/target/*.jar app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]