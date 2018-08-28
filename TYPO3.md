Setup a TYPO3 App in Docker
===========================

TYPO3 System Requirements

See https://docs.typo3.org/typo3cms/InstallationGuide/In-depth/SystemRequirements/Index.html

We need:

* PHP and a Web-Server: we choose PHP7 and Apache
  * mod_rewrite must be available
  * 128M PHP memory limit
* Database: we choose MySQL V5.5+
* composer
* some php modules like xml, zip, gd etc.

We will also install TYPO3 via composer in the container

### Run the LAMP Stack via `docker-compose`

Run the stack:

```
docker-compose up -d
```

and then exec a `bash` inside the running container:

```
docker-compose exec app /bin/bash
```

Run composer as www-data:

```
su - www-data ; cd html/
rm index.html
composer create-project typo3/cms-base-distribution:8.7 .
touch web/FIRST_INSTALL
```

Run Web-Browser:

```
open http://$(docker-machine ip workshop):8000/web/typo3
```

Configure the database with the credentials from `docker-compose.yml`. Host-name
is `db`.
