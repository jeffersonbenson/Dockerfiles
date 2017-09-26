FROM php:7.1-apache
MAINTAINER Jeff Benson <jbenson14@liberty.edu>

#basic installation of necessities + PHP framework
RUN apt update && apt full-upgrade -y && \
 	apt install -y \
	bash \
	build-essential \
	curl \
	gcc \
	git \
	libaio1 \
	libzip-dev \
	nodejs \
	npm \
	unzip \
	unixodbc-dev

RUN curl -sS https://getcomposer.org/installer | php && \
	mv composer.phar /usr/local/bin/composer && \
	ln -s ~/.composer/vendor/bin/* /usr/local/bin/

#Running Laravel Proper
RUN pecl install zip && \
	docker-php-ext-enable zip
RUN composer global require 'laravel/installer'
#RUN composer create-project laravel/laravel /var/www/laravel

#Installing Oracle Instant Client
COPY instantclient_12_*.zip ./
RUN unzip instantclient_12_2.zip -d /usr/local/ && \
	unzip instantclient_12_sdk.zip -d /usr/local && \
	ln -s /usr/local/instantclient_12_2 /usr/local/instantclient && \
	ln -s /usr/local/instantclient_12_2/libclntsh.so.12.1 /usr/local/instantclient_12_2/libclntsh.so

ENV ORACLE_BASE /usr/local/instantclient
ENV LD_LIBRARY_PATH /usr/local/instantclient
ENV TNS_ADMIN /usr/local/instantclient
ENV ORACLE_HOME /usr/local/instantclient

RUN echo 'instantclient,/usr/local/instantclient' | pecl install oci8 && \
	docker-php-ext-enable oci8 && \
	pecl install pdo_sqlsrv && \
	docker-php-ext-enable pdo_sqlsrv

EXPOSE 80 443

WORKDIR /var/www/laravel/

VOLUME /var/www/laravel/

ENTRYPOINT php ./artisan serve --port=80 --host=0.0.0.0
