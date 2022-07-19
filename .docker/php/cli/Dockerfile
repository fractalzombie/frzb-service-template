FROM php:8.1-cli

ENV COMPOSER_ALLOW_SUPERUSER=1
ENV PATH=$HOME/.composer/vendor/bin:$PATH

# Download script to install PHP extensions and dependencies
ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

RUN chmod uga+x /usr/local/bin/install-php-extensions && sync

# install system utilities
RUN apk update && apk add --no-cache \
    sed \
    curl \
    nano \
    gnupg \
    zip unzip \
    git \
    netcat-openbsd \
    openssl

# Install dev libraries
RUN apk update && apk add --no-cache \
    icu-dev \
    libpq-dev \
    libxml2-dev \
    unixodbc-dev \
    librdkafka-dev

# Install PHP
RUN install-php-extensions \
    bcmath \
    bz2 \
    pcntl \
    calendar \
    exif \
    gd \
    intl \
    imagick \
    ldap \
    opcache \
    redis \
    soap \
    xsl \
    gmp \
    zip \
    sockets \
    amqp \
    pdo_pgsql \
    pgsql \
    rdkafka \
    xdebug

# Install Composer.
RUN mkdir -p $HOME/.composer \
 && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
 && ln -s $(composer config --global home) $HOME/.composer

# Install symfony cli
RUN curl -O https://get.symfony.com/cli/installer \
 && bash installer \
 && rm -f installer* \
 && mv $HOME/.symfony/bin/symfony /usr/local/bin/symfony \
 && rm -rf $HOME/.symfony

COPY ./conf/conf.d/docker-php-ext-xdebug.ini /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
COPY ./conf/conf.d/docker-php-ext-opcache.ini /usr/local/etc/php/conf.d/docker-php-ext-opcache.ini
COPY ./conf/php.development.ini /usr/local/etc/php/php.ini

WORKDIR /var/www/html
