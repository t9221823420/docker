#https://github.com/ezsystems/docker-php/blob/master/php/Dockerfile-5.6
#https://github.com/Genentech/docker-php/blob/master/5.6-fpm/Dockerfile - example of ext lists
FROM php:5.6.34-fpm

RUN apt-get update && apt-get dist-upgrade -y && apt-get install --no-install-recommends -y \
		libfreetype6-dev \
		libjpeg62-turbo-dev \
		libmcrypt-dev \
		libwebp-dev  \
		libpng-dev \
		libxpm-dev \
		libzip-dev \
		libonig-dev \
		libssl-dev \
		libpq-dev \
    && docker-php-source extract \
    && docker-php-ext-configure mysqli --with-mysqli=mysqlnd \
    && docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd \
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
RUN pecl install xdebug-2.5.5 \
    && docker-php-ext-enable xdebug

# Install Git
RUN apt-get install -y git

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer