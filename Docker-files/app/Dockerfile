FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/jenkin-app/techminds.git
RUN cd techminds && git checkout docker && mvn install

FROM tomcat:9-jre11
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE techminds/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 9080
CMD [ "catalina.sh", "run" ]
