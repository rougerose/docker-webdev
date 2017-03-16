FROM nginx:alpine

RUN apk add --no-cache \
    bash \
    nano

COPY ./default.conf /etc/nginx/conf.d/default.conf

# commande pour une version debug
# les logs sont accessibles depuis docker logs
# CMD ["nginx-debug", "-g", "daemon off;"]
