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
* Instalación Laravel Breeze ([referencia](https://laravel.com/docs/8.x/starter-kits)): 
> Laravel Breeze es una implementación mínima y simple de todas las funciones de autenticación de Laravel, incluido el inicio de sesión, el registro, el restablecimiento de contraseña, la verificación de correo electrónico y la confirmación de contraseña. La capa de vista predeterminada de Laravel Breeze se compone de plantillas Blade simples diseñadas con Tailwind CSS. Breeze proporciona un excelente punto de partida para comenzar una nueva aplicación Laravel y también es una excelente opción para proyectos que planean llevar sus plantillas Blade al siguiente nivel con Laravel Livewire.

```sh
composer require laravel/breeze:1.9.2
php artisan breeze:install
npm install
npm run dev
```
* Una vez habiendo ejecutado los comandos de instalación de laravel breeze conectaremos nuestra base de datos en nuestro archivo de variables de ambiente ".env", en el caso de que nuestra base de datos aún no está definida podemos migrar el modelo inicial de laravel con el siguiente comando:
```sh
php artisan migrate
```
> Importante! Recuerde que antes de ejecutar nuestra migración debe establecer el largo de caracteres que tendrá por defecto las columnas a migrar, esto se establece en el archivo: app\Providers\AppServiceProvider.php, agregando el siguiente código en la función "boot": "Schema::defaultStringLength(191);".

* Instalación de herramienta de depuración "Laravel Debugbar":
> Antes de continuar con nuestra migración, se recomienda instalar la librería de "Laravel Debugbar", el cual permite trazar de forma optima la performance del servicio además de encontrar con varios métodos de depuración de código, para mas información puede visitar el repositorio publico de GitHub: [laravel-debugbar](https://github.com/barryvdh/laravel-debugbar)
```sh
composer require barryvdh/laravel-debugbar --dev
php artisan vendor:publish --provider="Barryvdh\Debugbar\ServiceProvider"
```
* Publicación de archivos de errores:
```sh
php artisan vendor:publish --tag=laravel-error
```
* Libreria Laravel Español:
```sh
composer require laraveles/spanish
php artisan vendor:publish --tag=lang
php artisan laraveles:install-lang
```
* Instalación AdminLte
```sh
composer require jeroennoten/laravel-adminlte
php artisan adminlte:install
```
* Para visualizar los paquetes instalados de AdminLte puede ejecutar el siguiente comando:
```sh
php artisan adminlte:status
```
* Instalación de vistas de autentificación AdminLte:
```sh
composer require laravel/ui
php artisan ui bootstrap --auth
php artisan adminlte:install --only=auth_views
npm install && npm run dev
```



