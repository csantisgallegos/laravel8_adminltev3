# Proyecto Laravel 8 con plantilla AdminLte V3

## Requisitos Previos:
* Instalar composer de forma global [Link](https://getcomposer.org/)
* Instalar Git [Link](https://git-scm.com/downloads)
* Instalar un entorno de desarrollo (Php8, Mysql/SQL, Apache), ejemplo: WampServer [Link](https://www.wampserver.com/en/).

----

Guía de instalación y configuración mediante comandos

* Instalación Laravel 8 
```sh
 composer create-project --prefer-dist laravel/laravel:^8.0 laravel8
 cd laravel8
 composer install
 cp .env.example .env
 php artisan key:generate
 php artisan storage:link
```
