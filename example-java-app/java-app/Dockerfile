FROM maven:3-alpine AS build
COPY src /usr/src/app/src
COPY pom.xml /usr/src/app
RUN mvn -f /usr/src/app/pom.xml -B -DskipTests clean package

FROM gcr.io/distroless/java
COPY --from=build /usr/src/app/target/my-app-1.0-SNAPSHOT.jar /usr/src/app/target/my-app-1.0-SNAPSHOT.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/usr/src/app/target/my-app-1.0-SNAPSHOT.jar"]