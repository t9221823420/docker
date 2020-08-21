FROM php:7.4.2-fpm

RUN apt-get update && apt-get install -y \
		libfreetype6-dev \
		libjpeg62-turbo-dev \
		libmcrypt-dev \
		libwebp-dev  \
		libpng-dev \
		libxpm-dev \
		libzip-dev \
		libonig-dev \
		libpq-dev \
	&& docker-php-ext-configure gd \
		--with-freetype \
		--with-jpeg \
		--with-webp \
		--with-xpm \
    && docker-php-ext-install \
       	gd \
        zip \
        bcmath \
        opcache \
        mbstring \
        mysqli \
        pgsql \
        pdo \
        pdo_mysql \
        pdo_pgsql

# Install XDebug
RUN pecl install xdebug-2.9.1 \
    && docker-php-ext-enable xdebug

# Install Git
RUN apt-get install -y git

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer