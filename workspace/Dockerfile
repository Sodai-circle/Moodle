ARG PHP_VERSION

FROM php:${PHP_VERSION}-fpm

COPY php.ini /usr/local/etc/php/

RUN apt-get update && \
    apt-get upgrade -y && \
    apt install -y graphviz \
     aspell \
     ghostscript \
     clamav &&\
    apt-get install -y \
      git \
      curl \
      vim \
      zip \
      unzip \
      libzip-dev \
      libpng-dev \
      libicu-dev \
      libxml2-dev \
    && apt-get clean
RUN docker-php-ext-install pdo_mysql zip gd intl xmlrpc soap mysqli opcache

RUN cd /opt && \
    git clone git://git.moodle.org/moodle.git && \
    cd moodle && \
    git branch --track MOODLE_39_STABLE origin/MOODLE_39_STABLE && \
    git checkout MOODLE_39_STABLE && \
    mkdir /var/moodledata

WORKDIR /var/www/html