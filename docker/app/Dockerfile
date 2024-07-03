FROM php:8-apache

WORKDIR /var/www/html

# PHP で必要なライブラリをインストール
RUN apt-get update \
    && apt-get install -y libonig-dev libzip-dev unzip mariadb-client \
    && docker-php-ext-install mbstring zip bcmath pdo_mysql mysqli \
    && pecl install xdebug \
    && docker-php-ext-enable xdebug

# mod_rewrite モジュールを使えるようにする
RUN a2enmod rewrite include

# Apache の設定を更新して SSI を有効にする
RUN echo "AddType text/html .shtml" >> /etc/apache2/apache2.conf \
    && echo "AddOutputFilter INCLUDES .shtml" >> /etc/apache2/apache2.conf


# composer のインストール
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer
ENV COMPOSER_ALLOW_SUPERUSER 1

# ファイルのコピー
COPY ./hogehoge /var/www/html
COPY ./docker/app/php.ini /usr/local/etc/php/php.ini
COPY ./docker/app/xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini
