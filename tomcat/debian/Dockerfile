FROM debian:jessie-slim

ADD jre-8u121-linux-x64.tar.gz /usr/local/
ADD tomcat.8.5.13.tar.gz /usr/local/
ADD sources.list /etc/apt/

RUN apt-get update && apt-get install curl -y  && rm -rf /var/lib/apt/lists/*

ENV JAVA_HOME /usr/local/jre1.8.0_121
ENV JRE_HOME $JAVA_HOME
ENV CLASSPATH .:$JAVA_HOME/lib:$JRE_HOME/lib
ENV PATH $PATH:$JAVA_HOME/bin
ENV CATALINA_HOME /usr/local/tomcat

EXPOSE 8080

CMD ["/usr/local/tomcat/bin/catalina.sh","start"]