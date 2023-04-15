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

[root@docker01 ~]# docker version
Client: Docker Engine - Community
 Version:           23.0.3
 API version:       1.42
 Go version:        go1.19.7
 Git commit:        3e7cbfd
 Built:             Tue Apr  4 22:04:21 2023
 OS/Arch:           linux/amd64
 Context:           default

Server: Docker Engine - Community
 Engine:
  Version:          23.0.3
  API version:      1.42 (minimum version 1.12)
  Go version:       go1.19.7
  Git commit:       59118bf
  Built:            Tue Apr  4 22:02:00 2023
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          1.6.20
  GitCommit:        2806fc1057397dbaeefbea0e4e17bddfbd388f38
 runc:
  Version:          1.1.5
  GitCommit:        v1.1.5-0-gf19387a
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0
  
  
  
  [root@docker01 ~]# docker info
Client:
 Context:    default
 Debug Mode: false
 Plugins:
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.10.4
    Path:     /usr/libexec/docker/cli-plugins/docker-buildx
  compose: Docker Compose (Docker Inc.)
    Version:  v2.17.2
    Path:     /usr/libexec/docker/cli-plugins/docker-compose

Server:
 Containers: 0
  Running: 0
  Paused: 0
  Stopped: 0
 Images: 0
 Server Version: 23.0.3
 Storage Driver: overlay2
  Backing Filesystem: xfs
  Supports d_type: true
  Using metacopy: false
  Native Overlay Diff: true
  userxattr: false
 Logging Driver: json-file
 Cgroup Driver: cgroupfs
 Cgroup Version: 1
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local logentries splunk syslog
 Swarm: inactive
 Runtimes: runc io.containerd.runc.v2
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: 2806fc1057397dbaeefbea0e4e17bddfbd388f38
 runc version: v1.1.5-0-gf19387a
 init version: de40ad0
 Security Options:
  seccomp
   Profile: builtin
 Kernel Version: 4.18.0-425.19.2.el8_7.x86_64
 Operating System: Red Hat Enterprise Linux 8.7 (Ootpa)
 OSType: linux
 Architecture: x86_64
 CPUs: 4
 Total Memory: 15.46GiB
 Name: docker01.themike.mx
 ID: c04c6ffc-6de8-4e2b-8149-b442cb51d08b
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 Registry: https://index.docker.io/v1/
 Experimental: false
 Insecure Registries:
  127.0.0.0/8
 Live Restore Enabled: false

  
  
```
5. agregue un usuario no root al grupo Docker
Si no desea utilizar "sudo" para ejecutar un comando Docker en su sistema, debe agregar el usuario no root de su sistema al grupo Docker. 
De esta forma, puede ejecutar el comando docker como usuario no root o actual. Este es un paso opcional.

```
[root@docker01 ~]# usermod -aG docker $USER
[root@docker01 ~]# reboot 
````

¡Y eso es todo! Ahora tienes Docker instalado en tu sistema RHEL 8.

## Trabajando con imágenes usando la interfaz de línea de comandos (CLI) de Docker
A continuación, se detallan los pasos para trabajar con imágenes utilizando la interfaz de línea de comandos (CLI) de Docker:

## Buscando imágenes en Docker Hub
Para buscar una imagen de Docker en el repositorio de Docker Hub, sigue estos pasos:

Visita https://hub.docker.com/ para buscar imágenes disponibles.

Ejecuta el siguiente comando:

```
[root@docker01 ~]# docker search httpd | head -n 10
NAME                                 DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
httpd                                The Apache HTTP Server Project                  4398      [OK]       
clearlinux/httpd                     httpd HyperText Transfer Protocol (HTTP) ser…   2                    
paketobuildpacks/httpd                                                               0                    
vulhub/httpd                                                                         0                    
jitesoft/httpd                       Apache httpd on Alpine linux.                   0                    
avenga/httpd-static                                                                  0                    
betterweb/httpd                                                                      0                    
centos/httpd-24-centos7              Platform for running Apache httpd 2.4 or bui…   45                   
manageiq/httpd                       Container with httpd, built on CentOS for Ma…   1                    [OK]
```

Salida del comando

El comando lista todas las imágenes disponibles en Docker Hub que contienen la palabra clave "httpd". Para cada imagen, muestra su nombre, descripción, número de estrellas y si es oficial o automatizada.

## Descargando imágenes desde Docker Hub

Una vez que hayas encontrado la imagen que deseas, descárgala utilizando el siguiente comando:
```
[root@docker01 ~]# docker pull httpd
Using default tag: latest
latest: Pulling from library/httpd
26c5c85e47da: Pull complete 
2d29d3837df5: Pull complete 
2483414a5e59: Pull complete 
e78016c4ba87: Pull complete 
757908175415: Pull complete 
Digest: sha256:a182ef2350699f04b8f8e736747104eb273e255e818cd55b6d7aa50a1490ed0c
Status: Downloaded newer image for httpd:latest
docker.io/library/httpd:latest
```

Si necesitas una versión específica de la imagen, agrega el tag correspondiente al final del comando. Por ejemplo:

```
root@docker01 ~]# docker pull httpd:2.2.29
2.2.29: Pulling from library/httpd
Image docker.io/library/httpd:2.2.29 uses outdated schema1 manifest format. Please upgrade to a schema2 image for better future compatibility. More information at https://docs.docker.com/registry/spec/deprecated-schema-v1/
4d2e9ae40c41: Pull complete 
a3ed95caeb02: Pull complete 
71da54557245: Pull complete 
721128148697: Pull complete 
bb02db57acca: Pull complete 
973e8b763f43: Pull complete 
9792a80ebd27: Pull complete 
Digest: sha256:0a39699d267aaee04382c6b1b4fe2fc30737450fe8d4fabd88eee1a3e0016144
Status: Downloaded newer image for httpd:2.2.29
docker.io/library/httpd:2.2.29
```

Salida del comando

El comando descarga la imagen httpd desde Docker Hub y muestra información sobre el proceso de descarga. En el ejemplo anterior, se descargó la versión "latest" de la imagen.

## Listando imágenes en tu sistema

Para verificar las imágenes descargadas en tu sistema, ejecuta el siguiente comando:

Ejemplo de ejecución

```
$ docker images

REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
httpd               latest              85f2c5846f52        2 weeks ago         138MB
httpd               2.2.29              ccb5efae6522        2 years ago         201MB
```

Salida del comando

El comando lista todas las imágenes descargadas en tu sistema. Para cada imagen, muestra su nombre, tag, identificador de imagen, fecha de creación y tamaño.

## Eliminando imágenes de tu sistema

Si deseas eliminar una imagen de tu sistema, utiliza el siguiente comando:

```
[root@docker01 ~]# docker rmi httpd:2.2.29
Untagged: httpd:2.2.29
Untagged: httpd@sha256:0a39699d267aaee04382c6b1b4fe2fc30737450fe8d4fabd88eee1a3e0016144
Deleted: sha256:78ef8a7db81acde885e627ceafbc7f2d76a052b44d679b9c274a18bce85d5ccc
Deleted: sha256:5d5325c9e14025425b154bcd4b4c4092fddc0cf28095dec4fda01da336a03aa6
Deleted: sha256:c04125bb67950cffe237d960070d48c9b29a00b27fcb12513406ecf0ab80d32d
Deleted: sha256:5f9dca6732ab55daa3c354a6de5c0e651a7032ad3700a8c5f5f2b4daefb3b8ef
Deleted: sha256:7a9b5807179ca1a30644ad5f8d0ff89c9970f6e30ed8957e7758321eff7036e4
Deleted: sha256:55efd6082c88416ed5089a9f9347d3493264931c11934299da4a0d0fe4aa22fb
Deleted: sha256:41324ac66556b527c8824ad9144cd2639e9753e4e387efde49fd2838082864ca
Deleted: sha256:c2b6854195202c32627a0918233531678a7f53ba89cb10c8ede6acc9c5139ab3
Deleted: sha256:5f7c1bd0a29de2d99977a1476cdc8eb357080a4831e91342738a2587e54bd095
Deleted: sha256:386ab9d75eab80ae1eedf219c639be1f398997e1b0773ccb05d4d0bbb7ca86d2
Deleted: sha256:080cf2d8b7f3c25eea37c4393b6696f30eb0411290ebaedc6dda57f17b375ec2
Deleted: sha256:64f09aa49f80203adc402b131fc8736961031f2b4478b1c5245bcaec404fd354
Deleted: sha256:a5dd5b712a2ae1a4868cedf54e44b8a63c8fd35c9a75edf74d64c099a9278331
Deleted: sha256:e10e5ea91f007db418b284f4adc5f0b98f374d79ae52b9687b0d6d33865ffbcf
Deleted: sha256:c69ae1aa46985cbaf186b6354c61a1d2e0d6af47133db47bf04f0c6eb9c858e9
```

Lista nuevamente tus imagenes y observa la salida.

## "Saving and Loading" imágenes de Docker

Es útil cuando se desea compartir una imagen de Docker con otros usuarios o trasladarla a otra máquina.

Para guardar una imagen de Docker, se utiliza el comando docker save seguido del nombre de la imagen y la ruta del archivo de destino donde se guardará la imagen.

```
[root@docker01 ~]# mkdir /mnt/docker ; cd /mnt/docker
```
```
[root@docker01 docker]# pwd
/mnt/docker
```
```
[root@docker01 docker]# ls
```
```
[root@docker01 docker]# docker save httpd -o httpd.tar
```
```
[root@docker01 docker]# ls
httpd.tar
```
```
[root@docker01 docker]# docker rmi httpd
Untagged: httpd:latest
Untagged: httpd@sha256:a182ef2350699f04b8f8e736747104eb273e255e818cd55b6d7aa50a1490ed0c
Deleted: sha256:4b7fc736cb48352ef2c989d63c74bed704fc5a0cd43eb5c7c7cf9ab7faf891d1
Deleted: sha256:24554be0fd03955c321886841f2a677f8057fa8cf93e0493a9cdc5a5eae54e71
Deleted: sha256:1c0d3c454ba728985456b066e59d4cfa163a06caa8471672f9e040706cbc2f82
Deleted: sha256:2698f8a274d166849ccc9e50434b996a8a392150b6ed0664c9d936e27c2aa3dc
Deleted: sha256:f5d462e0018cd9b8cd5b292a6046428dec593e0cd4b7856dd2d0968e4fc7538f
Deleted: sha256:ed7b0ef3bf5bbec74379c3ae3d5339e666a314223e863c70644f7522a7527461
```
```
[root@docker01 docker]# docker images
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
```
```
[root@docker01 docker]# docker load -i httpd.tar 
ed7b0ef3bf5b: Loading layer [==================================================>]  84.02MB/84.02MB
568467bc0db5: Loading layer [==================================================>]  3.072kB/3.072kB
16f81c3ee33a: Loading layer [==================================================>]  5.104MB/5.104MB
e7bd853ca2e7: Loading layer [==================================================>]  60.45MB/60.45MB
355053d0995e: Loading layer [==================================================>]  3.584kB/3.584kB
Loaded image: httpd:latest
```
```
[root@docker01 docker]# docker images
REPOSITORY   TAG       IMAGE ID       CREATED      SIZE
httpd        latest    4b7fc736cb48   3 days ago   145MB
```
## Manejando contenedores

### docker ps

El comando "docker ps" es utilizado en Docker para mostrar una lista de los contenedores de Docker que están actualmente en ejecución en el sistema. El proceso que realiza este comando se puede describir en los siguientes pasos:

1. Docker busca el demonio de Docker en ejecución en el sistema.

2. El comando "docker ps" se comunica con el demonio de Docker para obtener una lista de los contenedores en ejecución.

3. El demonio de Docker devuelve al comando una lista de los contenedores en ejecución, que incluye información como el ID del contenedor, el nombre del contenedor, la imagen utilizada para crear el contenedor, el estado actual del contenedor y otros detalles relevantes.

4. El comando "docker ps" presenta esta información en una tabla legible para el usuario, que muestra los detalles relevantes de cada contenedor en una línea separada.

```
[root@docker01 docker]# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```
```
[root@docker01 docker]# docker run httpd 
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
[Sat Apr 15 16:23:17.427825 2023] [mpm_event:notice] [pid 1:tid 139886229470528] AH00489: Apache/2.4.57 (Unix) configured -- resuming normal operations
[Sat Apr 15 16:23:17.428064 2023] [core:notice] [pid 1:tid 139886229470528] AH00094: Command line: 'httpd -D FOREGROUND'
```
### docker logs
El comando "docker logs ID" se utiliza en Docker para mostrar los registros o registros de un contenedor Docker específico. El proceso que realiza este comando se puede describir en los siguientes pasos:

1. Docker busca el demonio de Docker en ejecución en el sistema.

2. El comando "docker logs" se comunica con el demonio de Docker para buscar los registros del contenedor Docker específico que se especifica mediante su ID.

3. El demonio de Docker busca los registros del contenedor Docker especificado y los devuelve al comando "docker logs".

4. El comando "docker logs" presenta los registros del contenedor Docker especificado en la salida estándar del sistema.

```
[root@docker01 docker]# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```
```
[root@docker01 docker]# docker ps -a
CONTAINER ID   IMAGE     COMMAND              CREATED         STATUS                      PORTS     NAMES
485d7f760b45   httpd     "httpd-foreground"   3 minutes ago   Exited (0) 20 seconds ago             zealous_joliot
10d77bcb565e   httpd     "httpd-foreground"   3 minutes ago   Exited (0) 3 minutes ago              zen_goodall
```
```
[root@docker01 docker]# docker logs 10d77bcb565e
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
[Sat Apr 15 16:23:03.614604 2023] [mpm_event:notice] [pid 1:tid 140485278223680] AH00489: Apache/2.4.57 (Unix) configured -- resuming normal operations
[Sat Apr 15 16:23:03.614760 2023] [core:notice] [pid 1:tid 140485278223680] AH00094: Command line: 'httpd -D FOREGROUND'
[Sat Apr 15 16:23:11.415243 2023] [mpm_event:notice] [pid 1:tid 140485278223680] AH00491: caught SIGTERM, shutting down
```
```
[root@docker01 docker]# docker run -d httpd
fb69b457eb91f6df2d648ac230be0d1b8fa00912189d15cbef0d2f68f006bf7b
```
```
[root@docker01 docker]# docker ps
CONTAINER ID   IMAGE     COMMAND              CREATED         STATUS         PORTS     NAMES
fb69b457eb91   httpd     "httpd-foreground"   4 seconds ago   Up 3 seconds   80/tcp    stupefied_sinoussi
```

### Ejecutando comandos dentro de un contenedor

Ejecutar comandos dentro de un contenedor puede ser necesario por varias razones. Algunas de las razones comunes son las siguientes:

1. Configuración: A menudo, los contenedores Docker se utilizan para alojar aplicaciones o servicios que requieren una configuración especializada. Es posible que sea necesario ejecutar comandos para realizar una configuración específica dentro del contenedor, como configurar las variables de entorno, configurar la red, cambiar los permisos de los archivos, etc.

2. Depuración: Si una aplicación o servicio que se ejecuta en un contenedor Docker no funciona correctamente, se puede utilizar un comando para ejecutar una herramienta de depuración o una shell interactiva dentro del contenedor y analizar los registros y la salida de la aplicación en tiempo real.

3. Mantenimiento: En ocasiones, es posible que se necesite realizar tareas de mantenimiento dentro del contenedor, como la actualización de paquetes o la limpieza de archivos y directorios. Se pueden utilizar comandos para realizar estas tareas dentro del contenedor.

4. Pruebas: Los comandos se pueden utilizar para ejecutar pruebas dentro del contenedor Docker para verificar la funcionalidad de una aplicación o servicio que se ejecuta en el contenedor.

```
[root@docker01 docker]# docker ps
CONTAINER ID   IMAGE     COMMAND              CREATED         STATUS         PORTS     NAMES
fb69b457eb91   httpd     "httpd-foreground"   4 minutes ago   Up 4 minutes   80/tcp    stupefied_sinoussi
```
```
[root@docker01 docker]# docker exec -i fb69b457eb91 ls -l /
total 4
drwxr-xr-x.   1 root root    6 Apr 12 01:47 bin
drwxr-xr-x.   2 root root    6 Dec  9 19:15 boot
drwxr-xr-x.   5 root root  340 Apr 15 16:33 dev
drwxr-xr-x.   1 root root   66 Apr 15 16:33 etc
drwxr-xr-x.   2 root root    6 Dec  9 19:15 home
drwxr-xr-x.   1 root root   30 Apr 12 01:47 lib
drwxr-xr-x.   2 root root   34 Apr 11 00:00 lib64
drwxr-xr-x.   2 root root    6 Apr 11 00:00 media
drwxr-xr-x.   2 root root    6 Apr 11 00:00 mnt
drwxr-xr-x.   2 root root    6 Apr 11 00:00 opt
dr-xr-xr-x. 168 root root    0 Apr 15 16:33 proc
drwx------.   1 root root   24 Apr 12 01:45 root
drwxr-xr-x.   3 root root   30 Apr 11 00:00 run
drwxr-xr-x.   2 root root 4096 Apr 11 00:00 sbin
drwxr-xr-x.   2 root root    6 Apr 11 00:00 srv
dr-xr-xr-x.  13 root root    0 Apr 15 15:05 sys
drwxrwxrwt.   1 root root    6 Apr 12 01:47 tmp
drwxr-xr-x.   1 root root   19 Apr 11 00:00 usr
drwxr-xr-x.   1 root root   41 Apr 11 00:00 var
```
```
[root@docker01 docker]# docker exec -it fb69b457eb91 /bin/bash

root@fb69b457eb91:/usr/local/apache2# date
Sat Apr 15 16:38:39 UTC 2023

root@fb69b457eb91:/usr/local/apache2# whoami 
root

root@fb69b457eb91:/usr/local/apache2# cat /etc/os-release 
PRETTY_NAME="Debian GNU/Linux 11 (bullseye)"
NAME="Debian GNU/Linux"
VERSION_ID="11"
VERSION="11 (bullseye)"
VERSION_CODENAME=bullseye
ID=debian
HOME_URL="https://www.debian.org/"
SUPPORT_URL="https://www.debian.org/support"
BUG_REPORT_URL="https://bugs.debian.org/"
```
### docker start & docker stop

Los comandos "docker start" y "docker stop" se utilizan en Docker para iniciar y detener contenedores Docker, respectivamente. A continuación se presentan algunas situaciones en las que es necesario utilizar estos comandos:

Iniciar un contenedor: Después de crear un contenedor Docker utilizando el comando "docker run", es necesario usar el comando "docker start" para iniciar el contenedor. Esto asegura que el contenedor se inicie y se ejecute correctamente para que pueda utilizarse para alojar aplicaciones o servicios.

Detener un contenedor: Cuando se necesita realizar tareas de mantenimiento o actualización en el sistema host o en el contenedor mismo, es necesario detener el contenedor utilizando el comando "docker stop". Esto asegura que cualquier proceso en ejecución dentro del contenedor se detenga de manera segura antes de detener el contenedor.

Cambiar la configuración de un contenedor: Si se necesitan cambiar la configuración de un contenedor, como la configuración de la red o los volúmenes, es necesario detener el contenedor utilizando el comando "docker stop", realizar los cambios necesarios y, a continuación, iniciar el contenedor nuevamente utilizando el comando "docker start".

Liberar recursos del sistema: Si se ejecutan varios contenedores Docker en un sistema y se necesita liberar recursos del sistema, es necesario detener los contenedores que no se están utilizando utilizando el comando "docker stop".

```
[root@docker01 docker]# docker ps
CONTAINER ID   IMAGE     COMMAND              CREATED          STATUS          PORTS     NAMES
fb69b457eb91   httpd     "httpd-foreground"   21 minutes ago   Up 21 minutes   80/tcp    stupefied_sinoussi
```
```
[root@docker01 docker]# docker stop fb69b457eb91
fb69b457eb91
```
```
[root@docker01 docker]# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```
```
[root@docker01 docker]# docker start fb69b457eb91
fb69b457eb91
```
```
[root@docker01 docker]# docker ps
CONTAINER ID   IMAGE     COMMAND              CREATED          STATUS         PORTS     NAMES
fb69b457eb91   httpd     "httpd-foreground"   22 minutes ago   Up 2 seconds   80/tcp    stupefied_sinoussi
```
### docker --publish
El port mapping o mapeo de puertos en Docker es una técnica que se utiliza para exponer los puertos de un contenedor Docker al host o al mundo exterior. Esto permite que la aplicación o el servicio que se ejecuta dentro del contenedor Docker esté disponible para su uso en otros dispositivos o redes externas.

El mapeo de puertos se puede realizar utilizando la opción "-p" o "--publish" del comando "docker run". Esta opción permite especificar el puerto del host y el puerto del contenedor que se deben mapear. Por ejemplo, si se desea mapear el puerto 80 del host al puerto 8080 del contenedor, se puede utilizar el siguiente comando:
```
[root@docker01 docker]# docker ps
CONTAINER ID   IMAGE     COMMAND              CREATED          STATUS         PORTS     NAMES
fb69b457eb91   httpd     "httpd-foreground"   26 minutes ago   Up 4 minutes   80/tcp    stupefied_sinoussi
```
```
[root@docker01 docker]# curl localhost:8080
curl: (7) Failed to connect to localhost port 8080: Connection refused
```
```
[root@docker01 docker]# docker run -d -p 8080:80 httpd
eb0b95cda538c0799a58721141522fc372263668ec92440452336c41a04a7e49
```
```
[root@docker01 docker]# docker ps
CONTAINER ID   IMAGE     COMMAND              CREATED          STATUS         PORTS                                   NAMES
eb0b95cda538   httpd     "httpd-foreground"   5 seconds ago    Up 4 seconds   0.0.0.0:8080->80/tcp, :::8080->80/tcp   amazing_rosalind
fb69b457eb91   httpd     "httpd-foreground"   26 minutes ago   Up 4 minutes   80/tcp                                  stupefied_sinoussi
```
```
[root@docker01 docker]# curl localhost:8080
<html><body><h1>It works!</h1></body></html>
```

### Ejercicio
```
[root@docker01 docker]# docker run -d -p 8083:80 httpd
5ebb5649340eaaa9cabb26e3c7db89df291b18e416572980466ae3e9f3e71696
```
```
[root@docker01 docker]# docker ps
CONTAINER ID   IMAGE     COMMAND              CREATED          STATUS          PORTS                                   NAMES
5ebb5649340e   httpd     "httpd-foreground"   4 seconds ago    Up 3 seconds    0.0.0.0:8083->80/tcp, :::8083->80/tcp   serene_shtern
```
```
[root@docker01 docker]# docker exec -it 5ebb5649340e /bin/bash
```
```
root@5ebb5649340e:/usr/local/apache2# cd htdocs/
```
```
root@5ebb5649340e:/usr/local/apache2/htdocs# cat << EOF > index.html
> <!DOCTYPE html>
<html>
<head>
        <meta http-equiv="refresh" content="0; url=https://www.citig.mx/">
</head>
<body>
        <p>Redireccionando a https://www.citig.mx/...</p>
</body>
</html>
EOF
```
```
root@5ebb5649340e:/usr/local/apache2/htdocs# cat index.html 
<!DOCTYPE html>
<html>
<head>
	<meta http-equiv="refresh" content="0; url=https://www.citig.mx/">
</head>
<body>
	<p>Redireccionando a https://www.citig.mx/...</p>
</body>
</html>
```
```
root@5ebb5649340e:/usr/local/apache2/htdocs# exit
exit
```
```
[root@docker01 docker]# curl localhost:8083
<!DOCTYPE html>
<html>
<head>
	<meta http-equiv="refresh" content="0; url=https://www.citig.mx/">
</head>
<body>
	<p>Redireccionando a https://www.citig.mx/...</p>
</body>
</html>



