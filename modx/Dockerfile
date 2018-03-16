FROM php:7.0-fpm

RUN apt-get update && apt-get install -y curl zip unzip git vim xclip

RUN curl -sL https://deb.nodesource.com/setup_8.x | bash - && apt-get install -y nodejs build-essential

RUN docker-php-ext-install pdo pdo_mysql

RUN php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer

RUN cd /var/www && git clone https://github.com/modmore/Gitify.git && cd Gitify && composer install

RUN { echo 'date.timezone=Europe/Moscow'; } > /usr/local/etc/php/conf.d/datetime.ini

WORKDIR /var/www/html/public

VOLUME /var/www/html/public

RUN usermod -u 1000 www-data

CMD ["php-fpm"]
