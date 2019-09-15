
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

correr el comando anterior en el directorio del proyecto laravel

# artisan commands
```
docker-compose exec php72 php artisan key:generate
docker-compose exec php72 php artisan optimize

docker-compose exec php72 php artisan migrate --seed
docker-compose exec php72 php artisan make:controller MyController
```

'php72' es el contenedor con 'php-fpm'

