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

  ```
[root@docker01 ~]# yum update -y
Updating Subscription Management repositories.
Red Hat Enterprise Linux 8 for x86_64 - AppStre 712  B/s | 4.5 kB     00:06    
Red Hat Enterprise Linux 8 for x86_64 - AppStre 2.3 MB/s |  53 MB     00:23    
Red Hat Enterprise Linux 8 for x86_64 - BaseOS  679  B/s | 4.1 kB     00:06    
Dependencies resolved.
Nothing to do.
Complete!
```


2. Agrega el repositorio de Docker

  Docker no está disponible en los repositorios oficiales de RHEL 8, por lo que deberás agregar el repositorio de Docker para poder instalarlo. Para ello, sigue estos pasos:

  Descarga e instala el paquete que agrega el repositorio de Docker:

  ```
  sudo dnf install -y dnf-plugins-core`
  
  Updating Subscription Management repositories.
  Last metadata expiration check: 0:00:31 ago on Sat 15 Apr 2023 08:39:41 AM CST.
  Package dnf-plugins-core-4.0.21-14.1.el8.noarch is already installed.
  Dependencies resolved.
  Nothing to do.
  Complete!

  ```
Agrega el repositorio de Docker:

```
[root@docker01 ~]# dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo
Updating Subscription Management repositories.
Adding repo from: https://download.docker.com/linux/centos/docker-ce.repo
```

3. Instala Docker

Una vez que hayas agregado el repositorio de Docker, puedes instalar Docker Community Edition (CE) utilizando el siguiente comando:

```
[root@docker01 ~]# dnf install -y docker-ce docker-ce-cli containerd.io
Updating Subscription Management repositories.
Docker CE Stable - x86_64                                                                  3.7 kB/s |  40 kB     00:10    
Dependencies resolved.
===========================================================================================================================
 Package                     Arch     Version                                     Repository                          Size
===========================================================================================================================
Installing:
 containerd.io               x86_64   1.6.20-3.1.el8                              docker-ce-stable                    34 M
 docker-ce                   x86_64   3:23.0.3-1.el8                              docker-ce-stable                    23 M
 docker-ce-cli               x86_64   1:23.0.3-1.el8                              docker-ce-stable                   7.1 M
Installing dependencies:
 container-selinux           noarch   2:2.189.0-1.module+el8.7.0+17824+66a0202b   rhel-8-for-x86_64-appstream-rpms    60 k
 docker-ce-rootless-extras   x86_64   23.0.3-1.el8                                docker-ce-stable                   4.8 M
 fuse-common                 x86_64   3.3.0-16.el8                                rhel-8-for-x86_64-baseos-rpms       22 k
 fuse-overlayfs              x86_64   1.9-1.module+el8.7.0+17824+66a0202b         rhel-8-for-x86_64-appstream-rpms    74 k
 fuse3                       x86_64   3.3.0-16.el8                                rhel-8-for-x86_64-baseos-rpms       54 k
 fuse3-libs                  x86_64   3.3.0-16.el8                                rhel-8-for-x86_64-baseos-rpms       95 k
 libcgroup                   x86_64   0.41-19.el8                                 rhel-8-for-x86_64-baseos-rpms       70 k
 libslirp                    x86_64   4.4.0-1.module+el8.7.0+17824+66a0202b       rhel-8-for-x86_64-appstream-rpms    70 k
 slirp4netns                 x86_64   1.2.0-2.module+el8.7.0+17824+66a0202b       rhel-8-for-x86_64-appstream-rpms    54 k
Installing weak dependencies:
 docker-buildx-plugin        x86_64   0.10.4-1.el8                                docker-ce-stable                    12 M
 docker-compose-plugin       x86_64   2.17.2-1.el8                                docker-ce-stable                    12 M
Enabling module streams:
 container-tools                      rhel8                                                                               

Transaction Summary
===========================================================================================================================
Install  14 Packages

Total download size: 93 M
Installed size: 356 M
Downloading Packages:
(1/14): docker-ce-23.0.3-1.el8.x86_64.rpm                                                  1.7 MB/s |  23 MB     00:13    
(2/14): docker-buildx-plugin-0.10.4-1.el8.x86_64.rpm                                       899 kB/s |  12 MB     00:13    
(3/14): docker-ce-cli-23.0.3-1.el8.x86_64.rpm                                              2.7 MB/s | 7.1 MB     00:02    
(4/14): docker-ce-rootless-extras-23.0.3-1.el8.x86_64.rpm                                  1.6 MB/s | 4.8 MB     00:02    
(5/14): containerd.io-1.6.20-3.1.el8.x86_64.rpm                                            1.7 MB/s |  34 MB     00:19    
(6/14): docker-compose-plugin-2.17.2-1.el8.x86_64.rpm                                      2.2 MB/s |  12 MB     00:05    
(7/14): slirp4netns-1.2.0-2.module+el8.7.0+17824+66a0202b.x86_64.rpm                        42 kB/s |  54 kB     00:01    
(8/14): container-selinux-2.189.0-1.module+el8.7.0+17824+66a0202b.noarch.rpm                10 kB/s |  60 kB     00:05    
(9/14): libslirp-4.4.0-1.module+el8.7.0+17824+66a0202b.x86_64.rpm                           21 kB/s |  70 kB     00:03    
(10/14): fuse-overlayfs-1.9-1.module+el8.7.0+17824+66a0202b.x86_64.rpm                     293 kB/s |  74 kB     00:00    
(11/14): fuse3-libs-3.3.0-16.el8.x86_64.rpm                                                 86 kB/s |  95 kB     00:01    
(12/14): fuse-common-3.3.0-16.el8.x86_64.rpm                                                25 kB/s |  22 kB     00:00    
(13/14): libcgroup-0.41-19.el8.x86_64.rpm                                                   60 kB/s |  70 kB     00:01    
(14/14): fuse3-3.3.0-16.el8.x86_64.rpm                                                      56 kB/s |  54 kB     00:00    
---------------------------------------------------------------------------------------------------------------------------
Total                                                                                      3.8 MB/s |  93 MB     00:24     
Docker CE Stable - x86_64                                                                  298  B/s | 1.6 kB     00:05    
Importing GPG key 0x621E9F35:
 Userid     : "Docker Release (CE rpm) <docker@docker.com>"
 Fingerprint: 060A 61C5 1B55 8A7F 742B 77AA C52F EB6B 621E 9F35
 From       : https://download.docker.com/linux/centos/gpg
Key imported successfully
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                                                                   1/1 
  Installing       : fuse3-libs-3.3.0-16.el8.x86_64                                                                   1/14 
  Running scriptlet: fuse3-libs-3.3.0-16.el8.x86_64                                                                   1/14 
  Running scriptlet: container-selinux-2:2.189.0-1.module+el8.7.0+17824+66a0202b.noarch                               2/14 
  Installing       : container-selinux-2:2.189.0-1.module+el8.7.0+17824+66a0202b.noarch                               2/14 
  Running scriptlet: container-selinux-2:2.189.0-1.module+el8.7.0+17824+66a0202b.noarch                               2/14 
  Installing       : docker-compose-plugin-2.17.2-1.el8.x86_64                                                        3/14 
  Running scriptlet: docker-compose-plugin-2.17.2-1.el8.x86_64                                                        3/14 
  Installing       : containerd.io-1.6.20-3.1.el8.x86_64                                                              4/14 
  Running scriptlet: containerd.io-1.6.20-3.1.el8.x86_64                                                              4/14 
  Installing       : fuse-common-3.3.0-16.el8.x86_64                                                                  5/14 
  Installing       : fuse3-3.3.0-16.el8.x86_64                                                                        6/14 
  Installing       : fuse-overlayfs-1.9-1.module+el8.7.0+17824+66a0202b.x86_64                                        7/14 
  Running scriptlet: fuse-overlayfs-1.9-1.module+el8.7.0+17824+66a0202b.x86_64                                        7/14 
  Running scriptlet: libcgroup-0.41-19.el8.x86_64                                                                     8/14 
  Installing       : libcgroup-0.41-19.el8.x86_64                                                                     8/14 
  Running scriptlet: libcgroup-0.41-19.el8.x86_64                                                                     8/14 
  Installing       : libslirp-4.4.0-1.module+el8.7.0+17824+66a0202b.x86_64                                            9/14 
  Installing       : slirp4netns-1.2.0-2.module+el8.7.0+17824+66a0202b.x86_64                                        10/14 
  Installing       : docker-buildx-plugin-0.10.4-1.el8.x86_64                                                        11/14 
  Running scriptlet: docker-buildx-plugin-0.10.4-1.el8.x86_64                                                        11/14 
  Installing       : docker-ce-cli-1:23.0.3-1.el8.x86_64                                                             12/14 
  Running scriptlet: docker-ce-cli-1:23.0.3-1.el8.x86_64                                                             12/14 
  Installing       : docker-ce-rootless-extras-23.0.3-1.el8.x86_64                                                   13/14 
  Running scriptlet: docker-ce-rootless-extras-23.0.3-1.el8.x86_64                                                   13/14 
  Installing       : docker-ce-3:23.0.3-1.el8.x86_64                                                                 14/14 
  Running scriptlet: docker-ce-3:23.0.3-1.el8.x86_64                                                                 14/14 
  Running scriptlet: container-selinux-2:2.189.0-1.module+el8.7.0+17824+66a0202b.noarch                              14/14 
  Running scriptlet: docker-ce-3:23.0.3-1.el8.x86_64                                                                 14/14 
  Verifying        : containerd.io-1.6.20-3.1.el8.x86_64                                                              1/14 
  Verifying        : docker-buildx-plugin-0.10.4-1.el8.x86_64                                                         2/14 
  Verifying        : docker-ce-3:23.0.3-1.el8.x86_64                                                                  3/14 
  Verifying        : docker-ce-cli-1:23.0.3-1.el8.x86_64                                                              4/14 
  Verifying        : docker-ce-rootless-extras-23.0.3-1.el8.x86_64                                                    5/14 
  Verifying        : docker-compose-plugin-2.17.2-1.el8.x86_64                                                        6/14 
  Verifying        : container-selinux-2:2.189.0-1.module+el8.7.0+17824+66a0202b.noarch                               7/14 
  Verifying        : libslirp-4.4.0-1.module+el8.7.0+17824+66a0202b.x86_64                                            8/14 
  Verifying        : slirp4netns-1.2.0-2.module+el8.7.0+17824+66a0202b.x86_64                                         9/14 
  Verifying        : fuse-overlayfs-1.9-1.module+el8.7.0+17824+66a0202b.x86_64                                       10/14 
  Verifying        : libcgroup-0.41-19.el8.x86_64                                                                    11/14 
  Verifying        : fuse3-libs-3.3.0-16.el8.x86_64                                                                  12/14 
  Verifying        : fuse-common-3.3.0-16.el8.x86_64                                                                 13/14 
  Verifying        : fuse3-3.3.0-16.el8.x86_64                                                                       14/14 
Installed products updated.

Installed:
  container-selinux-2:2.189.0-1.module+el8.7.0+17824+66a0202b.noarch                                                       
  containerd.io-1.6.20-3.1.el8.x86_64                                                                                      
  docker-buildx-plugin-0.10.4-1.el8.x86_64                                                                                 
  docker-ce-3:23.0.3-1.el8.x86_64                                                                                          
  docker-ce-cli-1:23.0.3-1.el8.x86_64                                                                                      
  docker-ce-rootless-extras-23.0.3-1.el8.x86_64                                                                            
  docker-compose-plugin-2.17.2-1.el8.x86_64                                                                                
  fuse-common-3.3.0-16.el8.x86_64                                                                                          
  fuse-overlayfs-1.9-1.module+el8.7.0+17824+66a0202b.x86_64                                                                
  fuse3-3.3.0-16.el8.x86_64                                                                                                
  fuse3-libs-3.3.0-16.el8.x86_64                                                                                           
  libcgroup-0.41-19.el8.x86_64                                                                                             
  libslirp-4.4.0-1.module+el8.7.0+17824+66a0202b.x86_64                                                                    
  slirp4netns-1.2.0-2.module+el8.7.0+17824+66a0202b.x86_64                                                                 
```

Este comando instala la última versión de Docker CE, así como Docker CLI (la interfaz de línea de comandos de Docker) y containerd.io (el daemon de contenedores).

4. Inicia el servicio de Docker

Para iniciar el servicio de Docker, ejecuta el siguiente comando:

```
[root@docker01 ~]# systemctl start docker

[root@docker01 ~]# systemctl status docker
● docker.service - Docker Application Container Engine
   Loaded: loaded (/usr/lib/systemd/system/docker.service; disabled; vendor preset: disabled)
   Active: active (running) since Sat 2023-04-15 08:50:03 CST; 4min 26s ago
     Docs: https://docs.docker.com
 Main PID: 3793 (dockerd)
    Tasks: 9
   Memory: 35.8M
   CGroup: /system.slice/docker.service
           └─3793 /usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock

Apr 15 08:50:03 docker01.themike.mx dockerd[3793]: time="2023-04-15T08:50:03.336080680-06:00" level=info msg="Firewalld: i>
Apr 15 08:50:03 docker01.themike.mx dockerd[3793]: time="2023-04-15T08:50:03.462404855-06:00" level=info msg="Loading cont>
Apr 15 08:50:03 docker01.themike.mx dockerd[3793]: time="2023-04-15T08:50:03.477085545-06:00" level=info msg="Docker daemo>
Apr 15 08:50:03 docker01.themike.mx dockerd[3793]: time="2023-04-15T08:50:03.477204441-06:00" level=info msg="Daemon has c>
Apr 15 08:50:03 docker01.themike.mx dockerd[3793]: time="2023-04-15T08:50:03.502947077-06:00" level=info msg="[core] [Serv>
Apr 15 08:50:03 docker01.themike.mx systemd[1]: Started Docker Application Container Engine.
Apr 15 08:50:03 docker01.themike.mx dockerd[3793]: time="2023-04-15T08:50:03.507862781-06:00" level=info msg="API listen o>
Apr 15 08:50:52 docker01.themike.mx dockerd[3793]: time="2023-04-15T08:50:52.979466569-06:00" level=warning msg="Error get>
Apr 15 08:50:52 docker01.themike.mx dockerd[3793]: time="2023-04-15T08:50:52.979700336-06:00" level=info msg="Attempting n>
Apr 15 08:50:52 docker01.themike.mx dockerd[3793]: time="2023-04-15T08:50:52.983083281-06:00" level=error msg="Handler for>


[root@docker01 ~]# systemctl enable docker.service
Created symlink /etc/systemd/system/multi-user.target.wants/docker.service → /usr/lib/systemd/system/docker.service.

```

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
