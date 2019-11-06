FROM ubuntu:16.04

MAINTAINER cuong.ngo

RUN apt-get update && apt-get install -y --no-install-recommends apt-utils

RUN apt-get update && apt-get install -y language-pack-en

RUN locale-gen en_US.UTF-8

ENV LANGUAGE=en_US.UTF-8
ENV LC_ALL=en_US.UTF-8
ENV LC_CTYPE=UTF-8
ENV LANG=en_US.UTF-8
ENV TERM xterm


# Clean up
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Install "software-properties-common" (for the "add-apt-repository")
RUN apt-get update && apt-get install -y \
    software-properties-common php-pear

# Add the "PHP 7" ppa
RUN add-apt-repository -y \
    ppa:ondrej/php

# Install PHP-CLI 7, some PHP extentions and some useful Tools with APT
RUN apt-get update && apt-get install -y --allow-remove-essential \
        php-fpm \ 
        php-mysql \
        php-cgi \
        php-cli \ 
        php-dev \
        php-phpdbg \
        php-common \
        php-curl \
        php-json \
        php-xml \
        php-mbstring \
        php-mcrypt \
        git \
        curl \
        vim \
        nano \
        nodejs \
        php7.0-gd \
        npm

#Configure Nginx
RUN apt-get -yqq update; apt-get -yqq install nginx
ADD passcode.conf /etc/nginx/conf.d/
ADD passcode.conf /etc/nginx/sites-available/
ADD nginx.conf /etc/nginx/nginx.conf
RUN ln -s /etc/nginx/sites-available/global.conf /etc/nginx/sites-enabled/

RUN service php7.3-fpm start

RUN mkdir -p /var/www/html/webapp
WORKDIR /var/www/html/webapp

CMD service php7.3-fpm start && nginx

EXPOSE 80
