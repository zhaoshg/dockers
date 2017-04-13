FROM  tomcat:8.0.43-jre8-alpine


RUN apk add --no-cache curl

WORKDIR $CATALINA_HOME
EXPOSE 8080
CMD ["catalina.sh", "run"]