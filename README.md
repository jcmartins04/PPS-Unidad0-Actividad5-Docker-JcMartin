# PPS-Unidad0-Actividad5-Docker-JcMartin

![logotipo IES Valle del Jerte](./imagenes/excelencia.jpeg)

Aprendiendo "Docker" - Ejercicios Prácticos.
======


[Ejercicio 1 - Imagenes](./ejercicios/Ejercicio1.md)

[Ejercicio 2 - Almacenamiento](./ejercicios/Ejercicio2.md)

[Ejercicio 3 - Redes](./ejercicios/Ejercicio3.md)

[Ejercicio 4 - Multicontenedor](./ejercicios/Ejercicio4.md)

[Ejercicio 5 - Creando Imágenes](./ejercicios/Ejercicio5.md)



--- 


### Docker - Ejercicios prácticos



#### 1.- Imágenes Docker

Una imagen Docker es un paquete ligero, independiente y ejecutable que incluye todo lo necesario para ejecutar una aplicación,
como el código, las bibliotecas, las dependencias, las variables de entorno y los archivos de configuración.
Actúa como una plantilla de solo lectura a partir de la cual se crean contenedores. 

Cada imagen está compuesta por capas que representan modificaciones o adiciones realizadas durante su creación.

Estas capas son gestionadas por el sistema de archivos de Docker para maximizar la reutilización y minimizar el almacenamiento.

Por ejemplo, múltiples imágenes pueden compartir las mismas capas base (como un sistema operativo o dependencias comunes), reduciendo el tamaño total.

Las imágenes Docker son creadas usando un archivo de configuración llamado **Dockerfile**, donde se especifican los pasos necesarios
para construir la imagen. Los comandos en el Dockerfile, como `FROM` (definir una imagen base), `RUN` (ejecutar comandos) y `COPY` (copiar archivos),
son utilizados para personalizar la imagen.

Una vez construida, una imagen puede ser almacenada en un registro, como Docker Hub o un registro privado, desde donde se puede
distribuir y utilizar en diferentes entornos. Al ejecutar una imagen, se crea un contenedor, que es una instancia activa de esa imagen.
Esto permite que las aplicaciones sean portátiles, replicables y consistentes en cualquier plataforma compatible con Docker.


[Ejercicio 1 - Imagenes](./ejercicios/Ejercicio1.md)


#### 2.- Almacenamiento en Docker

El almacenamiento en Docker se refiere a las formas de gestionar datos persistentes que necesitan ser accesibles por los contenedores, ya que, por defecto,
el sistema de archivos dentro de un contenedor es efímero y se pierde al detener o eliminar el contenedor. Docker ofrece varias opciones de almacenamiento
para garantizar la persistencia y el intercambio de datos.

1. **Volumes (volúmenes)**: Son la forma más recomendada para almacenar datos persistentes. Los volúmenes son gestionados por Docker y almacenados fuera del sistema de archivos del contenedor, lo que los hace independientes del ciclo de vida de los contenedores. Son fáciles de compartir entre varios contenedores y
se pueden respaldar o cifrar.

2. **Bind mounts**: Permiten conectar un directorio específico del host al contenedor. Son útiles para acceder directamente a los datos del sistema anfitrión,
pero requieren más cuidado porque Docker no los administra.

3. **tmpfs mounts**: Almacenan datos en la memoria RAM del host en lugar de en disco. Son ideales para datos sensibles o temporales que no necesitan persistir.

El uso adecuado del almacenamiento en Docker depende de las necesidades de la aplicación, como el rendimiento, la persistencia o la accesibilidad compartida.
Además, Docker permite gestionar y monitorear estos métodos de almacenamiento para optimizar recursos y mantener la seguridad.


[Ejercicio 2 - Almacenamiento](./ejercicios/Ejercicio2.md)


#### 3.- Redes

Docker proporciona un sistema de redes flexible que permite a los contenedores comunicarse entre sí, con el host y con redes externas.
Las redes en Docker son gestionadas por su motor de redes, que facilita la creación, configuración y administración de diferentes tipos de redes
según las necesidades de las aplicaciones. Los principales tipos de redes en Docker son:

##### 1. **Bridge (puente)**  
Es la red predeterminada para contenedores que no especifican una red personalizada. Los contenedores conectados a una red de tipo bridge pueden
comunicarse entre sí usando sus nombres de contenedor como DNS. Es ideal para configuraciones simples donde los contenedores necesitan interactuar
solo dentro del mismo host.

##### 2. **Host**  
En esta configuración, el contenedor comparte la pila de red del host, eliminando el aislamiento de la red. Esto significa que el contenedor usará
directamente la IP y los puertos del host. Es útil cuando el rendimiento de la red es crítico o cuando se necesitan configuraciones específicas como
el uso de puertos privilegiados.

##### 3. **Overlay**  
Esta red conecta múltiples hosts Docker a través de una red virtual superpuesta. Se utiliza principalmente en clústeres Docker Swarm para permitir que
los servicios distribuidos se comuniquen de manera transparente. Es ideal para aplicaciones escalables y distribuidas en múltiples nodos.

##### 4. **Macvlan**  
Permite asignar una dirección MAC única a cada contenedor, haciéndolos aparecer como dispositivos físicos en la red del host.
Es útil para integrar contenedores directamente en redes existentes, especialmente en configuraciones heredadas o cuando se necesitan
configuraciones avanzadas de red.

##### 5. **None**  
Los contenedores en esta red no tienen acceso a la red externa ni a otras redes Docker. Es útil para ejecutar aplicaciones que no requieren
conectividad o para aislar completamente ciertos contenedores.

##### Beneficios y configuración  
Docker facilita la configuración de redes mediante comandos simples, como `docker network create`, y permite personalizar aspectos como el rango de
direcciones IP, subredes y gateways. También integra funciones como DNS interno para que los contenedores puedan resolverse por nombre sin
configuraciones adicionales.

Al elegir un tipo de red, es importante considerar las necesidades específicas de la aplicación, como el nivel de aislamiento, la escala y
el rendimiento necesario.


[Ejercicio 3 - Redes](./ejercicios/Ejercicio3.md)


#### 4.- Multicontenedor


Docker Compose es una herramienta que permite definir y administrar aplicaciones multicontenedor de manera sencilla. Utiliza un archivo de configuración en formato YAML, generalmente llamado `docker-compose.yml`, donde se describe cómo se deben construir y conectar los servicios que conforman una aplicación.
Esto incluye los contenedores, redes, volúmenes y otras configuraciones necesarias.

Con Docker Compose, puedes especificar detalles como la imagen que usará cada servicio, las variables de entorno, los puertos a exponer, las dependencias entre servicios y los volúmenes para persistir datos. Por ejemplo, es ideal para proyectos que requieren múltiples componentes como una base de datos,
un servidor web y un sistema de caché.

Una vez definido el archivo, comandos simples como `docker-compose up` inician todos los servicios, y `docker-compose down` los detiene y limpia los recursos
asociados. Esto facilita la replicación de entornos consistentes en desarrollo, pruebas y producción.

Docker Compose es especialmente útil en aplicaciones complejas, ya que automatiza y organiza la gestión de contenedores, permitiendo trabajar con entornos
reproducibles y simplificando el despliegue de sistemas completos.

Aquí tienes un resumen de los comandos más importantes de Docker Compose y su función:

### Comandos básicos
1. **`docker-compose up`**  
   Inicia todos los servicios definidos en el archivo `docker-compose.yml`.  
   - Opción `-d`: Ejecuta los servicios en segundo plano (modo *detached*).  

2. **`docker-compose down`**  
   Detiene y elimina los contenedores, redes y volúmenes creados por `docker-compose up`.  
   - Opción `--volumes`: También elimina los volúmenes asociados.

3. **`docker-compose build`**  
   Construye o reconstruye las imágenes de los servicios según lo definido en el archivo.

4. **`docker-compose ps`**  
   Muestra el estado de los servicios en ejecución.

5. **`docker-compose logs`**  
   Muestra los registros de salida de los servicios.  
   - Opción `-f`: Sigue mostrando los registros en tiempo real.

### Comandos de gestión
6. **`docker-compose start`**  
   Inicia los servicios que ya están creados pero detenidos.

7. **`docker-compose stop`**  
   Detiene los servicios en ejecución sin eliminarlos.

8. **`docker-compose restart`**  
   Reinicia los servicios en ejecución.

### Comandos avanzados
9. **`docker-compose exec <servicio> <comando>`**  
   Ejecuta un comando dentro de un contenedor específico.  
   Ejemplo: `docker-compose exec web bash`.

10. **`docker-compose run <servicio> <comando>`**  
   Crea y ejecuta un contenedor temporal para un servicio, útil para tareas específicas.  
   Ejemplo: `docker-compose run app python manage.py migrate`.

11. **`docker-compose config`**  
   Valida y muestra la configuración del archivo `docker-compose.yml`.

12. **`docker-compose scale <servicio>=<cantidad>`**  
   Escala un servicio a un número específico de instancias (puede requerir una configuración adecuada en redes y puertos).

13. **`docker-compose pull`**  
   Descarga las imágenes definidas en el archivo sin ejecutarlas.

14. **`docker-compose version`**  
   Muestra la versión instalada de Docker Compose.

Estos comandos simplifican el desarrollo y la gestión de aplicaciones multicontenedor, haciendo que las tareas de despliegue,
pruebas y mantenimiento sean más eficientes.


[Ejercicio 4 - Multicontenedor](./ejercicios/Ejercicio4.md)


#### 5.- Creando Imágenes


[Ejercicio 5 - Creando Imágenes](./ejercicios/Ejercicio5.md)
