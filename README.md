# Service Template

## Setup

### Automated way:
* Clone project:
```shell
git clone git@github.com:fractalzombie/frzb-service-template.git
```
* Copy .env.dist file to .env and configure it
* Change COMPOSE_PROJECT_NAME variable in .env file (ony snake_case is allowed for name)
* Change project namespace:
```shell
use make install name=NewServiceName (in PascalCase like in PSR conventions)
```
* Start docker containers using `docker-compose -d ${COMPOSE_PROJECT_NAME} up -d --build` or `make start`
* Your service is ready for development

### Manual way:
* Clone project:
```shell
git clone git@github.com:fractalzombie/frzb-service-template.git
```
* Copy .env.dist file to .env and configure it
* Change COMPOSE_PROJECT_NAME variable in .env file (ony snake_case is allowed for name)
* Change project namespace in these files:
```shell
composer.json
src/Kernel.php
public/index.php
bin/console
config/services.conf
```
* Make composer install
* Start docker containers using `docker-compose -d ${COMPOSE_PROJECT_NAME} up -d --build` or `make start`
* Your service is ready for development

## Description

### Versions:
**PHP**: _8.1_ \
**PHPUnit**: _9.5_ \
**Symfony**: _6.1_

### Dependencies:

#### Main:
```json
{
    "fp4php/functional": "^4.18",
    "frzb/dependency-injection": "^1.2",
    "frzb/request-mapper": "^1.6",
    "nelmio/api-doc-bundle": "^4.9",
    "symfony/console": "6.1.*",
    "symfony/dotenv": "6.1.*",
    "symfony/expression-language": "6.1.*",
    "symfony/flex": "^2",
    "symfony/framework-bundle": "6.1.*",
    "symfony/http-client": "6.1.*",
    "symfony/messenger": "6.1.*",
    "symfony/monolog-bundle": "^3.8",
    "symfony/property-access": "6.1.*",
    "symfony/property-info": "6.1.*",
    "symfony/runtime": "6.1.*",
    "symfony/security-bundle": "6.1.*",
    "symfony/serializer": "6.1.*",
    "symfony/string": "6.1.*",
    "symfony/uid": "6.1.*",
    "symfony/validator": "6.1.*",
    "symfony/yaml": "6.1.*"
}
```

#### Dev:
```json
{
    "friendsofphp/php-cs-fixer": "^3.9",
    "phpunit/phpunit": "^9.5",
    "sempro/phpunit-pretty-print": "^1.4",
    "symfony/var-dumper": "6.1.*",
    "symfony/web-profiler-bundle": "6.1.*"
}
```

### PHP Extensions:
```shell
bcmath
bz2
pcntl
calendar
exif
gd
intl
imagick
ldap
opcache
redis
soap
xsl
gmp
zip
sockets
amqp
pdo_pgsql
pgsql
rdkafka
xdebug
```

### Container Software:
```shell
curl
nano
gnupg
zip
unzip
git
netcat-openbsd
openssl
```

### Docker files:
**php/cli** for _CLI_ applications: cron, consumers, console commands \
**php/fpm** for _HTTP_ applications: controllers, websockets, rest \
**nginx** for _PROXY_ applications
