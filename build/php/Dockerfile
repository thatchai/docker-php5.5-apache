FROM php:5.5-apache

COPY ./php.ini /usr/local/etc/php

RUN a2enmod rewrite expires
RUN apt-get update && apt-get install -y libmcrypt-dev libgeoip-dev \
    && pecl install geoip \
    && docker-php-ext-enable geoip

# images
RUN apt-get update \
    && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng12-dev \
    libgd-dev \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install \
      gd \
      exif
      
RUN docker-php-ext-install pdo_mysql mysqli mysql mbstring mcrypt
