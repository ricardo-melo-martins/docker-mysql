
ARG MYSQL_VERSION=8.0.31
FROM "mysql:${MYSQL_VERSION}"

ENV DEBIAN_FRONTEND noninteractive

# RUN apt-get update \
#     && apt-get install -y wget unzip
#     && wget http://downloads.mysql.com/docs/sakila-db.zip \
#     && unzip sakila-db.zip

ARG PATH_SCRIPTS=/.rmm/.docker/mysql/script

COPY ${PATH_SCRIPTS}/sakila/1.4/sakila-schema.sql /docker-entrypoint-initdb.d/01_sakila-schema.sql
COPY ${PATH_SCRIPTS}/sakila/1.4/sakila-data.sql /docker-entrypoint-initdb.d/02_sakila-data.sql

#####################################
# Set Timezone
#####################################

ARG TZ=UTC
ENV TZ ${TZ}
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone \
&& chown -R mysql:root /var/lib/mysql/

# RUN apt-get update \
#  && apt-get install --no-install-recommends -y \
#   locales \
#  && rm -rf /var/lib/apt/lists/*

# COPY /script/my.cnf /etc/mysql/conf.d/my.cnf

# RUN chmod 0444 /etc/mysql/conf.d/my.cnf

# CMD ["mysqld"]

# EXPOSE 3306/tcp