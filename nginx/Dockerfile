FROM nginx:1.19.9

MAINTAINER Dirk Blicker <dirk.blicker@abus-kransysteme.de>

ARG nginxconf

RUN apt-get update

RUN apt-get install iputils-ping -y

RUN rm /etc/nginx/conf.d/default.conf

COPY config/$nginxconf /etc/nginx/nginx.conf

RUN rm -rf /etc/nginx/ssl

COPY config/ssl /etc/nginx/ssl

COPY config/mime.types /etc/nginx/mime.types

RUN mkdir /tmp/nginx && mkdir /tmp/nginx/cache
