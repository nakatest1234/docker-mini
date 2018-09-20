FROM php:5.6-fpm
MAINTAINER nakatest1234 <ambient2step@gmail.com>

# GD
# mcrypt
# memcached
RUN apt-get update -yqq \
  && apt-get install -yqq --no-install-recommends \
       libjpeg-dev libjpeg62-turbo-dev libpng12-dev libfreetype6-dev \
       libmcrypt-dev \
       libz-dev libmemcached-dev libmemcached11 libmemcachedutil2 build-essential \
       libssl-dev \
       libgpgme11-dev \
       libxml2-dev php-soap \
  && apt-get clean -yqq

# GD
# mysql
RUN docker-php-ext-configure gd        --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/
RUN docker-php-ext-configure mysql     --with-mysql=mysqlnd
RUN docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd
RUN docker-php-ext-configure opcache   --enable-opcache

# GD
# mcrypt
# mbstring
# bcmath
# opcache
# mysql
RUN docker-php-ext-install -j$(nproc) \
        gd \
        mbstring \
        mysql \
        pdo_mysql \
        mcrypt \
        bcmath \
        opcache \
        soap \
        zip \
        ftp

RUN pecl install memcached-2.2.0 && docker-php-ext-enable memcached
RUN pecl install gnupg && docker-php-ext-enable gnupg
RUN pecl install APCu-4.0.10 && docker-php-ext-enable apcu && echo "apc.enable_cli=1\napc.filters="'"^phar://"' >> /usr/local/etc/php/conf.d/docker-php-ext-apcu.ini
