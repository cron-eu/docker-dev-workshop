FROM debian:latest

# install apache and mod_php
RUN apt-get update \
  && apt-get -y install vim libapache2-mod-php \
  && rm -rf rm -rf /var/lib/apt/lists/*

VOLUME /var/www/html

ADD html/phpinfo.php /var/www/html/

# Start apache
CMD apachectl -D FOREGROUND
