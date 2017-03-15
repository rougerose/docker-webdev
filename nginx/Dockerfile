FROM nginx:alpine

RUN apk add --no-cache \
    bash \
    nano

COPY ./default.conf /etc/nginx/conf.d/default.conf
