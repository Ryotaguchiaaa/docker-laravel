FROM php:7.3-fpm
#phpを7.3以上にしないど"laravel new"が使えないので7.3を指定
COPY php.ini /usr/local/etc/php/

RUN apt-get update \
  && apt-get install -y zlib1g-dev mariadb-client libzip-dev\
  && docker-php-ext-install zip pdo_mysql 
#Composer install
COPY --from=composer /usr/bin/composer /usr/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1

ENV COMPOSER_HOME /composer

ENV PATH $PATH:/composer/vendor/bin


WORKDIR /var/www
#userを追加
#/var/wwwにnginx(webserver)でアクセスできるようにする
USER www-data
RUN chown -R www-data:www-data /var/www/


RUN composer global require "laravel/installer"
