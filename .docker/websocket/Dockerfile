FROM composer as build

COPY . /var/www/websocket.pathfinder

WORKDIR /var/www/websocket.pathfinder
RUN composer install

FROM php:7.2.5-alpine

COPY --from=build /var/www/websocket.pathfinder /var/www/websocket.pathfinder

WORKDIR /var/www/websocket.pathfinder

CMD [ "php", "cmd.php" ]