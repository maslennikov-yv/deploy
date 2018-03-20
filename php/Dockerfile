FROM php:7.2-fpm

RUN apt-get update && apt-get install -y \
    git vim sudo less libfreetype6-dev libpng-dev libjpeg62-turbo-dev libghc-postgresql-libpq-dev libgmp-dev \
    && ln -s /usr/include/x86_64-linux-gnu/gmp.h /usr/local/include/ \
    && docker-php-ext-configure gd --with-gd --with-freetype-dir=/usr/include/ --with-png-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-configure gmp \
    && docker-php-ext-install bcmath gd mbstring pdo opcache tokenizer zip \
    && docker-php-ext-install mysqli pdo_mysql gmp \
    && curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/bin/composer


RUN useradd -ms /bin/bash -p "openssl passwd -1 123456" -G sudo,www-data user