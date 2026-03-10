# PHP-FPM
FROM php:8.4-fpm

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

RUN docker-php-ext-install zip pdo pdo_pgsql

# Munkakönyvtár
WORKDIR /var/www
COPY ./backend /var/www

# TMPDIR beállítása
ENV TMPDIR=/tmp
RUN mkdir -p /tmp && chmod 777 /tmp

# Composer telepítés
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Indító parancs
CMD ["php-fpm"]