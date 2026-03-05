# PHP-FPM
FROM php:8.3-fpm

# Rendszer csomagok és PHP extensionök telepítése (ZIP, CURL, GIT, PostgreSQL)
RUN apt-get update && apt-get install -y \
    libzip-dev \
    zip \
    libpq-dev \
    curl \
    git \
    bash \
    unzip \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*
# Törli a felesleges dolgokat -> apg-get clean ....


RUN docker-php-ext-install zip pdo pdo_pgsql

# Munkakönyvtár beállítása
WORKDIR /var/www

# Composer telepítés | Másik módszerrel:
# COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
