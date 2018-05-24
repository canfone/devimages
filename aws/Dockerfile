FROM python:slim

MAINTAINER Cliff Richard Anfone <anfone.cliff@gmail.com>

RUN pip install --upgrade --no-cache-dir awsebcli awscli
RUN apt-get -yqq update && apt-get -yqq install git-all

WORKDIR /var/www

