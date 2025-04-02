FROM composer AS composer


FROM php:8.2-cli

COPY --from=composer /usr/bin/composer /usr/bin/composer

WORKDIR /app
RUN cd /app
COPY . .

RUN apt-get update \
    && apt-get install -y \
    libicu-dev libzip-dev \
    && docker-php-ext-enable opcache \
    && docker-php-ext-install pdo_mysql intl zip -j$(nproc) \
    && apt-get autoclean -y \
    && rm -rf /var/lib/apt/lists/*

RUN apt-get update \
    && apt-get install -y "$(cat add_pkgs | head -n 1)" || true \
    && docker-php-ext-enable "$(cat enable_ext | head -n 1)" || true \
    && docker-php-ext-enable "$(cat install_ext | head -n 1)" || true \
    && apt-get autoclean -y \
    && rm -rf /var/lib/apt/lists/*

CMD php spark serve --port 80 --host 0.0.0.0
