FROM python:slim

MAINTAINER Cliff Richard Anfone <anfone.cliff@gmail.com>

RUN pip install --upgrade --no-cache-dir awsebcli awscli
RUN apt-get -yqq update && apt-get -yqq install git-all


ARG SSH_KEYS=/root/.ssh
ENV SSH_KEY_DIR ${SSH_KEYS}

USER root

COPY ./ssh_keys/. $SSH_KEY_DIR/

RUN if [ -f $SSH_KEY_DIR/* ]; then \
    chmod 600 $SSH_KEY_DIR/* \
    && chmod 644 $SSH_KEY_DIR/*.pub \
;fi

WORKDIR /var/www

