FROM ubuntu:18.04
MAINTAINER xxx
ENV DEBIAN_FRONTEND=noninteractive \
    APACHE_DOCUMENT_ROOT=/var/www/html

RUN apt-get update \
    && apt-get install -y \
        apt-utils \
        build-essential \
        wget \
        autoconf \
        cron \
        iputils-ping \
        g++ \
        default-mysql-client \
        default-libmysqlclient-dev \
        git \
        curl \
        dpkg-dev \
        libpng-dev \
        libjpeg-dev \
        libonig-dev \
        libxml2-dev \
        libpq-dev \
        libzip-dev \
        cron \
        libmcrypt-dev \
        zlib1g-dev \
        libbz2-dev \
        libssl-dev \
        libicu-dev \
        libfreetype6-dev \
        redis \
        net-tools \
        zip \
        unzip \
        nano \
        sass \
    && apt-get install -y apache2 \
        apache2-bin \
        apache2-data \
        apache2-utils \
        libapr1 \
        libaprutil1 \
        libaprutil1-dbd-sqlite3 \
        libaprutil1-ldap \
        liblua5.2-0 \
        ssl-cert \
    && apt-get install -y libapache2-mod-php7.2 \
    && rm -rf /var/lib/apt/lists/*

#RUN echo "ServerName $sitename" >> /etc/apache2/apache2.conf
ADD ./apache-conf/emconnect-dev.conf /etc/apache2/sites-available/emconnect-dev.conf
#RUN echo "listen = 127.0.0.1:9000" >> /etc/php/7.2/fpm/php-fpm.conf

# COMPOSER
# COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Enable Apache mods.
#RUN a2enmod rewrite headers fcgid alias proxy_fcgi
RUN a2enmod rewrite headers alias proxy_fcgi ldap vhost_alias
RUN a2ensite emconnect-dev

CMD ["apache2ctl", "-D", "FOREGROUND"]