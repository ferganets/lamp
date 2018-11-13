![LAMP](https://github.com/teddysun/lamp/raw/master/conf/lamp.png)

Описание
===========
[LAMP](https://lamp.sh/) является мощным скриптом bash для установки Apache + PHP + MySQL / MariaDB / Percona Server и др. доп. приложений, разработанным китайским программистом [Teddysun](https://teddysun.com/). Вы можете установить Apache + PHP + MySQL / MariaDB / Percona Server очень просто, просто нужно выбрать необходимые вам модули перед запуском скрипта. И все выбранное будет установленно автоматически за несколько минут.

- [Поддерживаемые системы](#поддерживаемые-системы)
- [Поддерживаемые модули](#поддерживаемые-модули)
- [Установка](#установка)
- [Обновление](#обновление)
- [Резервное копирование](#резервное-копирование)
- [Удаление](#удаление)
- [Расположение модулей в системе](#расположение-модулей-в-системе)
- [Управление модулями](#управление-модулями)
- [Команды lamp](#команды-lamp)
- [Ошибки & Проблемы](#ошибки--проблемы)
- [Лицензия](#лицензия)

Поддерживаемые системы
===============
- CentOS-6.x
- CentOS-7.x (рекомендовано)
- Ubuntu-14.x
- Ubuntu-15.x
- Ubuntu-16.x
- Ubuntu-17.x
- Ubuntu-18.x (рекомендовано)
- Debian-7.x
- Debian-8.x
- Debian-9.x (рекомендовано)

Поддерживаемые модули
==================
- Apache-2.4 (Включая модуль HTTP/2: [nghttp2](https://github.com/nghttp2/nghttp2), [mod_http2](https://httpd.apache.org/docs/2.4/mod/mod_http2.html))
- Дополнительные модули Apache: [mod_wsgi](https://github.com/GrahamDumpleton/mod_wsgi), [mod_security](https://github.com/SpiderLabs/ModSecurity), [mod_jk](https://tomcat.apache.org/download-connectors.cgi)
- MySQL-5.5, MySQL-5.6, MySQL-5.7, MySQL-8.0, MariaDB-5.5, MariaDB-10.0, MariaDB-10.1, MariaDB-10.2, MariaDB-10.3, Percona-Server-5.5, Percona-Server-5.6, Percona-Server-5.7
- PHP-5.6, PHP-7.0, PHP-7.1, PHP-7.2
- Дополнительные модули PHP: opcache, [ionCube Loader](https://www.ioncube.com/loaders.php), [xcache](https://xcache.lighttpd.net/), [imagick](https://pecl.php.net/package/imagick), [gmagick](https://pecl.php.net/package/gmagick), [libsodium](https://github.com/jedisct1/libsodium-php), [memcached](https://github.com/php-memcached-dev/php-memcached), [redis](https://github.com/phpredis/phpredis), [mongodb](https://pecl.php.net/package/mongodb), [swoole](https://github.com/swoole/swoole-src), [xdebug](https://github.com/xdebug/xdebug)
- Прочие модули: [ImageMagick](https://github.com/ImageMagick/ImageMagick), [GraphicsMagick](http://www.graphicsmagick.org/), [Memcached](https://github.com/memcached/memcached), [phpMyAdmin](https://github.com/phpmyadmin/phpmyadmin), [Redis](https://github.com/antirez/redis), [KodExplorer](https://github.com/kalcaddle/KodExplorer)

Установка
============
- Еслу ваша операционная система: CentOS
```bash
yum -y install wget screen git
git clone https://github.com/teddysun/lamp.git
cd lamp
chmod +x *.sh
screen -S lamp
./lamp.sh
```

- Еслу ваша операционная система: Debian/Ubuntu
```bash
apt-get -y install wget screen git
git clone https://github.com/teddysun/lamp.git
cd lamp
chmod +x *.sh
screen -S lamp
./lamp.sh
```

Обновление
=======
```bash
git pull                 // Get latest version

./upgrade.sh             // Select one to upgrade
./upgrade.sh apache      // Upgrade Apache
./upgrade.sh db          // Upgrade MySQL/MariaDB/Percona
./upgrade.sh php         // Upgrade PHP
./upgrade.sh phpmyadmin  // Upgrade phpMyAdmin
```

Резервное копирование
======
- Требуется изменить конфигурацию перед запуском
- Резервное копирование БД MySQL/MariaDB/Percona, файлов и каталогов
- Backup file is encrypted with AES256-cbc with SHA1 message-digest (опционально)
- Отправка резервных копий в Google Drive (требуется выполнить команду [gdrive](https://teddysun.com/469.html)) (опционально)
- Отправка резервных копий на FTP сервер (опционально)
- Автоматическое удаление устаревших файлов с Google Drive или FTP сервера (опционально)

```bash
./backup.sh
```

Удаление
=========
```bash
./uninstall.sh
```

Расположение модулей в системе
================
| Расположение Apache        | Путь                                           |
|----------------------------|------------------------------------------------|
| Install Prefix             | /usr/local/apache                              |
| Web root location          | /data/www/default                              |
| Main Configuration File    | /usr/local/apache/conf/httpd.conf              |
| Default Virtual Host conf  | /usr/local/apache/conf/extra/httpd-vhosts.conf |
| Virtual Host location      | /data/www/virtual_host_names                   |
| Virtual Host log location  | /data/wwwlog/virtual_host_names                |
| Virtual Host conf          | /usr/local/apache/conf/vhost/virtual_host.conf |

| Расположение phpMyAdmin    | Путь                                           |
|----------------------------|------------------------------------------------|
| Installation location      | /data/www/default/phpmyadmin                   |

| Расположение KodExplorer   | Путь                                           |
|----------------------------|------------------------------------------------|
| Installation location      | /data/www/default/kod                          |

| Расположение PHP           | Путь                                           |
|----------------------------|------------------------------------------------|
| Install Prefix             | /usr/local/php                                 |
| Configuration File         | /usr/local/php/etc/php.ini                     |
| ini additional location    | /usr/local/php/php.d                           |

| Расположение MySQL         | Путь                                           |
|----------------------------|------------------------------------------------|
| Install Prefix             | /usr/local/mysql                               |
| Data Location              | /usr/local/mysql/data                          |
| my.cnf Configuration File  | /etc/my.cnf                                    |

| Расположение MariaDB       | Путь                                           |
|----------------------------|------------------------------------------------|
| Install Prefix             | /usr/local/mariadb                             |
| Data Location              | /usr/local/mariadb/data                        |
| my.cnf Configuration File  | /etc/my.cnf                                    |

| Расположение Percona       | Путь                                           |
|----------------------------|------------------------------------------------|
| Install Prefix             | /usr/local/percona                             |
| Data Location              | /usr/local/percona/data                        |
| my.cnf Configuration File  | /etc/my.cnf                                    |

Управление модулями
==================
| Модули      | Команды                                                 |
|-------------|---------------------------------------------------------|
| Apache      | /etc/init.d/httpd  (start\|stop\|status\|restart)       |
| MySQL       | /etc/init.d/mysqld (start\|stop\|status\|restart)       |
| MariaDB     | /etc/init.d/mysqld (start\|stop\|status\|restart)       |
| Percona     | /etc/init.d/mysqld (start\|stop\|status\|restart)       |
| Memcached   | /etc/init.d/memcached (start\|stop\|restart)            |
| Redis-Server| /etc/init.d/redis-server (start\|stop\|restart)         |

Команды lamp
============
| Команды    | Описание                        |
|------------|---------------------------------|
| lamp add   | create a virtual host           |
| lamp list  | list all virtual host           |
| lamp del   | remove a virtual host           |

Ошибки & Проблемы
=============
Пожалуйста, сообщите нам о любых ошибках или проблемах по электронной почте: ferganets@gmail.com or [open issues](https://github.com/teddysun/lamp/issues) on Github.

Поддержка (на Китайском): https://lamp.sh/support.html

Лицензия
=======
Copyright (C) 2013 - 2018 Teddysun

Licensed under the [GPLv3](LICENSE) License.
