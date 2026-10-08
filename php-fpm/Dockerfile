FROM php:8.5-fpm

RUN apt-get update && apt-get install -y \
        autoconf \
        g++ \
        gcc \
        make \
        imagemagick \
        libmagickwand-dev \
        libpng-dev \
        libjpeg-dev \
        libicu-dev \
        default-mysql-client \
	&& docker-php-ext-configure gd \
        --with-freetype \
        --with-jpeg \
    && docker-php-ext-install \
        pdo_mysql \
        mysqli \
        gd \
        intl \
    && pecl install imagick \
    && docker-php-ext-enable imagick \
    && apt-get purge -y autoconf g++ gcc make \
    && apt-get autoremove -y \
    && rm -rf /var/lib/apt/lists/*

RUN echo "[client]" > /etc/my.cnf && \
    echo "skip-ssl=1" >> /etc/my.cnf && \
    echo "[mysqldump]" >> /etc/my.cnf && \
    echo "skip-ssl=1" >> /etc/my.cnf && \
    chmod 644 /etc/my.cnf