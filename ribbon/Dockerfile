FROM airdock/oraclejdk:1.8

COPY target/ribbon-0.0.1-SNAPSHOT.jar /opt/app/ribbon-0.0.1-SNAPSHOT.jar
WORKDIR /opt/app
CMD ["java", "-jar", "ribbon-0.0.1-SNAPSHOT.jar"]
