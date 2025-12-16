# Stage One - build
FROM maven:3.9-eclipse-temurin-17 AS build

WORKDIR /app

# Copy the pom then the src
COPY pom.xml .
COPY src ./src

# Build the application
RUN mvn clean package -DskipTests

# Stage Two - run
FROM eclipse-temurin:17-jre-alpine AS run

WORKDIR /app
# Copy the jar from build
COPY --from=build /app/target/docker-lab-0.0.1-SNAPSHOT.jar /app/

EXPOSE 8080

# Run the application
CMD ["java", "-jar", "./docker-lab-0.0.1-SNAPSHOT.jar"]
