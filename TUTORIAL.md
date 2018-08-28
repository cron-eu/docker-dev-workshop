Docker Dev Workshop, Tutorial
=============================

## Docker

See Prerequisites to create a Docker Machine if desired.

### Use `docker-run` to execute a bash

Use `docker run` to create a new container based on a given image:

```
docker run --name my-debian-container -it debian:latest /bin/bash
```

List (all, also non-running) containers:

```
docker ps -a
```

Delete container with:

```
docker rm my-debian-container
```

### Use `docker run` and install stuff, run apache

```
docker run --rm --name my-debian-container -p 8000:80 \
 -it debian:latest /bin/bash
```

Install Apache and PHP inside the Container:

```
# install apache with mod_php
apt-get update ; apt-get -y install vim libapache2-mod-php
# start apache
/etc/init.d/apache2 start
vi /var/www/html/phpinfo.php
```

Run the browser and access phpinfo()

```
open http://$(docker-machine ip workshop):8000/phpinfo.php
```

Dockerfile
----------

Build `myapp` as an image:

```
docker build -t myapp app/
```

List available docker images:

```
docker images
```

Create a new app instance and from the `myapp` image:

```
docker run -d -p 8000:80 --name myapp_1 myapp
```

`-d` - daemon, runs in background

List running containers:

```
docker ps
```

Stop and remove the app instance:

```
docker stop myapp_1
docker rm -v myapp_1
```

Link a local dir to the app instance

```
mkdir -p app/html
docker run -d -p 8000:80 --name myapp_1 -v $(pwd)/app/html:/var/www/html myapp
```

### References

* [Dockerfile reference](https://docs.docker.com/engine/reference/builder/)


Docker Compose
--------------

Instead of using `docker` manually a `docker-compose.yml` configuration file
can be used instead:

```
docker-compose up -d
```

----

## Prerequisites

Use `docker-machine` to create a new VM for this workshop.

```
docker-machine create -d virtualbox workshop
eval $(docker-machine env workshop)
```
