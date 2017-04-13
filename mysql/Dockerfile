FROM mysql:5.6.35

RUN apt-get update && apt-get install curl -y  && rm -rf /var/lib/apt/lists/*

USER mysql
ENTRYPOINT ["docker-entrypoint.sh"]

EXPOSE 3306
CMD ["mysqld"]