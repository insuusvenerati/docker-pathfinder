# FROM composer as build
FROM php:7.2-fpm-alpine

COPY --chown=www-data:www-data ./app /usr/share/nginx/html
COPY ./.docker/php/environment.ini ./.docker/php/pathfinder.ini /usr/share/nginx/html/app/ 
WORKDIR /usr/share/nginx/html
RUN apk add --no-cache \
  curl-dev libpng-dev libevent-dev ${PHPIZE_DEPS} git nodejs npm libxml2-dev && \
  docker-php-ext-install sockets curl gd pdo_mysql zip xmlrpc

RUN pecl install -o -f redis event && \
  docker-php-ext-enable redis && \
  docker-php-ext-enable --ini-name zz-event.ini event

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer --version=1.6.3

RUN composer install
RUN chmod 0766 ./logs ./tmp