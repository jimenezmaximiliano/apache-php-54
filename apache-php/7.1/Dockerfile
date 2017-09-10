FROM php:7.1-apache
MAINTAINER Maximiliano Jimenez <jimenez@maximiliano.com.ar>
RUN apt-get update && apt-get install -y \
        git \
        curl \
        zip \
        unzip \
        vim \
        libpq-dev \
        libsqlite3-dev \
        libcurl4-openssl-dev

RUN docker-php-ext-install mysqli pdo pdo_mysql pgsql pdo_pgsql pdo_sqlite curl
RUN pecl install xdebug-2.5.0 \
    && docker-php-ext-enable xdebug

RUN curl https://raw.githubusercontent.com/php/php-src/0221e9f827632942225586687a33cfd554860d5e/php.ini-development > /usr/local/etc/php/php.ini

RUN echo "xdebug.remote_enable=1" >> /usr/local/etc/php/php.ini
RUN echo "xdebug.remote_handler=dbgp" >> /usr/local/etc/php/php.ini
RUN echo "xdebug.remote_mode=req" >> /usr/local/etc/php/php.ini
RUN echo "xdebug.remote_connect_back=1" >> /usr/local/etc/php/php.ini
RUN echo "xdebug.remote_port=9001" >> /usr/local/etc/php/php.ini
RUN echo "xdebug.idekey=PHPSTORM" >> /usr/local/etc/php/php.ini

RUN php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer

RUN a2enmod rewrite
RUN service apache2 restart

EXPOSE 80

RUN rm -f /var/run/apache2/apache2.pid

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
