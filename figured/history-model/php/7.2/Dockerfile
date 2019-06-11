FROM php:7.2
MAINTAINER Maximiliano Jimenez <jimenez@maximiliano.com.ar>

RUN apt-get update && apt-get install -y \
        git \
        curl \
        vim \
        zip \
        unzip \
        libxml2-dev

RUN docker-php-ext-install pdo pdo_mysql mbstring dom

RUN pecl install xdebug-beta \
    && docker-php-ext-enable xdebug

RUN curl https://raw.githubusercontent.com/php/php-src/e845291527f934db9fa4b001ad63651bd5bfb745/php.ini-development > /usr/local/etc/php/php.ini

RUN echo "xdebug.remote_enable=1" >> /usr/local/etc/php/php.ini
RUN echo "xdebug.remote_handler=dbgp" >> /usr/local/etc/php/php.ini
RUN echo "xdebug.remote_mode=req" >> /usr/local/etc/php/php.ini
RUN echo "xdebug.remote_connect_back=1" >> /usr/local/etc/php/php.ini
RUN echo "xdebug.remote_port=9001" >> /usr/local/etc/php/php.ini
RUN echo "xdebug.idekey=XDEBUG" >> /usr/local/etc/php/php.ini


RUN php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer