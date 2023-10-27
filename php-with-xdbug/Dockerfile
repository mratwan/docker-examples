FROM php:fpm-alpine

# Install linux tools
RUN apk update && apk add --no-cache \
    autoconf gcc make g++ \
    ca-certificates \
    bash \
    curl \
    tar \
    xz \
    openssl \
    zip unzip libzip-dev\
    git \
    && rm -rf /var/cache/apk/* \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install X-Debug php extension
RUN pecl install -o -f xdebug-3.0.0 \
    && rm -rf /tmp/pear

# Enable X-Debug php extensison
RUN docker-php-ext-enable xdebug

COPY . /app
WORKDIR /app

CMD ["php-fpm"]

EXPOSE 9000
EXPOSE 9003