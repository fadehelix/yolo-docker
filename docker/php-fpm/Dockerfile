FROM php:7.0-fpm

RUN apt-get update && apt-get install -y \
	git \
	unzip \
	vim

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN docker-php-ext-install pdo pdo_mysql

#Symfony 3
RUN echo 'alias sf="php bin/console"' >> ~/.bashrc

WORKDIR /usr/local/apache2/htdocs
