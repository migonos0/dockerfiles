## https://stackoverflow.com/questions/47603398/docker-php-with-pdo-pgsql-install-issue

FROM php:8.1.6-fpm-bullseye

RUN mv /etc/apt/preferences.d/no-debian-php /etc/apt/preferences.d/yes-debian-php

RUN apt update

# Install Postgres PDO
RUN apt install -y libpq-dev \
    && docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
    && docker-php-ext-install pdo pdo_pgsql pgsql

RUN mv /etc/apt/preferences.d/yes-debian-php /etc/apt/preferences.d/no-debian-php

RUN apt update
