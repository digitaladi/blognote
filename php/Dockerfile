FROM php:8-fpm

RUN apt update \
    && apt install -y zlib1g-dev g++ git libicu-dev zip libzip-dev zip \
    && docker-php-ext-install intl opcache pdo_mysql \
    && pecl install apcu \
    && docker-php-ext-enable apcu \
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip 

    

    #RUN docker-php-ext-configure gd --with-freetype --with-webp --with-jpeg \
    #&& docker-php-ext-install  gd \
    #&& docker-php-ext-install exif



WORKDIR /var/www/html/blognote

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

#le binaire de symfony
RUN curl -sS https://get.symfony.com/cli/installer | bash
#éxécutable de symfony
RUN mv /root/.symfony5/bin/symfony /usr/local/bin/symfony
#configuration de git
RUN git config --global user.email "aladi.timera1605@gmail.com" \ 
    && git config --global user.name "digitaladi"












