FROM openjdk:8-jdk-alpine

COPY nginx.conf /etc/nginx/conf.d/default.conf

WORKDIR /usr/share/nginx/html
COPY src .

RUN mvn install

FROM openjdk:8-jre-alpine
WORKDIR /usr/share/nginx/html
COPY --from=build /usr/share/nginx/html/target/project.jar
CMD ["java -jar project.jar"]
