# Requerimentos para levantar contenedor con Sonarqube

## Requerimientos del host :
```
sysctl -w vm.max_map_count=262144
sysctl -w fs.file-max=65536
ulimit -n 65536
ulimit -u 4096
```

## Agregar permisos de escritura para directorios :
```
chmod a+w sonarqube/data
chmod a+w sonarqube/extensions
chmod a+w sonarqube/bundled-plugins 
```
## Login inicial :
```
user : admin
pass : admin
```
## Instalar plugin SonarPHP :
* En Marketplace buscar php e instalarlo
* Restart Server
* Login again

## token maxi : c37dce49d84d2be9051334f02e29fe74b1037787

## En la instancia EC2 :
user : postgres
pass : pgSigmma2020

user : sonar
pass : sonar

login : psql -U sonar -W



SELECT datname FROM pg_database;
SELECT * FROM pg_catalog.pg_tables

408293204
