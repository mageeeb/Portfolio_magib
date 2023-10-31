FROM php:8.1-apache

ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

RUN chmod +x /usr/local/bin/install-php-extensions && \
    install-php-extensions pdo_pgsql intl

COPY --from=composer /usr/bin/composer /usr/bin/composer

FROM node:lts-slim as base
ENV NODE_ENV=production
ENV HOST 0.0.0.0
WORKDIR /app
COPY package*.json .
RUN npm config list
RUN npm ci --force \
    && npm cache clean --force



COPY . /var/www/