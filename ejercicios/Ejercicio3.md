# PPS-Unidad0-Actividad5-Docker-JcMartin

![logotipo IES Valle del Jerte](../imagenes/excelencia.jpeg)

Aprendiendo "Docker" - Ejercicios Prácticos.
======

[Anterior](./ejercicios/Ejercicio2.md)
[Ejercicio 3 - Redes](#Docker---Ejercicio-3)
[Siguiente](./ejercicios/Ejercicio4.md)


--- 


### Docker - Ejercicio 3

#### Despliegue de Nextcloud + mariadb/postgreSQL
Vamos a desplegar la aplicación nextcloud con una base de datos (puedes elegir mariadb o PostgreSQL) (NOTA: Para que no te de errores utiiliza la imagen mariadb:10.5). Te puede servir el ejercicio que hemos realizado para desplegar Wordpress. Para ello sigue los siguientes pasos:

Crea una red de tipo bridge.

Crea el contenedor de la base de datos conectado a la red que has creado.

La base de datos se debe configurar para crear una base de datos y un usuario.

Además el contenedor debe utilizar almacenamiento (volúmenes o bind mount) para guardar la información.

 Puedes seguir la documentación de mariadb o la de PostgreSQL.


A continuación, siguiendo la documentación de la imagen nextcloud, crea un contenedor

conectado a la misma red, e indica las variables adecuadas para que se configure de forma adecuada y realice la conexión a la base de datos.

El contenedor también debe ser persistente usando almacenamiento.

Accede a la aplicación usando un navegador web.


Deberás entregar los siguientes pantallazos comprimidos en un zip o en un documento pdf:

#### Ejercicio 1.- Creando la Base de Datos

Pantallazo con la instrucción para crear el contenedor de la base de datos.

![Pantallazo ejercicio 1](../imagenes/Docker3-mariadb1.png)


#### Ejercicio 2.- Creando la Aplicación

Pantallazo con la instrucción para crear el contenedor de la aplicación.

![Pantallazo ejercicio 2](../imagenes/Docker3-nexcloud2.png)


#### Ejecrcio 3.- Acceso a la Interface web Nexcloud

Pantallazo donde se ve el acceso a la aplicación desde un navegador web.

![Pantallazo ejercicio 3](../imagenes/Docker3-nexcloud3.png)


[Inicio](#Docker---Ejercicio-3)
