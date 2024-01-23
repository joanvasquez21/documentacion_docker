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

## Networking container
Son entornos virtuales que permiten que los contenedores se comuniquen entre sí y con otros recursos de red. Estas redes son lógicas y aíslan el tráfico de red de un conjunto de contenedores, lo que facilita la gestion de la comunicación.
1.- Crear una red
   
![image](https://github.com/joanvasquez21/documentacion_docker/assets/70104624/da09d56d-70df-4736-9aa5-5eba9e27e400)

2.- Lista de los dos contenedores que vamos a conectar a la red

![image](https://github.com/joanvasquez21/documentacion_docker/assets/70104624/5bf5502b-b102-410f-98f0-c8d085ba0ac7)

3.- Utilizamos los identificadores para conectarlos 

![image](https://github.com/joanvasquez21/documentacion_docker/assets/70104624/06a83d75-9397-42db-a04e-5c79522d8870)

4.- Inspeccionar los contenedores conectados a la misma red

![image](https://github.com/joanvasquez21/documentacion_docker/assets/70104624/b6a66f07-0789-4bd9-85bb-56bdd125078e)


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

## Volumenes
## Introducción
En Docker, un volumen es un mecanismo que permite persistir y compartir datos entre contenedores y el sistema host de una manera independiente del ciclo de vida del contenedor. Los volúmenes proporcionan una forma eficiente de manejar el almacenamiento de datos, permitiendo que los datos persistan incluso cuando el contenedor que los utiliza se detiene o se elimina.

## Explicación sencilla:
Un volumen en Docker es como una carpeta especial que puede contener datos y que está fuera del contenedor. Esta carpeta se puede compartir entre varios contenedores y mantiene sus datos incluso si el contenedor se apaga o se borra.

## Ejemplo:
Supongamos que estás ejecutando una base de datos en un contenedor Docker y deseas asegurarte de que los datos de la base de datos no se pierdan cuando el contenedor se detiene o se elimina. En lugar de almacenar los datos dentro del contenedor, puedes utilizar un volumen para mantener esos datos fuera del contenedor.

# Creación de un volumen
* `docker volume create mydata` : Se crea un volumen llamado "mydata"
```bash
$ docker volume create mydata
```
* `docker volume create mydata` : Ejecuta un contenedor de MySQL utilizando el volumen "mydata"
```bash
$ docker run -d \
  --name mysql-container \
  -e MYSQL_ROOT_PASSWORD=my-secret-pw \
  -v mydata:/var/lib/mysql \
  mysql:latest
```

## En este ejemplo:

• Se crea un volumen llamado "mydata" utilizando docker volume create.
• Un contenedor de MySQL se ejecuta con la opción -v mydata:/var/lib/mysql, lo que significa que el directorio /var/lib/mysql dentro del contenedor está vinculado al volumen "mydata".
• Los datos de la base de datos MySQL se almacenan en el volumen "mydata", y estos datos persistirán incluso si el contenedor se detiene o se elimina.
• Si necesitas ejecutar otro contenedor de MySQL o cualquier otro servicio que requiera acceso a esos datos, simplemente puedes vincularlo al mismo volumen "mydata", facilitando el intercambio de datos entre contenedores.
