FROM tomcat:8.5.5-jre8

LABEL maintainer="sergey.rubtsov81@gmail.com"

COPY conf/tomcat-users.xml /usr/local/tomcat/conf/tomcat-users.xml
COPY conf/context.xml /usr/local/tomcat/webapps/manager/META-INF/context.xml

COPY spring-petclinic-2.0.0.BUILD-SNAPSHOT.jar /usr/local/tomcat/webapps/

EXPOSE 5000

WORKDIR /usr/local/tomcat