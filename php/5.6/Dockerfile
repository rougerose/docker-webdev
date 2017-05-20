FROM php:5-fpm-alpine

RUN apk add --no-cache \
        bash \
        freetype-dev libjpeg-turbo-dev libpng-dev libxslt-dev libintl icu icu-dev libxml2-dev \
        && docker-php-ext-configure gd --with-freetype-dir=/usr/include --with-png-dir=/usr/include --with-jpeg-dir=/usr/include \
        && NPROC=$(getconf _NPROCESSORS_ONLN) \
        && pecl install xdebug \
        && docker-php-ext-enable xdebug \
        && docker-php-ext-install -j${NPROC} iconv intl gd xsl mysql pdo_mysql mysqli \
        # xdebug config
        && echo "xdebug.remote_enable=on" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
        && echo "xdebug.remote_autostart=off" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
        && echo "xdebug.remote_port=9000" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
        && echo "xdebug.remote_handler=dbgp" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
        && echo "xdebug.remote_connect_back=0" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

COPY ./php.ini /usr/local/etc/php/conf.d/php.ini

ENV TZ=Europe/Paris

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
