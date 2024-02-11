FROM php:8.1-cli-bullseye

RUN pecl install opentelemetry-1.0.1 \
    && docker-php-ext-enable opentelemetry
