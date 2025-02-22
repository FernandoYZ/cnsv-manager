FROM php:8.3-fpm-alpine

# Instalar extensiones PHP necesarias para Laravel
RUN docker-php-ext-install pdo pdo_pgsql pcntl opcache

# Instalar Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

# Instalar dependencias del sistema y extensiones adicionales
RUN apk add --no-cache \
    nginx \
    supervisor \
    postgresql-client \
    redis \
    && pecl install redis \
    && docker-php-ext-enable redis

# Configuración de PHP para Laravel
COPY docker/php/php.ini /usr/local/etc/php/conf.d/laravel.ini

WORKDIR /var/www/html
