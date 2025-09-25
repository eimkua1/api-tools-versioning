FROM php:8.4.11-cli-bullseye

RUN apt-get update && apt-get install -y libzip-dev wget

# Install PHP core extensions
RUN docker-php-ext-install -j$(nproc) bcmath

# Install PHP pecl extensions
RUN pecl install zip && pecl install xdebug

# Enable extensions
RUN docker-php-ext-enable zip xdebug

# Install composer
ADD ./composer-installer.sh /usr/bin/composer-installer.sh
RUN chmod 0775 /usr/bin/composer-installer.sh && \
    /usr/bin/composer-installer.sh && \
    rm -rf /usr/bin/composer-installer.sh && \
    mv composer.phar /usr/bin/composer && \
    chmod 0775 /usr/bin/composer
