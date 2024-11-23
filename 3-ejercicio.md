## Esquema para el ejercicio

![Imagen](img/esquema-ejercicio3.PNG)

### Crear red net-wp

```

docker network create net-wp -d bridge

```

### Para que persista la información es necesario conocer en dónde mysql almacena la información

# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN <https://hub.docker.com/>

En el esquema del ejercicio carpeta del contenedor mysql es /var/lib/mysql

Ruta carpeta host: D:\DockerData\ejercicio\db

### ¿Qué contiene la carpeta db del host?

No contiene ninguna informacion

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD

# COMPLETAR CON EL COMANDO

```
docker run -d --name mysql --network net-wp -v D:/DockerData/ejercicio/db:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123 -e MYSQL_DATABASE=db -e MYSQL_USER=ariel -e MYSQL_PASSWORD=123 mysql:8
```

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?

Ahora encuentra con toda la informacion de la base de datos

### Para que persista la información es necesario conocer en dónde wordpress almacena la información

# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN <https://hub.docker.com/>

En el esquema del ejercicio la carpeta del contenedor wordpress es /var/www/html

Ruta carpeta host: D:\DockerData\ejercicio\www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)

```
docker run -d --name wordpress --network net-wp -v D:/DockerData/ejercicio/www:/var/www/html -e WORDPRESS_DB_HOST=mysql:3306 -e WORDPRESS_DB_USER=ariel -e WORDPRESS_DB_PASSWORD=123 -e WORDPRESS_DB_NAME=db -p 8080:80 wordpress
```

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

La informacion del sitio web, se mantuvo al eliminarla y crearlo otra vez
