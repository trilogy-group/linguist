FROM ubuntu:16.04

ENV LANG=C.UTF-8

RUN apt-get update \
 && apt-get install -y build-essential \
     cmake \
     git \
     libcurl4-openssl-dev \
     libicu-dev \
     libssl-dev \
     pkg-config \
     ruby-full \
     zlib1g \
     zlib1g-dev \
     zlibc \
 && apt-get clean \
 && ln -s /usr/bin/make /usr/bin/gmake \
 && echo bundler-1.10 > .rbenv-gemsets \
 && gem install bundler -v 1.10.6 \
 && rm -f .rbenv-gemsets

WORKDIR /data

CMD tail -f /dev/null
