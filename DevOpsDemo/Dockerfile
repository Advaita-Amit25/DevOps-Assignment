#FROM Openjdk:17
#EXPOSE 8090
#ADD target/DevOpsDemo-0.0.1-SNAPSHOT.jar DevOpsDemo-0.0.1-SNAPSHOT.jar
#ENTRYPOINT ["java","-jar","/DevOpsDemo-0.0.1-SNAPSHOT.jar" ]

FROM amazoncorretto:17-alpine3.18-full

WORKDIR app/

COPY ./target/*.jar ./

EXPOSE 8090

CMD ["java", "-jar", "DevOpsDemo-0.0.1-SNAPSHOT.jar"]
