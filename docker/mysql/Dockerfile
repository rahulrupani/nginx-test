FROM mysql:5.7

LABEL maintainer=kuldeep@gmail.com
ARG DOCKER_ARTIFACT_DIR=./docker

### MySql Config ###
COPY $DOCKER_ARTIFACT_DIR/mysql/startup /etc/mysql/startup
COPY $DOCKER_ARTIFACT_DIR//mysql/my.cnf /etc/mysql/conf.d/my.cnf

RUN chown -R mysql:root /var/lib/mysql/

ARG MYSQL_DATABASE=homestead
ARG MYSQL_USER=homestead
ARG MYSQL_PASSWORD=secret
ARG MYSQL_ROOT_PASSWORD=root

ENV MYSQL_DATABASE=$MYSQL_DATABASE
ENV MYSQL_USER=$MYSQL_USER
ENV MYSQL_PASSWORD=$MYSQL_PASSWORD
ENV MYSQL_ROOT_PASSWORD=$MYSQL_ROOT_PASSWORD

RUN sed -i 's/MYSQL_DATABASE/'$MYSQL_DATABASE'/g' /etc/mysql/startup && \
    sed -i 's/MYSQL_USER/'$MYSQL_USER'/g' /etc/mysql/startup && \
    sed -i 's/MYSQL_PASSWORD/'$MYSQL_PASSWORD'/g' /etc/mysql/startup

### Initialize DB ###
CMD ["mysqld", "--init-file=/etc/mysql/startup"]

### Expose ports ###
EXPOSE 3306
