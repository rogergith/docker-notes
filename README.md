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

Lista las imagenes que tenemos descargada en nuestra maquina.

Creamos y arrancamos un contenedor basado en la imagen postgres en su version 12 llamado `database_hf` que escuchara en el puerto `5499` y estara mapeado al puerto `5432`. EL usuario configurado para la base de datos sera `postgres` con el password `rogerdeb`, su host `127.0.0.1` y una base dedatos de prueba `testdb`. 

El volumen para persistir las base de datos estaran en el directorio `C:/data_postgres_hf` del equipo anfitrion mapeado con el direcotio `/var/lib/postgresql/data` de contenedor.

```sh
docker run --name database_hf -p 5499:5432 -v C:/data_postgres_hf:/var/lib/postgresql/data -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=rogerdeb -e POSTGRES_DB=testdb -e DATABASE_HOST=127.0.0.1  postgres:12
```
