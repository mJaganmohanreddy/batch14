#multistage Dockerfile

#BUILD STAGE1

FROM maven as buildstage
RUN mkdir /opt/mindcircuit13
WORKDIR /opt/mindcircuit13
COPY . .
RUN mvn clean install  #Generate artifact in this stage-- .war

#BUILD STAGE2

FROM tomcat
WORKDIR webapps
COPY --from=buildstage /opt/mindcircuit13/target/*.war .
RUN rm -rf ROOT && mv *.war ROOT.war
EXPOSE 8080
