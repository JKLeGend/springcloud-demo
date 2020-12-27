FROM airdock/oraclejdk:1.8

COPY target/gateway-0.0.1-SNAPSHOT.jar /opt/app/gateway-0.0.1-SNAPSHOT.jar
WORKDIR /opt/app
CMD ["java", "-jar", "gateway-0.0.1-SNAPSHOT.jar"]
