FROM php:5.6.30-fpm

RUN usermod -u 1000 www-data
RUN cd /var/www && mkdir -p cache data logs && chown -R www-data:www-data cache data logs

RUN apt-get update && apt-get install -y libpq-dev zlib1g-dev

RUN docker-php-ext-install pdo pdo_mysql zip opcache

COPY config/php.ini /usr/local/etc/php/php.ini.config
RUN cd /usr/local/etc/php && cat php.ini.config >> php.ini

RUN pecl install -o -f xdebug && docker-php-ext-enable xdebug
COPY config/docker-php-ext-xdebug.ini /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

WORKDIR /var/www/ist-env-emulator
