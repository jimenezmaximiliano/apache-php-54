FROM php:5.4-apache
MAINTAINER Maximiliano Jimenez <jimenez@maximiliano.com.ar>
RUN apt-get update && apt-get install -y \
        git \
        curl \
        php5-mcrypt \
    	php5-pgsql \
    	php5-sqlite \
    	php5-curl \
	php5-xdebug \
	zip \
	unzip \
	vim \
	php5-mysql
RUN docker-php-ext-install mysql mysqli pdo pdo_mysql
RUN apt-get update
RUN cp /usr/share/php5/php.ini-development /usr/local/etc/php/php.ini

RUN echo "xdebug.remote_enable=1" >> /usr/local/etc/php/php.ini
RUN echo "xdebug.remote_handler=dbgp" >> /usr/local/etc/php/php.ini
RUN echo "xdebug.remote_mode=req" >> /usr/local/etc/php/php.ini
RUN echo "xdebug.remote_connect_back=1" >> /usr/local/etc/php/php.ini
RUN echo "xdebug.remote_port=9001" >> /usr/local/etc/php/php.ini
RUN echo "xdebug.idekey=PHPSTORM" >> /usr/local/etc/php/php.ini

RUN a2enmod rewrite
RUN service apache2 restart

EXPOSE 80

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
