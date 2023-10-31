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
*`docker network inspect`: se utiliza para inspeccionar la red con los contenedores conectados.
```bash
$ docker network inspect NOMBRE_DE_LA_RED
```

## Ejercicio:
Montar la imagen de MariaDB con el tag jammy, publicar en el puerto 3309 del contenedor con el puerto 3306 de nuestro
equipo, colocarle el nombre al contenedor de maria-db (--name maria-db) y definir las siguientes variables de entorno:

• MARIADB_USER=user
• MARIADB_PASSWORD=password
• MARIADB_ROOT_PASSWORD=root-password
• MARIADB_DATABASE=w-db

2. Conectarse usando Table Plus a la base de datos con las credenciales del usuario (NO EL ROOT).
3. Conectarse a la base de datos world-db.
4. Ejecutar el query de creación de tablas e inserción proporcionado.
5. Revisar que efectivamente tengamos el contenedor

## Solucion 
1.- Configuramos la base de datos de MariaDB en un contenedor Docker con las variables del ejercicio, utilizando como tag jammy

![image](https://github.com/joanvasquez21/documentacion_docker/assets/70104624/5bda9980-d5b1-40c7-9604-7612aa932468)

2.-Nos conectamos usando Table Plus

![image](https://github.com/joanvasquez21/documentacion_docker/assets/70104624/a21fbdc4-e19a-4ad9-86fa-e7b348e74c97)

3.- Utilizamos el query de creacion de tablas

![image](https://github.com/joanvasquez21/documentacion_docker/assets/70104624/efe5974e-9d49-41d0-af3e-55018fbb7986)

5.-Tenemos el contenedor

![image](https://github.com/joanvasquez21/documentacion_docker/assets/70104624/fcb8151d-157a-498c-b661-13443d9d9a2a)

