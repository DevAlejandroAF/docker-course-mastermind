# FROM ubuntu:22.04
#
# ENV DEBIAN_FRONTEND noninteractive
# ENV TZ America/Bogota
#
# RUN apt update && apt-get install -y \
#     curl \
#     unzip \
#     php8.1 \
#     php8.1-curl \
#     php8.1-xml
#
# RUN curl -sS https://getcomposer.org/installer \
#     | php -- --install-dir=/usr/bin/ --filename=composer
#
# WORKDIR /app
# COPY composer.* ./
# RUN composer install --no-scripts
# COPY . .
#
# EXPOSE 8000
#
# CMD php artisan serve --host 0.0.0.0

# Php image
FROM php:8.1

ENV TZ America/Bogota

RUN apt update && apt-get install -y unzip

COPY --from=composer /usr/bin/composer /usr/bin/composer

WORKDIR /app
COPY composer.* ./
RUN composer install --no-scripts
COPY . .

EXPOSE 8000

CMD php artisan serve --host 0.0.0.0
