FROM airdock/oraclejdk:1.8

COPY target/hystrix-0.0.1-SNAPSHOT.jar /opt/app/hystrix-0.0.1-SNAPSHOT.jar
WORKDIR /opt/app
CMD ["java", "-jar", "hystrix-0.0.1-SNAPSHOT.jar"]
