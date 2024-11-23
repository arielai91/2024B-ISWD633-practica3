# VOLUMEN TIPO HOST

Un volumen host (o bind mount) es un tipo de volumen donde se monta un directorio o archivo específico del sistema de archivos del host en un contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```

### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura

![Volúmenes](img/directorio.PNG)

### Crear un volumen tipo host con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)

![Volúmenes](img/volumen-host.PNG)

# COMPLETAR CON EL COMANDO

```
docker run -d --name contenedor1 -v D:\DockerData\nginx\html:/usr/share/nginx/html -p 8080:80 nginx:alpine
```

### ¿Qué sucede al ingresar al servidor de nginx?

Me sale un error 403 Forbidden, esto es debido a que no encuentra ningun contenido.

### ¿Qué pasa con el archivo index.html del contenedor?

Debido a que no encuentra ningun archivo index.html no lo recibe, por lo que el resultado es el mismo que anterior.

### Ir a <https://html5up.net/> y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html

### ¿Qué sucede al ingresar al servidor de nginx?

Lee el archivo index.html, y nos muestra en pantalla.

### Eliminar el contenedor

```
docker rm contenedor1
```

### ¿Qué sucede al crear nuevamente el mismo contenedor con volumen de tipo host a los directorios definidos anteriormente?

* Datos persistentes: Si ya había archivos dentro de la carpeta html en el host, esos archivos serán accesibles y utilizables dentro del contenedor. El contenedor tendrá acceso a esos archivos en el directorio mapeado.

* Reemplazo de contenedor: Si eliminaste el contenedor previamente, Docker creará uno nuevo, pero la ruta en el host no cambia, lo que significa que los datos persistentes en esa carpeta se mantendrán.

* Reutilización de los datos previos: Si el directorio del host contenía datos, al crear un nuevo contenedor, esos datos se usarán dentro del contenedor, lo que podría afectar la configuración o el comportamiento si los datos ya estaban en un estado específico.

### ¿Qué hace el comando pwd?

muestra la ruta completa del directorio de trabajo actual

Si quieres incluir el comando pwd dentro de un comando de Docker, lo puedes hacer de diferentes maneras dependiendo del shell que estés utilizando.

### Volumen tipo host usando PWD y PowerShell

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v ${PWD}/<ruta relativa>:<ruta absoluta> <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (Git Bash)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd -W)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (en Linux)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```
