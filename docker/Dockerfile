FROM php:7.4-alpine

RUN apk --no-cache add shadow && \
    groupmod -g 9999 xfs && groupmod -g 33 www-data && groupmod -g 82 xfs

RUN apk update

RUN apk add supervisor tzdata
COPY ./supervisord.conf /etc/
COPY ./php7.sh /etc/profile.d/php7.sh

RUN apk add nginx php7-fpm php7-mcrypt php7-openssl php7-gmp php7-pdo_odbc php7-json php7-dom php7-pdo php7-zip php7-mysqli php7-sqlite3 php7-apcu php7-pdo_pgsql php7-bcmath php7-gd php7-odbc php7-pdo_mysql php7-pdo_sqlite php7-gettext php7-xmlreader php7-xmlrpc php7-bz2 php7-iconv php7-pdo_dblib php7-curl php7-ctype

RUN chmod +x /etc/profile.d/php7.sh && /bin/sh /etc/profile.d/php7.sh

ENTRYPOINT /usr/bin/supervisord -c /etc/supervisord.conf
