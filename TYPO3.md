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

We will also install TYPO3 via composer in the container

### Run the LAMP Stack via `docker-compose`

```
su - www-data ; cd html/
composer create-project typo3/cms-base-distribution:8.7 .
```
