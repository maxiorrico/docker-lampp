
# laravel
```
git clone --single-branch --branch [TAG_VERSION] https://github.com/laravel/laravel.git laravel-app
```

[TAG_VERSION] : 5.8 , 4.2 , 6.0 ...

# composer commands
```
docker run --rm --interactive --tty \
  --volume $PWD:/app \
  --user $(id -u):$(id -g) \
  composer install
```
```
docker run --rm --interactive --tty \
  --volume $PWD:/app \
  --user $(id -u):$(id -g) \
  prooph/composer:5.6 \
  install
```
correr el comando anterior en el directorio del proyecto laravel
variantes : 'composer/composer:php5 install' , default=php7
          : 'composer/composer:php5-alpine install'

# artisan commands
```
docker-compose exec php72 php laravel-app/artisan key:generate
docker-compose exec php72 php laravel-app/artisan optimize
docker-compose exec php72 php laravel-app/artisan migrate --seed
docker-compose exec php72 php laravel-app/artisan make:controller MyController
```

'php72' es el contenedor con 'php-fpm'
'laravel-app' es la carpea donde esta instalado el proyecto

# docker commands

### remove all stopped containers, all dangling images, and all unused networks
```
docker system prune
```

# Apache SSL suppport 
Dentro de el directorio 'apache' :
```
openssl req -new -newkey rsa:4096 -days 3650 -nodes -x509 -subj \
    "/C=AR/ST=Tucuman/L=SMTucuman/O=Security/CN=localhost" \
    -keyout ./ssl.key -out ./ssl.crt
``` 

# TODO

* build php56 con zip, ...

