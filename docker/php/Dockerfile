FROM php:8.3-fpm

RUN apt update && apt-get install -y \
    sshpass \
    procps \
    acl \
    apt-transport-https \
    build-essential \
    ca-certificates \
    coreutils \
    curl \
    file \
    gettext \
    git \
    wget \
    zip \
    unzip \
    libssl-dev \
    mariadb-client \
    odbcinst \
    libodbc1 \
    libaio1 \
    && apt-get clean

RUN rm -rf /var/lib/apt/lists/*

# Setup Composer
COPY --from=composer /usr/bin/composer /usr/bin/composer
ENV COMPOSER_ALLOW_SUPERUSER=1

# Setup extensões
ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/
RUN chmod +x /usr/local/bin/install-php-extensions && \
    install-php-extensions xdebug oci8 sockets amqp soap gd odbc mysqli pdo_mysql pdo_odbc mongodb-^1.13 intl pdo_oci