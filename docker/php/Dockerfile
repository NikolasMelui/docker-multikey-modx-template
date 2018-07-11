FROM php:7.0-fpm

RUN apt-get update && apt-get install -y \
  curl \
  wget \
  git \
  vim \
  libfreetype6-dev \
  libjpeg62-turbo-dev \
  libxslt-dev \
  libicu-dev \
  libmcrypt-dev \
  libpng-dev \
  libxml2-dev \
  xclip \
  gnupg \
  && docker-php-ext-install -j$(nproc) iconv mcrypt mbstring mysqli pdo_mysql zip unzip \
  && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
  && docker-php-ext-install -j$(nproc) gd
RUN curl -sL https://deb.nodesource.com/setup_8.x | bash - \
  && apt-get install -y nodejs build-essential
RUN php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer \
  && cd /var/www && git clone https://github.com/NikolasMelui/Gitify.git -b content-class_key-include \
  && cd Gitify \
  && composer install
RUN { echo 'date.timezone=Europe/Moscow'; } > /usr/local/etc/php/conf.d/datetime.ini

WORKDIR /var/www/html/public

VOLUME /var/www/html/public

RUN usermod -u 1000 www-data

CMD ["php-fpm"]
