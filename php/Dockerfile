  FROM php:7.4-fpm
    RUN usermod -u 1000 www-data \
    && echo "deb http://mirrors.aliyun.com/debian/ buster main non-free contrib \n \
    deb-src http://mirrors.aliyun.com/debian/ buster main non-free contrib \n \
    deb http://mirrors.aliyun.com/debian-security buster/updates main \n \
    deb-src http://mirrors.aliyun.com/debian-security buster/updates main \n \
    deb http://mirrors.aliyun.com/debian/ buster-updates main non-free contrib \n \
    deb-src http://mirrors.aliyun.com/debian/ buster-updates main non-free contrib \n \
    deb http://mirrors.aliyun.com/debian/ buster-backports main non-free contrib \n \
    deb-src http://mirrors.aliyun.com/debian/ buster-backports main non-free contrib" > /etc/apt/sources.list \
    && apt-get update \
    && apt-get install -y \
    build-essential \
    libmagickcore-dev \
    libmagickwand-dev \
    imagemagick \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng-dev \
    libzip-dev \
    && docker-php-ext-configure gd  --with-jpeg=/usr/include --with-freetype=/usr/include/freetype2/ \
    && docker-php-ext-install -j$(nproc) bz2 zip gd iconv pdo_mysql mysqli bcmath calendar exif gettext sockets dba  pcntl  shmop sysvmsg sysvsem sysvshm \
    && pecl install redis-5.1.1 \
    && pecl install imagick \
    && pecl install mcrypt \
    && docker-php-ext-enable redis imagick mcrypt