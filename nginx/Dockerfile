FROM nginx:alpine

MAINTAINER Cliff Richard Anfone <anfone.cliff@gmail.com>

ADD nginx.conf /etc/nginx/

RUN apk update \
    && apk upgrade \
    && apk add --no-cache bash \
    && adduser -D -H -u 1000 -s /bin/bash www-data

ARG SSL_KEYS=/etc/nginx/ssl
ENV SSL_KEY_DIR ${SSL_KEYS}

USER root

COPY ./ssl_keys/. $SSL_KEY_DIR/

RUN if [ -f $SSL_KEY_DIR/* ]; then \
    chmod 600 $SSL_KEY_DIR/* \
;fi


# Set upstream conf and remove the default conf
RUN echo "upstream php-upstream { server php-fpm:9000; }" > /etc/nginx/conf.d/upstream.conf \
    && rm /etc/nginx/conf.d/default.conf

CMD ["nginx"]

EXPOSE 80 443
