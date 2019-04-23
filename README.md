# DEVLAMP (Ubuntu 18.04)
# 0.1.20190423.0

Docker: I/O :: MQ - PHPDEV-Ubuntu 18.04

**Docker for PHP Developers**

external config (/docker/conf/)

* Ubuntu 18.04
* Apache 2.4.29
* MySQL 5.7.25
* PHP 7.2.17 (mod-php, xdebug, cli, phpunit, composer) (PHP 7.2: php-mcrypt del)
* mail: ssmtp (docker pull iomq/mailcatcher)
* cron.d-Support


example: docker run with iomq/mailcatcher
docker run --link mailcatcher:mailcatcher -d -p "80:80" -p "3306:3306" -v "/dockerdb/mysql/iomq1804:/var/lib/mysql" -v "/docker:/docker" -v "/var/www:/var/www" -v "/docker/opt/tools:/opt/tools" --name iomq1804 iomq/lamp1804


example: full docker run with iomq/mailcatcher

docker run --link mailcatcher:mailcatcher -d -h="iomq1804" --add-host="php.iomq:127.0.0.1" -p "80:80" -p "3306:3306" -v "/dockerdb/mysql/iomq1804:/var/lib/mysql" -v "/docker:/docker" -v "/usr/local/iomqwww:/usr/local/iomqwww" -v "/docker/opt:/opt" -e WORKDIR="/usr/local/iomqwww" -e APACHE_CHANGEUSER=Y -e APACHE_MYUSER=Y -e APACHE_USER=iomq -e APACHE_GROUP=iomq --name iomq1804 iomq/lamp1804


MySQL user 'root' has no password but only allows local connections
mysql -uadmin -pchangeit -h127.0.0.1

supervisorctl (start|stop) apache2
supervisorctl (start|stop) mysqld
