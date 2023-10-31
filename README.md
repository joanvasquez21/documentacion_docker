# Guía de Uso de Docker :whale:

¡Bienvenido a la guía de uso de Docker! :rocket:

## Introducción
Docker es una plataforma de contenedores que facilita la creación, implementación y administración de aplicaciones en contenedores. Los contenedores son una forma excelente de encapsular una aplicación y sus dependencias en un entorno aislado y portátil. :package:

## Instalacion de docker y wsl2 
1.-Asegúrate de tener Docker instalado antes de continuar. Puedes descargarlo desde [Docker's Website](https://docs.docker.com/desktop/install/windows-install/).

2.-Instalar WSL mediante comando, leer: [Wsl microsoft](https://learn.microsoft.com/en-us/windows/wsl/install).
```bash
$ wsl install
```

3.- Activamos la virtualización
![image](https://github.com/joanvasquez21/documentacion_docker/assets/70104624/233b5eaa-b395-459e-8247-0e1f00e83eee)

## Empezemos
* `docker pull` :  se utiliza para descargar (o "extraer") una imagen de Docker desde un registro de imágenes, como el Docker Hub o un registro privado.
```bash
$ docker pull NOMBRE_DE_LA_IMAGEN
```
* `docker container run`: se utiliza para crear y ejecutar un contenedor a partir de una imagen.
```bash
$ docker container run NOMBRE_DE_LA_IMAGEN
```
*`docker network create`: se utiliza para crear una red personalizada en un entorno de contenedor.
```bash
$ docker network create NOMBRE_DE_LA_RED
```
*`docker network connect`: se utiliza para conectar contenedores.
```bash
$ docker network connect NOMBRE_DE_LA_RED ID_DEL_CONTENEDOR
```
