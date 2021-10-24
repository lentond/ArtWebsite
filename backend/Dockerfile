# Pulling in java development kit so container has all required dependencies
FROM openjdk:8-jre-alpine

# Can listen to the app on 8080
EXPOSE 8080

# Creating a folder called app
RUN mkdir /app

# Copying the packaged maven jar files into the app folder
COPY target/*.jar /app/spring-boot-application.jar

# On build, the first command to run will execute the jar file. The security property is included for faster startup - see https://stackoverflow.com/questions/58853372/what-exactly-does-djava-security-egd-file-dev-urandom-do-when-containerizi
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app/spring-boot-application.jar"]

# A health check that will kill the container if it fails. -q is a quiet flag for wget, -T is the timeout length, and the health check is performed every 1 minute.
HEALTHCHECK --interval=1m --timeout=3s CMD wget -q -T 3 -s http://localhost:8080 || exit 1
