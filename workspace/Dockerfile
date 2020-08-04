ARG PHP_VERSION

FROM php:${PHP_VERSION}-fpm

COPY php.ini /usr/local/etc/php/

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y \
      git \
      curl \
      vim \
      zip \
      unzip \
    && apt-get clean
RUN docker-php-ext-install pdo_mysql

#Composer install
COPY --from=composer /usr/bin/composer /usr/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1

ENV COMPOSER_HOME /composer

ENV PATH $PATH:/composer/vendor/bin

WORKDIR /var/www