## https://stackoverflow.com/questions/47603398/docker-php-with-pdo-pgsql-install-issue

FROM php:8.1.6-fpm-bullseye

RUN mv /etc/apt/preferences.d/no-debian-php /etc/apt/preferences.d/yes-debian-php

RUN apt update

# Install Postgres PDO
RUN apt install -y libpq-dev \
    && docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
    && docker-php-ext-install pdo pdo_pgsql pgsql

## Install Composer
RUN apt install -y git zip \
    && php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php -r "if (hash_file('sha384', 'composer-setup.php') === '55ce33d7678c5a611085589f1f3ddf8b3c52d662cd01d4ba75c0ee0459970c2200a51f492d557530c71c15d8dba01eae') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
    && php composer-setup.php \
    && php -r "unlink('composer-setup.php');" \
    && mv composer.phar /usr/local/bin/composer

RUN mv /etc/apt/preferences.d/yes-debian-php /etc/apt/preferences.d/no-debian-php

RUN apt update
