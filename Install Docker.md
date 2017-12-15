 DOCKER:
 es un proyecto de código abierto que permite automatizar el despliegue de aplicaciones dentro de “contenedores”. Éste contenedor empaqueta todo lo necesario para que uno o más procesos (servicios o aplicaciones) funcionen: código, herramientas del sistema, bibliotecas del sistema, dependencias, etc. Ésto garantiza que siempre se podrá ejecutar, independientemente del entorno en el que queramos desplegarlo. No hay que preocuparse de qué software ni versiones tiene nuestra máquina, ya que nuestra aplicación se ejecutará en el contenedor

 CARACTERÍSTICAS Las principales características de Docker son:
• Portabilidad: el contenedor Docker podemos desplegarlo en cualquier sistema, sin necesidad de volver a configurarlo o realizar las instalaciones necesarias para que la aplicación funcione, ya que todas las dependencias son empaquetadas con la aplicación en el contenedor.
• Ligereza: los contenedores Docker sólo contienen lo que las diferencia del sistema operativo en el que se ejecutan, no se virtualiza un SO completo.
• Autosuficiencia: un contenedor Docker no contiene todo un sistema operativo completo, sólo aquellas librerías, archivos y configuraciones necesarias para desplegar las funcionalidades que contenga

VENTAJAS Y DESVENTAJAS Usar contenedores Docker permite a desarrolladores y administradores de sistemas probar aplicaciones o servicios en un entorno seguro e igual al de producción, reduciendo los tiempos de pruebas y adaptaciones entre los entornos de prueba y producción. Las principales ventajas de usar contenedores Docker son:
• Las instancias se inician en pocos segundos.
• Son fácilmente replicables.
• Es fácil de automatizar y de integrar en entornos de integración continua.
• Consumen menos recursos que las máquinas virtuales tradicionales.
• Mayor rendimiento que la virtualización tradicional ya que corre directamente sobre el Kernel de la máquina en la que se aloja, evitando al hypervisor.
• Ocupan mucho menos espacio.
• Permite aislar las dependencias de una aplicación de las instaladas en el host.
• Existe un gran repositorio de imágenes ya creadas sobre miles de aplicaciones, que además pueden modificarse libremente. Por todo esto Docker ha entrado con mucha fuerza en el mundo del desarrollo, ya que permite desplegar las aplicaciones en el mismo entorno que tienen en producción o viceversa, permite desarrollarlas en el mismo entorno que tendrán en producción. Aunque también tiene algunas desventajas: • Sólo puede usarse de forma nativa en entornos Unix con Kernel igual o superior a 3.8. • Sólo soporta arquitecturas de 64 bits. • Como es relativamente nuevo, puede haber errores de código entre versiones.

USOS Y RECOMENDACIONES El uso de Docker está recomendado en: • Entornos de integración continua, es decir, cuando el paso de desarrollo a producción en un proyecto sea lo más a menudo posible, para así poder detectar fallos cuanto antes. • Para garantizar la integridad de las aplicaciones en diferentes entornos. • Cuando necesitemos tener entornos fácilmente desplegables, portables y desechables. • Cuando necesitemos un entorno fácilmente escalable.

ARQUITECTURA Docker usa una arquitectura cliente-servidor. El cliente de Docker habla con el demonio de Docker que hace el trabajo de crear, correr y distribuir los contenedores. Ambos pueden ejecutarse en el mismo sistema, o se puede conectar un cliente a un demonio Docker remoto. El cliente Docker y el demonio se comunican vía sockets o a través de una RESTfull API. (imagen pagina oficial). Explicamos un poco por orden la arquitectura o funcionamiento de Docker: El cliente de Docker (Docker Client) es la principal interfaz de usuario para Docker. Él acepta comandos del usuario y se comunica con el demonio Docker. El demonio Docker (Docker Engine) corre en una máquina anfitriona (host). El usuario no interactúa directamente con el demonio, en su lugar lo hace a través del cliente Docker.

COMPONENTES Según la documentación oficial:
ver sabores docker

DIFERENCIAS CON LAS MÁQUINAS VIRTUALES La principal diferencia es que una máquina virtual necesita tener virtualizado todo el sistema operativo, mientras que el contenedor Docker aprovecha el sistema operativo sobre el que se ejecuta, compartiendo el Kernel e incluso parte de sus bibliotecas. Para el SO anfitrión, cada contenedor no es más que un proceso que corre sobre el Kernel. El concepto de contenedor o “virtualización ligera”  no es nuevo. En Linux, LXC (Linux Containers) es una tecnología de virtualización a nivel de sistema operativo que utiliza dos características del Kernel, cgroups (que permite aislar y rastrear el uso de recursos) y namespaces (que permite a los grupos separarse, así no pueden verse unos a otros), para poder ejecutar procesos ligeros independientes en una sola máquina, aislados unos de otros, cada uno con su propia configuración de red. Ejemplos de esto son las jaulas de FreeBSD, OpenSolaris o Linux Vservers. Otra diferencia es el tamaño, una máquina virtual convencional puede ocupar bastante, sin embargo los contenedores Docker sólo contienen lo que las diferencia del sistema operativo en el que se ejecutan, ocupando una media de 150-250 Mb. En cuanto a recursos, el consumo de procesador y memoria RAM es mucho menor al no estar todo el sistema operativo virtualizado.
ver maquinas virtuales

Instalación
ver modo programador
ver activar hyper-v
ver virtualizar en bios

PRINCIPALES COMANDOS DOCKER Antes de empezar a usar Docker en la máquina que hemos preparado, vamos a familiarizarnos con los comandos que nos ofrece Docker. Escribiendo docker en la terminal nos aparece una lista de las opciones disponibles:
• attach: para acceder a la consola de un contenedor que está corriendo.
• build: construye un contenedor a partir de un Dockerfile. 
• commit: crea una nueva imagen de los cambios de un contenedor. 
• cp: copia archivos o carpetas desde el sistema de ficheros de un contenedor a el host.
• create: crea un nuevo contenedor. 
• daemon: crea un proceso demonio. 
• diff: comprueba cambios en el sistema de ficheros de un contenedor. 
• events: muestra eventos en tiempo real del estado de un contenedor. 
• exec: ejecuta un comando en un contenedor activo. 
• export: exporta el contenido del sistema de ficheros de un contenedor a un archivo .tar.
• history: muestra el historial de una imagen. 
• images: lista las imágenes que tenemos descargadas y disponibles. 
• import: crea una nueva imagen del sistema de archivos vacío e importa el contenido de un fichero .tar. • info: muestra información sobre los contenedores, imágenes, versión de docker. 
• inspect: muestra informaciones de bajo nivel del contenedor o la imagen. 
• kill: detiene a un contenedor activo. 
• load: carga una imagen desde un archivo .tar. 
• login: para registrarse en un servidor de registro de Docker, por defecto “https://index.docker.io/v1/”• logout: se desconecta del servidor de registro de Docker. 
• logs: obtiene los registros de un contenedor. 
• network connect: conecta un contenedor a una red. 
• network create: crea una nueva red con un nombre especificado por el usuario. 
• network disconnect: desconecta un contenedor de una red. 
• network inspect: muestra información detallada de una red. 
• network ls: lista todas las redes creadas por el usuario. 
• network rm: elemina una o más redes. 
• pause: pausa todos los procesos dentro de un contenedor. 
• port: busca el puerto público, el cual está nateado, y lo hace privado. 
• ps: lista los contenedores.
• pull: descarga una imagen o un repositorio del servidor de registros Docker. 
• push: envía  una imagen o un repositorio al servidor de registros de Docker. 
• rename: renombra un contenedor existente. 
• restart: reinicia un contenedor activo. 
• rm: elimina uno o más contenedores. • rmi: elimina una o más imágenes. 
• run: ejecuta un comando en un nuevo contenedor. 
• save: guarda una imagen en un archivo .tar • search: busca una imagen en el índice de Docker. 
• start: inicia un contenedor detenido. 
• stats: muestra el uso de los recursos de los contenedores. 
• stop: detiene un contenedor. 
• tag: etiqueta una imagen en un repositorio. 
• top: busca los procesos en ejecución de un contenedor. 
• unpause: reanuda un contenedor pausado. 
• update: actualiza la configuración de uno o más contenedores. 
• version: muestra la versión de Docker instalada. 
• volume create: crea un volumen. 
• volume inspect: devuelve información de bajo nivel de un volumen. 
• volume ls: lista los volúmenes. 
• volume rm: elimina un volumen. 
• wait: bloquea hasta detener un contenedor, entonces muestra su código de salida.
Y si queremos saber cómo funciona un comando concreto debemos escribir “docker COMMAND --help”, por ejemplo vemos cómo usar el comando save: 
docker save --help 

IMÁGENES Las imágenes son plantillas de sólo lectura que usamos como base para lanzar un contenedor. Una imagen Docker se compone de un sistema de archivos en capas una sobre la otra. En la base tenemos un sistema de archivos de arranque, bootfs (parecido al sistema de archivos de Linux) sobre el que arranca la imagen base. 

Para comprobar las imágenes que tenemos en local tenemos que ejecutar 
• docker images

Ahora mismo sólo tenemos la imagen que se descargó cuándo comprobamos que se había instalado correctamente Docker. Podemos buscar la imagen que queremos con el comando search. Por ejemplo si queremos saber que imágenes hay disponibles de Ubuntu.
• docker search ubuntu

Para descargar una imagen debemos hacerlo con el comando pull (también podemos hacerlo con el el comando run como veremos más adelante, pero ésta es la forma correcta). Sintaxis: 
• docker pull ubuntu

Para ver los detalles de una imagen ejecutamos el siguiente comando:
• docker inspect ubuntu 

Una vez que tenemos disponible una imagen podemos ejecutar cualquier contenedor.



EJECUCIÓN DE CONTENEDORES COMANDO RUN Podemos crear un contenedor con el comando run. Sintaxis: 
• docker run ubuntu echo mi primer contenedor

Entre las opciones se encuentran (lista completa aquí): 
• -a, --attach: para conectarnos a un contenedor que está corriendo. 
• -d, --detach: corre un contenedor en segundo plano. 
• -i, --interactive: habilita el modo interactivo. 
• --name: le pone nombre a un contenedor. Ahora vamos a ejecutar un contenedor sobre la imagen de ubuntu que tenemos descargada
• docker run ubuntu echo mensaje

Algo a tener en cuenta es que si la imagen que estamos poniendo en el comando run no la tuviéramos en local, Docker primero la descargaría y la guardaría en local y luego seguiría con la construcción capa por capa del contenedor

• docker ps para ver los contenedores que este corriendo
• docker ps -a para ver todos los contenedores

Si queremos especificar un nombre en particular podemos hacerlo con el parámetro --name. 
• docker run --name prueba ubuntu echo prueba
• docker ps -a para ver todos los contenedores

MODO INTERACTIVO Cómo hemos visto, cuando creamos un contenedor con run, debemos especificar un comando que se va a ejecutar y cuando se acabe su ejecución el contenedor se detendrá. Básicamente el contenedor se crea para ejecutar dicho comando. Tenemos la opción de ejecutar un contenedor en modo interactivo con los flags:
• -t: ejecuta una terminal. 
• -i: nos comunicamos con el contenedor en modo interactivo.
• docker run -it ubuntu bash

Si abrimos otra terminal y ejecutamos un docker ps, vemos que tenemos el contenedor corriendo.
Pero si nos salimos de la shell del contenedor, éste se detendrá.

El contenedor sigue ahí así que podemos reiniciarlo
• docker start nombrecontenedor y/o id

Y conectarnos a él
• docker attach tiny_turing 

O ejecutar con exec comandos dentro de un contenedor activo, por ejemplo una shell
• docker exec -it nombrecontenedor /bin/sh 

CREANDO IMÁGENES DOCKER Las imágenes, como hemos visto, son plantillas de sólo lectura, que usamos de base para lanzar contenedores. Por tanto lo que hagamos en el contenedor sólo persiste en ese contenedor, las modificaciones no las hacemos en la imagen. Si queremos que dichos cambios sean permanentes, debemos crear una nueva imagen con el contenedor personalizado. 

Vamos a realizar un ejemplo. Tenemos la imagen base de ubuntu. Lanzamos un contenedor con esa imagen base en el modo interactivo que vimos anteriorementey vamos a instalar una serie de paquetes.

• docker run -it --name afn01 ubuntu /bin/bash 
--> apt-get update 
Instalamos por ejemplo git.
-->  apt-get install git

Ahora vamos a guardar los cambios realizados en la imagen. Tenemos que salir del contenedor y ejecutar el comando “commit”. 
Para poder utilizar esta imagen con los cambios, tenemos que crear una nueva imagen, con el comando:
• docker commit -m "Instalado Git" -a "andrés naranjo" c906d56c7aa5 git/ubuntu:v1

Con:
commit: creamos una nueva imagen en nuestro repositorio loca
-m: añadimos un comentario. 
-a: autor de la imagen. 
c906d56c7aa5: identificador del contenedores. 
git/ubuntu:v1: el nombre que le damos a la imagen.

A partir de aquí podemos crear un contenedor con esta nueva imagen como base y ya tendrá instalado git. Lo comprobamos:
• docker run -it --name git git/ubuntu:v1 /bin/bash

DETACHED o BACKGROUND Nos permite ejecutar un contenedor en segundo plano y poder correr comandos sobre el mismo en cualquier momento mientras esté en ejecución. Lo hacemos con el flag -d. Se dice que es un contenedor demonizado y se ejecutará indefinidamente. Vamos a ver un ejemplo. Primero creamos un contenedor  basado en la imagen ubuntu que hemos descargado en modo interactivo.

• docker run -it --name 2plano ubuntu /bin/bash 
Y le vamos a instalar un servidor web. 
• docker run -it --name apache ubuntu /bin/bash 
apt-get install apache2

Ahora creamos una nueva imagen del contenedor con apache instalado.
• docker commit -m "Instalado Apache" -a "andrés naranjo" 2ca26b7f9d5c  apache/ubuntu:v1 
Ahora podemos arrancar un contenedor en segundo plano.

• docker run -d --name server apache/ubuntu:v1 /usr/sbin/apache2ctl -DFOREGROUND

Vamos a hacer que el servicio apache no se detenga con -D y que el contenedor se ejecute en segundo plano con -d.
Comprobamos nuestros contenedores.
• docker ps

Podemos ver los procesos que se están ejecutando en un contenedor con “top”.
• docker top web_server 

Una vez que hemos creado el contenedor y lo tenemos corriendo en segundo plano, podemos conectarnos a él mediante el comando exec, que ejecuta un proceso en el contenedor
• docker exec -it server /bin/bash 

Vemos que al salirnos del contenedor, éste no se detiene:
 --> exit 
 • docker ps 

MAPEO DE PUERTOS Para que la aplicación que nos está sirviendo nuestro contenedor, por ejemplo el servidor web instalado en el contenedor anteior, tenemos que mapear los puertos. Es decir, al crear el contenedor, éste no está disponible al exterior. Para que lo esté tenemos que redireccionar el puerto 22 del contenedor a uno de nuestra máquina. Usamos para ello el flag -p. Vamos a ejecutar un contenedor basado en la imagen apache, en segundo plano y con la redirección de puertos activa. Podemos hacer la redirección de puertos con las opciones: -p: especificamos a qué puerto queremos la redirección. -P: le dice a Docker que si expone algún tipo de puerto haga el fordwarding a un puerto aleatorio. Este se una cuando usamos un Dockerfile.

Lanzamos el contenedor:

• docker run -d -p 8000:80 --name apache_2 apache/ubuntu:v1 /usr/sbin/apache2ctl -D FOREGROUND

Comprobamos
• docker ps 

Vemos que nos indica la redirección. Si accedemos desde nuestra máquina local veremos el servidor web en el puerto 8000 del anfitrión.

LINKS
Para que dos contenedores colaboren entre ellos podemos abrir puertos y que se comuniquen por ahí, pero Docker nos ofrece la posibilidad de crear links entre contenedores. Primero creamos un contenedor.

• docker run -d --name links01 apache/ubuntu:v1 /usr/sbin/apache2ctl -D FOREGROUND 

No hemos mapeado ningún puerto, el servidor no es accesible desde fuera. Ahora creamos otro con la opción --link para que Docker cree un túnel entre los dos contenedores.

• docker run -d --name links02 --link links01 apache/ubuntu:v1 /usr/sbin/apache2ctl -D FOREGROUND 

Comprobamos los contenedores activos con 
• docker ps

Este túnel es unidireccional y sólo podremos acceder desde el que se ha ejecutado con --link
al otro.

• docker exec links02 env

VOLÚMENES Podemos montar volúmenes de datos en nuestros contenedores. Con el flag -v podemos montar un directorio dentro de nuestro contenedor. Así podemos incorporar datos que estarían disponibles para nuestro contenedor. Además seguirá apareciendo después de un reinicio del contenedor, serán persistentes. También podemos compartir volúmenes de datos entre contenedores. Si dichos volúmenes están anclados al sistema operativo anfitrión, no serán eliminados por Docker cuando desaparezca el contenedor. Vamos a crear un contenedor al que le pasemos un volumen.

• docker run -it --name ejemplovolumen -v /volumen01/ apache/ubuntu:v1 /bin/bash

Cuando listamos vemos la carpeta que encontramos montado en nuestro contenedor el directorio volumen01.
Esto es muy útil para pasarle ficheros a los contenedores y que los datos que nos interesen en ellos sean persistentes. También podemos crear un contenedor que monte un volumen de otro con la opción: 
–-> volume-from
• docker run -d -p 8085:80 --name volumen01 --volumes-from ejemplo_volumen apache/ubuntu:v1 /usr/sbin/apache2ctl -D FOREGROUND 








VARIABLES DE ENTORNO Podemos modificar las variables de entorno de un contenedor con el flag -e (--env) También podemos pasarlas desde un fichero externo con ---env-file Y podemos ver las variables con:
• docker exec a60 env PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin HOSTNAME=a6066a7a2383 HOME=/root

CONFIGURACIÓN DE RED Por defecto los contenedores tienen las conexiones de redes habilitadas. Podemos deshabilitarlas pasando la opción --net none. Con el comando docker run podemos especificar 3 configuraciones referentes a la red: -dns: para configurar un servidor dns en el contenedor.

• docker run -i -t -dns=”8.8.8.8” ubuntu /bin/bash

-net: crear una red y conectar el servidor a ella.

• docker network create -d overlay mi-red 

• docker network create -d overlay mi-red # docker run -net=mi-red -i -t -d ubuntu
-add-host: agregando una entrada en el fichero /etc/hosts del contenedor.
• docker run -i -t –add-host apache:10.0.0.10 ubuntu /bin/bash

ELIMINAR CONTENEDORES Para eliminar un contenedor podemos hacerlo por el nombre o por el ID. Realmente sólo nos hace falta los 3 primeros dígitos del ID. Para poder eliminarlo debe estar parado. Si no lo estuviera tendríamos que pararlo con “stop”. Utilizamos el comando rm. Si queremos ahorrarnos el paso de pararlo usamos -f
• docker stop idcontenedor y/o nombre
• docker rm idcontenedor y/o nombre
• docker rm -f idcontenedor y/o nombre

Dockerfile:
es un archivo legible por el demonio Docker, que contiene una serie de instrucciones para automatizar el proceso de creación de un contenedor.

CONSTRUIR EL CONTENEDOR El comando docker build irá siguiendo las instrucciones del Dockerfile y  armando la imagen. El Dockerfile puede encontrarse en el directorio en el que estemos o en un repositorio. El demonio de Docker es el que se encarga de construir la imagen siguiendo las instrucciones línea por línea y va lanzando los resultados por pantalla. Cada vez que ejecuta una nueva instrucción se hace en una nueva imagen, son imágenes intermedias, hasta que muestra el ID de la imagen resultante de ejecutar todas las instrucciones. El daemon irá haciendo una limpieza automática de las imágenes intermedias. Estas imágenes intermedias con la caché de Docker. Y ¿para qué sirve que Docker cree una caché de imágenes intermedias? Pues si por alguna razón la creación de la imagen falla (por un comando erróneo por ejemplo), cuando lo corregimos y volvemos a construir la imagen a partir del dockerfile, el demonio no iniciará todo el proceso, sino que usará las imágenes intermedias y continuará en el punto dónde falló.


DOCKERFILE COMANDOS FROM Indicamos una imagen base para construir el contenedor y opcionalmente un tag (si no la indicamos docker asumirá “latest” por defecto, es decir buscará la última versión). Lo que hace docker al leer esto es buscar en la máquina local una imagen que se llama, si no la encuentra la descargará de los repositorios. Sintaxis:
FROM <imagen> 
FROM <imagen>:<tag>

MAINTAINER Es información del creador y mantenedor de la imagen, usuario, correo, etc. Sintaxis:
MAINTAINER <nombre> <correo> <cualquier_info>

RUN
Ejecuta directamente comandos dentro del contenedor y luego aplica/persiste los cambios creando una nueva capa encima de la anterior con los cambios producidos de la ejecución del comando y se hace un commit de los resultados. Posteriormente sigue con la siguiente instrucción. Sintaxis: 
RUN <comando> → modo shell, /bin/sh -c 
RUN [“ejecutable”,”parámetro1”,”parámetro2”] → modo ejecución, que permite correr comandos en imágenes base que no tengan /bin/sh o hacer uso de otra shell.

ENV
Establece variables de entorno del contenedor. Dichas variables se pasarán a todas las instrucciones RUN que se ejecuten posteriores a la declaración de las variables. Podemos especificar varias variables de entorno en una sóla instrucción ENV. Sintaxis:
ENV <key> <value> <key> <value> ENV <key>=<value> <key>=<value>

Si queremos sustituir una variable aunque esté definida en el Dockerfile, al ejecutar un contenedor podemos especificarla y tomará dicho valor, tenga el que tenga en el Dockerfile.
docker run -env <key>=<valor> También podemos pasar variables de entorno con el comando “docker run” utilizando el parámetro -e, para especificar que dichas variables sólo se utilizarán en tiempo de ejecución. Podemos usar estas variables en otras instrucciones llamándolas con $nombre_var o $ {nombre_var}. Por ejemplo:
ENV DESTINO_DIR /opt/app WORKDIR $DESTINO_DIR

ADD 
Esta instrucción copia los archivos o directorios de una ubicación especificada en <fuente> y los agrega al sistema de archivos del contenedor en la ruta especificada en <destino>. En fuente podemos poner una URL, docker se encargará de descargar el archivo y copiarlo al destino. Si el archivo origen está comprimido, lo descomprime en el destino cómo si usáramos “tar -x”. Sintaxis:
ADD <fuente>..<destino> ADD [“fuente”,...”destino”] El parámetro <fuente> acepta caracteres comodín tipo ?,*, etc. 

COPY
Es igual que ADD, sólo que NO admite URLs remotas y archivos comprimidos como lo hace ADD.

WORKDIR Permite especificar en qué directorio se va a ejecutar una instrucción RUN, CMD o ENTRYPOINT. Puede ser usada varias veces dentro de un Dockerfile. Si se da una ruta relativa, esta será la ruta relativa de la instrucción WORKDIR anterior. Podemos usar variables de entorno previamente configuradas, por ejemplo:
ENV rutadir /ruta WORKDIR $rutadir

USER
Sirve para configurar el nombre de usuario a usar cuando se lanza un contenedor y para la ejecución de cualquier instrucción RUN, CMD o ENTRYPOINT posteriores

EXPOSE Se utiliza para asociar puertos, permitiéndonos exponer un contenedor al exterior (internet, host,etc.). Esta instrucción le especifica a Docker que el contenedor escucha en los puertos especificados. Pero EXPOSE no hace que los puertos puedan ser accedidos desde el host, para esto debemos mapear los puertos usando la opción -p en docker run. Por ejemplo:
EXPOSE 80 443 docker run centos:centos7 -p 8080:80

CMD
Esta instrucción es similar al comando RUN pero con la diferencia de que se ejecuta cuando instanciamos o arrancamos el contenedor, no en la construcción de la imagen. Sólo puede existir una única instrucción CMD por cada Dockerfile y puede ser útil para ejecutar servicios que ya estén instalados o para correr archivos ejecutables especificando su ubicación.

ENTRYPOINT Cualquier argumento que pasemos en la línea de comandos mediante docker run serán anexados después de todos los elementos especificados mediante la isntrucción ENTRYPOINT, y anulará cualquier elemento especificado con CMD. Esto permite pasar cualquier argumento al punto de entrada. Sintaxis: ENTRYPOINT [“ejecutable”,”parámetro1”,”parámetro2”] → forma de ejecución ENTRYPOINT comando parámetro1 parámetro 2 → forma shell ENTRYPOINT nos permite indicar qué comando se va a ejecutar al iniciar el contenedor, pero en este caso el usuario no puede indicar otro comando al iniciar el contenedor. Si usamos esta opción es porque no esperamos que el usuario ejecute otro comando que el especificado

ARCHIVO DOCKERIGNORE
Es recomendable colocar cada DockerFile en un directorio limpio, en el que sólo agregemos los ficheros que sean necesarios. Pero es posible que tengamos algún archivo en dicho directorio, que cumpla alguna función pero que no queremos que sea agregado a la imagen. Para esto usamos .dockerignore, para que docker build excluya esos archivos durante la creación de la imagen. Un ejemplo de .dockerignore */prueba* */*/prueba prueba?

EJEMPLO DOCKERFILE Vamos a lanzar un contenedor haciendo uso del siguiente Dockerfile, que hemos colocado en una carpeta llamada /wordpress.

crear 
app.js
var http = require('http')
var server = http.createServer(function (request, response) {
        response.writeHead(200, {'Content-Type': 'text/plain'});
        response.end('Hola mundo desde un contenedor Docker con nodejs.');
});
server.listen(8089);
console.log('Server running at http://127.0.0.1:8089');

crear
package.json
{
    "name": "prueba",
    "description": "prueba",
    "version": "0.0.1",
    "private": true,
    "dependencies": {
        "express": "latest"
    }
}

crear 
Dockerfile

FROM google/nodejs
WORKDIR /app
ADD package.json /app/
RUN npm install
ADD . /app
EXPOSE 8089
CMD node app.js



• docker build -t app .

• docker images

• docker run -d -p 80:8089 -i app
mauricio pulgarin
instalar docker en ubuntu:16.04
descargar ubuntu y virtualbox

https://www.ubuntu.com/download/server/thank-you?country=CO&version=16.04.3&architecture=amd64
https://virtualbox.uptodown.com/windows/descargar

sudo apt-get update
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository \
   "deb [arch=armhf] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"


sudo apt-get update

sudo apt-get install docker

sudo su
Adduser afn
gpasswd -a afn sudo

