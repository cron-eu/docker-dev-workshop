FROM debian:latest

# install apache and mod_php
RUN apt-get update \
  && apt-get -y install vim libapache2-mod-php \
  && rm -rf rm -rf /var/lib/apt/lists/*

# install mysqlclient libraries and other stuff
RUN apt-get install -y mysql-client php-mysql curl zip unzip php-xml less \
 php-gd php-zip \
 && phpenmod xml gd zip

COPY php/apache/php.ini /etc/php/7.0/apache2/conf.d/99-typo3.ini

# install PHP composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# allow su to www-data
RUN chsh -s /bin/bash www-data ; chown www-data /var/www -R

VOLUME /var/www/html

ADD html/phpinfo.php /var/www/html/

# Start apache
CMD apachectl -D FOREGROUND
