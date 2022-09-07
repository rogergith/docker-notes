Descargar la ultima imagen de `node`:

```sh
docker pull node 
```

Descargar la version `18` de `node`
```sh
docker pull node:18 
```

Lista las imagenes que tenemos descargada en nuestra maquina.
```sh
docker images
```

Eliminar una imagen `node` version `16`
```sh
docker image rm node:16
```

#### Comando para contenedores

Crear un contenerdor de mongo a partir de una imagen de mongo previamente descargada.
```sh
docker create mongo
```

Crear un contenedor con nombre `monguito` en base a la imagen de mongo.
```sh
docker create --name monguito mongo
```

Iniciar un contenedor
```sh
docker start ID_CONTENEDOR o NOMBRE_CONTENEDOR.
```

Verificar si el contenedor esta corriendo de forma correcta.
```sh
docker ps
```

Detener un contenedor
```sh
docker stop ID_CONTENEDOR o NOMBRE_CONTENEDOR.
```

Ver todos los contenedores que estan en nuestro sistema.
```sh
docker ps -a
```
#### Puerto en Docker

Se crea un contenedor llamado `monguito` que escuchara en el puerto `27017` y estara mapeado con el puerto `27015` del contenedor
```sh
docker create -p27017:27015 --name monguito mongo 
```

Docker asigna un puerto para conectarnos al contenedor
```sh
docker create -p27015 --name monguito mongo
```

Creamos y arrancamos un contenedor basado en la imagen postgres en su version 12 llamado `database_hf` que escuchara en el puerto `5499` y estara mapeado al puerto `5432`. EL usuario configurado para la base de datos sera `postgres` con el password `rogerdeb`, su host `127.0.0.1` y una base dedatos de prueba `testdb`. 

El volumen para persistir las base de datos estaran en el directorio `C:/data_postgres_hf` del equipo anfitrion mapeado con el direcotio `/var/lib/postgresql/data` de contenedor.

```sh
docker run --name database_hf -p 5499:5432 -v C:/data_postgres_hf:/var/lib/postgresql/data -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=rogerdeb -e POSTGRES_DB=testdb -e DATABASE_HOST=127.0.0.1  postgres:12
```
