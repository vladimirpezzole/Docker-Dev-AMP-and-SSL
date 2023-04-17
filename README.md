# Docker Dev AMP and SSL 
<hr>

**Clone com modificações de >> [Erykai/docker-php](https://github.com/Erykai/docker-php)  -->[ LINK do Vídeo original ](https://www.youtube.com/watch?v=4vcFGtyl8Xk)**

<hr>

Ambiente prático para laboratório de várias versões PHP com Docker:

**PHP5.6, PHP 7.0, PHP7.2, PHP7.3, PHP7.4, PHP8.0 e PHP8.1**

com **Apache, MariaDB 10 And PhpMyAdmin**.

Todas com **xdebug, sendmail, libpng-dev, libzip-dev, zlib1g-dev, mysqli, pdo, imagick and gd**

<hr>

**Para carregar o docker compose da versão específica execute**
`docker compose -f [arquivo].yml up -d`

Ex.: `docker compose -f 81.yml up -d` para rodar o **PHP 8.1**

*Obs. se a versão do Docker CLI versão 2.0.0 for anterior use **docker-compose** com hífen(-).*

<hr>

**LINKS do VirtualHost: `lvh.me`**

<h5>https://lvh.me:9443 PHP</h5>  

<h5>http://lvh.me:9016 PhpMyAdmin</h5>

**Diretório de trabalho >> `/public_html`**

**Usuário e senha do DB MySQL **

```bash
HOST = mysql
MYSQL_USER = root
MYSQL_PASSWORD = root
MYSQL_ROOT_PASSWORD = root

```

**Portas usadas salvas no arquivo >> `.env`**

```bash
PORT_DB=9306
PORT_PHPMYADMIN=9015
PORT_WEB=9016
PORT_WEB_SSL=9443
WORKING_DIR=/public_html
```
**VirtualHost em >> `.docker/apache/000-default.conf` portas 9016 e 9443**

```bash
define ROOT "/var/www/html"
define SITE "lvh.me"

<VirtualHost *:9016>
    DocumentRoot "${ROOT}"
    ServerName ${SITE}
    ServerAlias *.${SITE}
    <Directory "${ROOT}">
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>

<VirtualHost *:9443>
    DocumentRoot "${ROOT}"
    ServerName ${SITE}
    ServerAlias *.${SITE}
    <Directory "${ROOT}">
        AllowOverride All
        Require all granted
        Options Indexes FollowSymLinks
    </Directory>

```

