# Proyecto Laravel 9 con plantilla AdminLte V3

## Versiones

- [Laravel 8 con plantilla AdminLte V3](README.md)
- [Laravel 9 con plantilla AdminLte V3](README_laravel9.md)

## Control de cambios

- 14-06-2023:
  - Proyecto Laravel 9 con plantilla AdminLte V3 (Instalación desde cero)
  - Eliminación de Laravel Breeze

## Requisitos Previos

Antes de comenzar, asegúrate de tener instaladas las siguientes herramientas:

- [Composer](https://getcomposer.org/) (instalación global)
- [Git](https://git-scm.com/downloads)
- Entorno de desarrollo (Php8, Mysql/SQL, Apache), por ejemplo: [WampServer](https://www.wampserver.com/en/)

---

## Guía de instalación y configuración mediante comandos

### Instalación de Laravel 9

```sh
composer create-project --prefer-dist laravel/laravel:^9.0 laravel9
cd laravel9
composer install
cp .env.example .env
php artisan key:generate
php artisan storage:link
```

### Configuración de la base de datos

Si aún no has configurado la base de datos, puedes migrar el modelo inicial de Laravel con el siguiente comando:

```sh
php artisan migrate
```

Recuerda establecer el largo de caracteres por defecto de las columnas a migrar en el archivo `app\Providers\AppServiceProvider.php`, agregando el siguiente código en la función `boot`: `Schema::defaultStringLength(191);`

### Instalación de la herramienta de depuración "Laravel Debugbar"

Antes de continuar con la migración, se recomienda instalar la librería "Laravel Debugbar" para facilitar la depuración y el seguimiento del rendimiento del servicio. Puedes instalarla con los siguientes comandos:

```sh
composer require barryvdh/laravel-debugbar --dev
php artisan vendor:publish --provider="Barryvdh\Debugbar\ServiceProvider"
```

### Publicación de archivos de errores

Si deseas personalizar la apariencia y el comportamiento de los errores de Laravel, puedes publicar los archivos de errores con el siguiente comando:

```sh
php artisan vendor:publish --tag=laravel-errors
```

### Instalación de la librería "Laravel Español"

Si prefieres utilizar el idioma español en tu proyecto, puedes instalar la librería "Laravel Español" con los siguientes comandos:

```sh
composer require laraveles/spanish
php artisan vendor:publish --tag=lang
php artisan laraveles:install-lang
```

### Instalación de AdminLte

Para utilizar la plantilla AdminLte en tu proyecto, ejecuta los siguientes comandos:

```sh
composer require jeroennoten/laravel-adminlte
php artisan adminlte:install
```

### Instalación de vistas de autenticación AdminLte

Si deseas utilizar las vistas de autenticación predefinidas de AdminLte, puedes instalarlas con los siguientes comandos:

```sh
composer require laravel/ui
php artisan ui bootstrap --auth
php artisan adminlte:install --only=auth_views
php artisan adminlte:install --only=main_views
npm install && npm run build
```

### Uso de las plantillas predefinidas

Una vez instalada la librería por completo, puedes comenzar a utilizar las plantillas predefinidas. Puedes encontrar más información en la documentación de [Laravel-AdminLTE](https://github.com/jeroennoten/Laravel-AdminLTE/wiki/Usage). A continuación, se muestra un ejemplo de cómo reemplazar el contenido de un archivo:

```php
@extends('adminlte::page')

@section('title', 'Dashboard')

@section('content_header')
     <h1>Dashboard</h1>
@stop

@section('content')
     <p>Bienvenido al panel de administración.</p>
@stop

@section('css')
     <link rel="stylesheet" href="/css/admin_custom.css">
@stop

@section('js')
     <script> console.log('¡Hola!'); </script>
@stop
```

---

## Instalación de plugins adicionales de AdminLte

AdminLte v3 incluye una lista de paquetes asociados a librerías más recurrentes. Puedes obtener la lista de plugins disponibles con el siguiente comando:

```sh
php artisan adminlte:plugins
```

Para instalar alguno de estos plugins, utiliza el siguiente comando indicando la "Key" del plugin:

```sh
php artisan adminlte:plugins install --plugin=icheckBootstrap
php artisan adminlte:plugins install --plugin=paceProgress
```

---

## Comandos generales de ayuda

Aquí tienes algunos comandos útiles para el desarrollo de tu proyecto:

- `composer update`: Actualiza todas las dependencias del proyecto a sus últimas versiones, de acuerdo con las restricciones especificadas en el archivo `composer.json`. También actualiza el archivo `composer.lock` para reflejar estos cambios.

- `php artisan storage:link`: Crea un enlace simbólico desde `public/storage` a `storage/app/public`, permitiendo acceder a los archivos de almacenamiento a través de la web.

- `npm install`: Instala todas las dependencias del proyecto listadas en el archivo `package.json`. Las dependencias se instalan en la carpeta `node_modules`.

- `npm run build`: Ejecuta el script `build` especificado en el archivo `package.json`. Normalmente, este script compila o transpila el código fuente del proyecto en una versión que puede ser ejecutada en el entorno de producción.

- `php artisan optimize:clear`: Borra todas las cachés de la aplicación, incluyendo la caché de configuración, la caché de rutas, la caché de vistas, y otras. Esto es útil durante el desarrollo para asegurarse de que los cambios más recientes se reflejen inmediatamente.

Puedes ejecutar estos comandos de la siguiente manera:

```sh
composer update
php artisan storage:link
npm install
npm run build
php artisan optimize:clear
```

---

## Resumen de comandos para instalación desde cero

Aquí tienes un resumen de los comandos necesarios para instalar el proyecto desde cero:

1. Crea un nuevo proyecto Laravel 9 utilizando la plantilla preferida "laravel/laravel" en la versión 9.0.
2. Cambia al directorio del proyecto "laravel9".
3. Instala las dependencias del proyecto utilizando Composer.
4. Copia el archivo de ejemplo ".env.example" y crea un nuevo archivo ".env" para la configuración del entorno.
5. Genera una nueva clave de aplicación en el archivo ".env".
6. Crea un enlace simbólico desde la carpeta "public/storage" a la carpeta "storage/app/public", permitiendo acceder a los archivos de almacenamiento a través de la web.
7. Ejecuta las migraciones de la base de datos para crear las tablas necesarias.
8. Instala la biblioteca "Laravel Debugbar" para facilitar la depuración y el seguimiento del rendimiento del servicio.
9. Publica los archivos de errores de Laravel para personalizar su apariencia y comportamiento.
10. Instala la biblioteca "Laravel Español" para traducir los mensajes y etiquetas del framework al español.
11. Instala la plantilla "AdminLte" para Laravel, proporcionando una interfaz de usuario predefinida y funcionalidades adicionales.
12. Instala la biblioteca "Laravel UI" para generar las vistas de autenticación y otras funcionalidades relacionadas con la interfaz de usuario.

```sh
composer create-project --prefer-dist laravel/laravel:^9.0 laravel9
cd laravel9
composer install
cp .env.example .env
php artisan key:generate
php artisan storage:link
php artisan migrate
composer require barryvdh/laravel-debugbar --dev
php artisan vendor:publish --provider="Barryvdh\Debugbar\ServiceProvider"
php artisan vendor:publish --tag=laravel-errors
composer require laraveles/spanish
php artisan vendor:publish --tag=lang
php artisan laraveles:install-lang
composer require jeroennoten/laravel-adminlte
php artisan adminlte:install
composer require laravel/ui
php artisan ui bootstrap --auth
php artisan adminlte:install --only=auth_views
php artisan adminlte:install --only=main_views
npm install && npm run build
```

---

## Comandos de instalación asociados al proyecto actual

Si ya tienes el proyecto clonado, estos son los comandos necesarios para configurarlo:

```sh
git clone https://github.com/csantisgallegos/laravel8_adminltev3.git
cd laravel8_adminltev3/laravel9
cp .env.example .env (debe establecer variables de conexión a la base de datos)
composer update
npm install && npm run build
php artisan key:generate
php artisan storage:link
php artisan optimize:clear
```

---

Bibliografía:

- [Git - la guía sencilla](http://rogerdudler.github.io/git-guide/index.es.html)
- [Laravel 9](https://laravel.com/docs/9.x)
- [Laravel-AdminLTE](https://github.com/jeroennoten/Laravel-AdminLTE)
