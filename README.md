# DockerWorkshop

## Instalación de Docker en RHEL 8

Docker es una plataforma de software que permite crear, probar y desplegar aplicaciones en contenedores. A continuación, se detallan los pasos para instalar Docker en RHEL 8:

Requisitos previos

Antes de instalar Docker en RHEL 8, asegúrate de tener lo siguiente:

- Acceso de administrador al sistema
- Suscripción a Red Hat Enterprise Linux 8
- Acceso a Internet

1. Actualiza el sistema

  Antes de instalar Docker, actualiza el sistema con los últimos paquetes disponibles. Para ello, ejecuta el siguiente comando:

  `sudo dnf update`

2. Agrega el repositorio de Docker

  Docker no está disponible en los repositorios oficiales de RHEL 8, por lo que deberás agregar el repositorio de Docker para poder instalarlo. Para ello, sigue estos pasos:

  Descarga e instala el paquete que agrega el repositorio de Docker:

  `sudo dnf install -y dnf-plugins-core`

Agrega el repositorio de Docker:

`sudo dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo`

3. Instala Docker

Una vez que hayas agregado el repositorio de Docker, puedes instalar Docker Community Edition (CE) utilizando el siguiente comando:

`sudo dnf install -y docker-ce docker-ce-cli containerd.io`

Este comando instala la última versión de Docker CE, así como Docker CLI (la interfaz de línea de comandos de Docker) y containerd.io (el daemon de contenedores).

4. Inicia el servicio de Docker

Para iniciar el servicio de Docker, ejecuta el siguiente comando:

`sudo systemctl start docker`

5. Verifica la instalación de Docker

Para verificar que Docker se ha instalado correctamente, ejecuta el siguiente comando:

`sudo docker run hello-world`

Este comando descarga una imagen de prueba y la ejecuta en un contenedor. Si Docker está instalado correctamente, verás un mensaje de saludo de Docker.

¡Y eso es todo! Ahora tienes Docker instalado en tu sistema RHEL 8.






Trabajando con imágenes usando la interfaz de línea de comandos (CLI) de Docker
A continuación, se detallan los pasos para trabajar con imágenes utilizando la interfaz de línea de comandos (CLI) de Docker:

## Buscando imágenes en Docker Hub
Para buscar una imagen de Docker en el repositorio de Docker Hub, sigue estos pasos:

Visita https://hub.docker.com/ para buscar imágenes disponibles.

Ejecuta el siguiente comando:

`docker search httpd`

Ejemplo de ejecución
```
$ docker search httpd

NAME                     DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
httpd                    The Apache HTTP Server Project                  4566      [OK]
httpd-alpine             The Apache HTTP Server Project in alpine       1071      [OK]
...
```


Salida del comando

El comando lista todas las imágenes disponibles en Docker Hub que contienen la palabra clave "httpd". Para cada imagen, muestra su nombre, descripción, número de estrellas y si es oficial o automatizada.

## Descargando imágenes desde Docker Hub
Una vez que hayas encontrado la imagen que deseas, descárgala utilizando el siguiente comando:

`docker pull httpd`

Si necesitas una versión específica de la imagen, agrega el tag correspondiente al final del comando. Por ejemplo:

`docker pull httpd:2.2.29`

Ejemplo de ejecución

```
$ docker pull httpd

Using default tag: latest
latest: Pulling from library/httpd
b9a857cbf04d: Pull complete
...
Digest: sha256:ddcecd29a7a58c38a68d8b3a3a1402eebd9040b39f9d8c0e87e38c68dc1bcb51
Status: Downloaded newer image for httpd:latest
docker.io/library/httpd:latest
```

Salida del comando

El comando descarga la imagen httpd desde Docker Hub y muestra información sobre el proceso de descarga. En el ejemplo anterior, se descargó la versión "latest" de la imagen.

## Listando imágenes en tu sistema

Para verificar las imágenes descargadas en tu sistema, ejecuta el siguiente comando:

`docker images`

Ejemplo de ejecución

```
$ docker images

REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
httpd               latest              85f2c5846f52        2 weeks ago         138MB
httpd               2.2.29              ccb5efae6522        2 years ago         201MB
...
```

Salida del comando

El comando lista todas las imágenes descargadas en tu sistema. Para cada imagen, muestra su nombre, tag, identificador de imagen, fecha de creación y tamaño.

## Eliminando imágenes de tu sistema

Si deseas eliminar una imagen de tu sistema, utiliza el siguiente comando:

`docker rmi httpd:2.2.29`

Ejemplo de ejecución

```
$ docker rmi httpd:2.2.29

Untagged: httpd:2.2.29
Deleted: sha256:ccb5efae65225eb3fb2b47e8d947e4c54726f6b4e4
```
