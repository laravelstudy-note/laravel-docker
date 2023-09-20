# Dockerfile

FROM php:8.2-apache

# setup requiing
RUN apt-get update \
  && apt-get install -y \
        libmcrypt-dev \
        libpng-dev \
        apt-utils \
        default-mysql-client \
		libjpeg-dev \
		libfreetype6-dev \
		libonig-dev \
		git zip unzip \
  && docker-php-ext-install pdo_mysql mysqli mbstring iconv \
  && docker-php-ext-configure gd \
  && docker-php-ext-install -j$(nproc) gd \
  && apt-get install -y vim \
  && apt-get install -y git 

RUN usermod -u 1000 www-data \
  && groupmod -g 1000 www-data

# composer
RUN curl -S https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer \
    && composer self-update

# copy vhosts
ADD ./docker/php8/vhosts.conf /etc/apache2/conf-enabled/vhosts.conf

# mod rewrite
RUN a2enmod rewrite

WORKDIR /app

# restart apache2
RUN service apache2 restart