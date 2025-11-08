FROM php:8.2-apache

# Instalamos extensiones necesarias para Symfony y MySQL
RUN apt-get update && apt-get install -y \
    libicu-dev \
    libpq-dev \
    git \
    unzip \
    zip \
    && docker-php-ext-install intl pdo pdo_mysql opcache \
    && a2enmod rewrite

# Instalar Node.js y npm
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - \
    && apt-get install -y nodejs \
    && npm install -g npm@latest

RUN npm install -g sass

# Configuración de Apache
COPY vhost.conf /etc/apache2/sites-available/000-default.conf

# Establecer directorio de trabajo
WORKDIR /var/www/html

# Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer
