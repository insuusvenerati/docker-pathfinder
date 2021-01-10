FROM nginx:1.19.6-alpine

COPY --chown=nginx:nginx ./app /usr/share/nginx/html/
COPY ./.docker/nginx/nginx.conf /etc/nginx/nginx.conf
COPY ./.docker/nginx/pathfinder-http.conf /etc/nginx/conf.d/default.conf
COPY ./.docker/nginx/h5bp/ /etc/nginx/h5bp/
COPY ./.docker/nginx/mime.types /etc/nginx/mime.types

RUN mkdir -p /usr/share/nginx/html/logs

ENTRYPOINT ["nginx"]