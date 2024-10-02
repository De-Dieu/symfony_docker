FROM php:8.3-fpm

RUN apt update \
    && apt install -y zlib1g-dev g++ git libicu-dev zip libzip-dev zip \
    && docker-php-ext-install intl opcache pdo pdo_mysql \
    && pecl install apcu \
    && docker-php-ext-enable apcu \
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip

WORKDIR /var/www/symfony_docker

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN curl -sS https://get.symfony.com/cli/installer | bash \
    && mv /root/.symfony*/bin/symfony /usr/local/bin/symfony
# RUN curl -sS https://get.symfony.com/cli/installer | bash \
#     && if [ -f /root/.symfony5/bin/symfony ]; then mv /root/.symfony5/bin/symfony /usr/local/bin/symfony; else echo "Symfony CLI installation failed"; exit 1; fi

RUN git config --global user.email "dedieu.mbou@ginov.io" \ 
    && git config --global user.name "De-Dieu"