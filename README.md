# WordPress with Docker Compose

This is a setup to run WordPress using Docker. It is primarily intended for development use but can probably easily be adopted for simple production use.

## Software Stack
Linux + Nginx + PHP-FPM + MariaDB

## setup
[Download](https://wordpress.org/download/) a version of WordPress and unzip its contents to `data-wp/` and then copy the `config/wp-config.php` file to `data-wp/`.

## Configuration
Before starting the containers, some configuration must be done. Don't worry, it's super easy. All the necessary needed configurations to get it up and running can be done via the `.env` file.

Example configuration to get you started:
```
WEB_PORT=80

DB_HOST=database
DB_USER=user
DB_PASSWORD=password
DB_NAME=wordpress
DB_ROOT_PASSWORD=toor
DB_TABLE_PREFIX=wp_
DB_CHARSET=utf8
DB_COLLATE=

WP_DEBUG=false
WP_ALLOW_MULTISITE=false
WP_AUTH_KEY=^ij>T+Z4w9|2VR@dR3}yw[D]H|k&Oeil9uqR[ru}UtnXZ^aya_z|ZA]-.x,]/:?h
WP_SECURE_AUTH_KEY=A_a7.mn=f--gg9{+VUuSdI9t+V|o*z8z9VdO!C=+^mA<FuONPYSYH8z0fDcyd/US
WP_LOGGED_IN_KEY=o?8T9Ze;xGa-ut!I/-[u>,$!@1+QOwW}nW8&o3E/Mu1Vmz>L[SR`qstTDBWeJWOM
WP_NONCE_KEY=$tAeO%rJDXv#88O]Ak}zSpPxouL4O(K/]<>(67~L43?eh-yO3Q;RdEN^yh4a^(6~
WP_AUTH_SALT=H[+n-CM^(6ZlGa%kZ3w;$@,G*ZF$DFNUE^!M ,vV7l>O-YUL 6Y+i-|wzY2+<-0f
WP_SECURE_AUTH_SALT=m3w|&-;sE+GMLjHcvfoX`?f@CdF-|tM-#a5b%|IjFp?g+LHkXM?iwb-f}A-Iyfo`
WP_LOGGED_IN_SALT=!MIDWB^u&,:U~7R4+=bDdg&6A{!YpQEa:,]W%A5sZ~mtQ~8w?=3n0-%ItqCz6yi{
WP_NONCE_SALT=^X:yclTDu/N8v=vUM:>tjM%;u*QiYPq1zWr$kF{ZdXf,tU:{58tP083OE|5gz</u
```

Please do not use this for your production site. This should just be an example to get you up and running.

You can have WordPress generate a set of keys and salts for you via the [WordPress API](https://api.wordpress.org/secret-key/1.1/salt/).

## Running
Make sure to have **Docker (docker-engine)** and **Docker Compose (docker-compose)** installed.

Simply run:
```
$ docker-compose up -d
```

Go to [your installation of WordPress](http://localhost/).

## Additional configuration done

#### nginx
Workdir `/var/www`

#### PHP
| Parameter           | Value |
| ------------------- | ----- |
| upload_max_filesize | 128M  |
| post_max_size       | 128M  |

## Todos
- Currently no SSL support configured
- Add extra commonly used PHP extensions
- Allow for dynamic scaling
- Script to automatically provision WordPress
