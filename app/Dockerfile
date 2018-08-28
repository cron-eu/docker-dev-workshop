FROM debian:latest

# install apache and mod_php
RUN apt-get update ; apt-get -y install vim libapache2-mod-php

VOLUME /var/www/html

# Start apache
CMD apachectl -D FOREGROUND
