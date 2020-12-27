FROM airdock/oraclejdk:1.8

COPY target/client-service-0.0.1-SNAPSHOT.jar /opt/app/client-service-0.0.1-SNAPSHOT.jar
COPY src/main/resources/agent /opt/app/agent
WORKDIR /opt/app
CMD ["java", "-javaagent:/opt/app/agent/skywalking-agent.jar", "-jar", "client-service-0.0.1-SNAPSHOT.jar"]
