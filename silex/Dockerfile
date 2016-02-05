FROM php:5.6-cli

RUN apt-get update && apt-get install -y git zip zlib1g-dev && \
    docker-php-ext-install -j$(nproc) zip

ONBUILD WORKDIR /code
ONBUILD ADD . /code

ONBUILD RUN curl -sS https://getcomposer.org/installer | php && \
            mv composer.phar composer && \
            php composer install

WORKDIR /code
ADD . /code

RUN curl -sS https://getcomposer.org/installer | php && \
            mv composer.phar composer && \
            php composer install

# ONBUILD RUN php -S 0.0.0.0:8080 -t public index.php

