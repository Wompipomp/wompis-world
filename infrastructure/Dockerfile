FROM maven:3.6-openjdk-11 AS BUILD_IMAGE

ENV APP_HOME=/build/
RUN mkdir -p $APP_HOME
COPY . $APP_HOME
WORKDIR $APP_HOME
RUN mvn clean install -DskipTests


FROM adoptopenjdk/openjdk11-openj9:alpine-slim
WORKDIR /app
COPY --from=BUILD_IMAGE /build/target/hello-world-0.0.1-SNAPSHOT.jar app.jar
RUN ls -l /app
ENTRYPOINT ["java","-jar", "app.jar"]




