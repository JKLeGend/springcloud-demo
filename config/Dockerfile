FROM airdock/oraclejdk:1.8

COPY target/config-0.0.1-SNAPSHOT.jar /opt/app/config-0.0.1-SNAPSHOT.jar
WORKDIR /opt/app
CMD ["java", "-jar", "config-0.0.1-SNAPSHOT.jar"]
