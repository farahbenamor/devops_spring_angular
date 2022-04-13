FROM maven:3.8.3-jdk-11-slim
RUN apt update && apt install curl -y \
        && rm -rf /var/lib/apt/lists/*          
WORKDIR /app
COPY pom.xml .
COPY src src
RUN mvn -Ptest dependency:go-offline
RUN mvn -Ptest clean package -DskipTests
#ADD target/spring-boot-server-0.0.1-SNAPSHOT.jar  sspring-boot-server-0.0.1-SNAPSHOT.jar
EXPOSE 8080
HEALTHCHECK --interval=30s --timeout=3s \
  CMD curl -f http://localhost:8080/MeExt/api/v1/ || exit 1
ENTRYPOINT ["java", "-jar", "target/spring-boot-data-jpa-0.0.1-SNAPSHOT.jar"]
