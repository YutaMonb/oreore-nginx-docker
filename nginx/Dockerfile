FROM nginx:1.15.8-alpine

WORKDIR /etc/nginx/
RUN apk --update add openssl

RUN openssl genrsa 4096 > server.key
RUN openssl req -new -subj "/C=JP/ST=Hokkaido/L=Sapporosi/" -key server.key > server.csr
RUN openssl x509 -days 3650 -req -signkey server.key < server.csr > server.crt

COPY default.conf /etc/nginx/conf.d/default.conf

COPY web/ /var/www/html