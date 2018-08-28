FROM debian:latest

# install php (only CLI mode)
RUN apt-get update ; apt-get -y install vim php-cli \
  && rm -rf /var/lib/apt/lists/*

# install mysqlclient libraries and other stuff
RUN apt-get install -y mysql-client php-mysql curl zip unzip php-xml less \
 php-gd php-zip \
 && phpenmod xml gd zip \
 && rm -rf /var/lib/apt/lists/*

# install PHP composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN chsh -s /bin/bash www-data \
  && mkdir -p ~www-data/.ssh \
  && chown www-data ~www-data/.ssh \
  && chmod 700 ~www-data/.ssh

# copy own SSH pub key to authorized_keys for www-data user
COPY authorized_keys /var/www/.ssh/authorized_keys

# install OpenSSH server
RUN apt-get install -y openssh-server && mkdir /var/run/sshd

# Start SSH server
CMD ["/usr/sbin/sshd", "-D"]
