FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/devopshydclub/vprofile-project.git
RUN cd vporfile-project && git checkout docker && mvn install

FROM tomcat:9-jre11
FROM mysql:8.0.33
LABEL "Project"="Vprofile"
LABEL "Author"="Nikola"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vporfile-project/target/vporfile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD [ "catalina.sh","run" ]
