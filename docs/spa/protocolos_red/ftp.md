# FTP

El **Protocolo de transferencia de archivos** (en inglés **File Transfer Protocol** o **FTP**) es un protocolo de red para la transferencia de archivos entre sistemas conectados a una red TCP (Transmission Control Protocol), basado en la arquitectura cliente-servidor. Desde un equipo cliente se puede conectar a un servidor para descargar archivos desde él o para enviarle archivos, independientemente del sistema operativo utilizado en cada equipo.

El servicio FTP es ofrecido por la capa de aplicación del modelo de capas de red TCP/IP al usuario, utilizando normalmente el puerto de red 20 y el 21. Un problema básico de FTP es que está pensado para ofrecer la máxima velocidad en la conexión, pero no la máxima seguridad, ya que todo el intercambio de información, desde el login y password del usuario en el servidor hasta la transferencia de cualquier archivo, se realiza en texto plano sin ningún tipo de cifrado, con lo que un posible atacante puede capturar este tráfico, acceder al servidor y/o apropiarse de los archivos transferidos.

Para solucionar este problema son de gran utilidad aplicaciones como SCP y SFTP, incluidas en el paquete SSH, que permiten transferir archivos pero cifrando todo el tráfico.

## Historia

El protocolo FTP se empezó a utilizar en abril de 1971, publicado como el RFC 114, antes de que existiera la pila TCP/IP. La estructura general fue establecida en 1973. Fue modificado varias veces, añadiendo nuevos comandos y funcionalidades. Al final se publicó el RFC 959 en octubre de 1985, que es la que se utiliza actualmente.

## El Modelo FTP

En el modelo, el intérprete de protocolo (PI) de usuario inicia la conexión de control en el puerto 21. Las órdenes FTP estándar las genera el PI de usuario y se transmiten al proceso servidor a través de la conexión de control. Las respuestas estándar se envían desde la PI del servidor hasta la PI de usuario por la conexión de control como respuesta a las órdenes.

Estas órdenes FTP especifican parámetros para la conexión de datos (puerto de datos, modo de transferencia, tipo de representación y estructura) y la naturaleza de la operación sobre el sistema de archivos (almacenar, recuperar, añadir, borrar, etc.). El proceso de transferencia de datos (DTP) de usuario u otro proceso en su lugar, debe esperar a que el servidor inicie la conexión al puerto de datos especificado (puerto 20 en modo activo o estándar) y transferir los datos en función de los parámetros que se hayan especificado.

Vemos también en el diagrama que la comunicación entre cliente y servidor es independiente del sistema de archivos utilizado en cada computadora, de manera que no importa que sus sistemas operativos sean distintos, porque las entidades que se comunican entre sí son los PI y los DTP, que usan el mismo protocolo estandarizado: el FTP.

También hay que destacar que la conexión de datos es bidireccional, es decir, se puede usar simultáneamente para enviar y para recibir, y no tiene por qué existir todo el tiempo que dura la conexión FTP. Pero tenía en sus comienzos un problema, y era la localización de los servidores en la red. Es decir, el usuario que quería descargar algún archivo debía conocer en qué máquina estaba ubicado. La única herramienta de búsqueda de información que existía era Gopher, con todas sus limitaciones.

### Primer buscador de información

Gopher significa 'lanzarse sobre' la información. Es un servicio cuyo objetivo es la localización de archivos a partir de su título. Consiste en un conjunto de menús de recursos ubicados en diferentes máquinas que están intercomunicadas. Cada máquina sirve un área de información, pero su organización interna permite que todas ellas funcionen como si se tratase de una sola máquina. El usuario navega a través de estos menús hasta localizar la información buscada, y desconoce exactamente de qué máquina está descargando dicha información. Con la llegada de Internet, los potentes motores de búsqueda dejaron el servicio Gopher, y la localización de los servidores FTP dejó de ser un problema. En la actualidad, cuando el usuario se descarga un archivo a partir de un enlace de una página web no llega ni a saber que lo está haciendo desde un servidor FTP. El servicio FTP ha evolucionado a lo largo del tiempo y hoy día es muy utilizado en Internet, en redes corporativas, Intranets, etc. Soportado por cualquier sistema operativo, existe gran cantidad de software basado en el protocolo FTP.

## Servidor FTP

Un servidor FTP es un programa especial que se ejecuta en un equipo servidor normalmente conectado a Internet (aunque puede estar conectado a otros tipos de redes, LAN, MAN, etc.). Su función es permitir el intercambio de datos entre diferentes servidores/ordenadores.

Por lo general, los programas servidores FTP no suelen encontrarse en los ordenadores personales, por lo que un usuario normalmente utilizará el FTP para conectarse remotamente a uno y así intercambiar información con él.

Las aplicaciones más comunes de los servidores FTP suelen ser el alojamiento web, en el que sus clientes utilizan el servicio para subir sus páginas web y sus archivos correspondientes; o como servidor de backup (copia de seguridad) de los archivos importantes que pueda tener una empresa. Para ello, existen protocolos de comunicación FTP para que los datos se transmitan cifrados, como el SFTP (Secure File Transfer Protocol).

### Ejemplos de Servidores

- Titan FTP Server
- WS_FTP Server

## Cliente FTP

Cuando un navegador no está equipado con la función FTP, o si se quiere cargar archivos en un ordenador remoto, se necesitará utilizar un programa cliente FTP. Un cliente FTP es un programa que se instala en el ordenador del usuario, y que emplea el protocolo FTP para conectarse a un servidor FTP y transferir archivos, ya sea para descargarlos o para subirlos.

Para utilizar un cliente FTP, se necesita conocer el nombre del archivo, el ordenador en que reside (servidor, en el caso de descarga de archivos), el ordenador al que se quiere transferir el archivo (en caso de querer subirlo nosotros al servidor), y la carpeta en la que se encuentra.

Algunos clientes de FTP básicos en modo consola vienen integrados en los sistemas operativos, incluyendo Microsoft Windows, DOS, GNU/Linux y Unix. Sin embargo, hay disponibles clientes con opciones añadidas e interfaz gráfica. Aunque muchos navegadores tienen ya integrado FTP, es más confiable a la hora de conectarse con servidores FTP no anónimos utilizar un programa cliente.

### **Acceso anónimo**

Los servidores FTP anónimos ofrecen sus servicios libremente a todos los usuarios, permiten acceder a sus archivos sin necesidad de tener un 'USER ID' o una cuenta de usuario. Es la manera más cómoda fuera del servicio web de permitir que todo el mundo tenga acceso a cierta información sin que para ello el administrador de un sistema tenga que crear una cuenta para cada usuario.

Si un servidor posee servicio 'FTP anonymous' solamente con teclear la palabra «anonymous», cuando pregunte por tu usuario tendrás acceso a ese sistema. No se necesita ninguna contraseña preestablecida, aunque tendrás que introducir una solo para ese momento, normalmente se suele utilizar la dirección de correo electrónico propia.

Solamente con eso se consigue acceso a los archivos del FTP, aunque con menos privilegios que un usuario normal. Normalmente solo podrás leer y copiar los archivos que sean públicos, así indicados por el administrador del servidor al que nos queramos conectar.

Normalmente, se utiliza un servidor FTP anónimo para depositar grandes archivos que no tienen utilidad si no son transferidos a la máquina del usuario, como por ejemplo programas, y se reservan los servidores de páginas web (HTTP) para almacenar información textual destinada a la lectura en línea.

### **Acceso de usuario**

Si se desea tener privilegios de acceso a cualquier parte del sistema de archivos del servidor FTP, de modificación de archivos existentes, y de posibilidad de subir nuestros propios archivos, generalmente se suele realizar mediante una cuenta de usuario. En el servidor se guarda la información de las distintas cuentas de usuario que pueden acceder a él, de manera que para iniciar una sesión FTP debemos introducir una autentificación (en inglés: *login*) y una contraseña (en inglés: *password*) que nos identifica unívocamente.

### **Cliente FTP basado en Web**

Un «cliente FTP basado en Web» no es más que un cliente FTP al cual podemos acceder a través de nuestro navegador web sin necesidad de tener otra aplicación para ello. El usuario se conecta mediante HTTP a un servidor web, y el servidor web se conecta mediante FTP al servidor de archivos. El servidor web actúa de intermediario haciendo pasar la información desde el servidor FTP en los puertos 20 y 21 hacia el puerto 80 HTTP que ve el usuario.

Siempre hay momentos en que nos encontramos fuera de casa, no llevamos el ordenador portátil encima y necesitamos realizar alguna tarea urgente desde un ordenador de acceso público, de un amigo, del trabajo, la universidad, etc. Lo más común es que no estén instaladas las aplicaciones que necesitamos y en muchos casos hasta carecemos de los permisos necesarios para realizar su instalación. Otras veces estamos detrás de un proxy o cortafuegos que no nos permite acceder a servidores FTP externos.

Al disponer de un cliente FTP basado en Web podemos acceder al servidor FTP remoto como si estuviéramos realizando cualquier otro tipo de navegación web. A través de un cliente FTP basado en Web podrás, crear, copiar, renombrar y eliminar archivos y directorios. Cambiar permisos, editar, ver, subir y descargar archivos, así como cualquier otra función del protocolo FTP que el servidor FTP remoto permita.

### **Acceso de invitado**

El acceso sin restricciones al servidor que proporcionan las cuentas de usuario implica problemas de seguridad, lo que ha dado lugar a un tercer tipo de acceso FTP denominado invitado (guest), que se puede contemplar como una mezcla de los dos anteriores.

La idea de este mecanismo es la siguiente: se trata de permitir que cada usuario conecte a la máquina mediante su login y su password, pero evitando que tenga acceso a partes del sistema de archivos que no necesita para realizar su trabajo, de esta forma accederá a un entorno restringido, algo muy similar a lo que sucede en los accesos anónimos, pero con más privilegios.

### **Ejemplos de Clientes FTPs**

Entre los varios clientes FTP que existen, se pueden mencionar los siguientes:

- net2ftp
- WebDrive
- Web-Ftp
- Jambai FTP
- ftp4net
- PHP FTP Client
- Asuk PHP FTP
- Weeble File Manager
- FileZilla
- Transmit

## Modos de conexión del cliente FTP

FTP admite dos modos de conexión del cliente. Estos modos se denominan activo (o Estándar, o PORT, debido a que el cliente envía comandos tipo PORT al servidor por el canal de control al establecer la conexión) y pasivo (o PASV, porque en este caso envía comandos tipo PASV). Tanto en el modo Activo como en el modo Pasivo, el cliente establece una conexión con el servidor mediante el puerto 21, que establece el canal de control.

### **Modo activo**

En modo Activo, el servidor siempre crea el canal de datos en su puerto 20, mientras que en el lado del cliente el canal de datos se asocia a un puerto aleatorio mayor que el 1024. Para ello, el cliente manda un comando PORT al servidor por el canal de control indicándole ese número de puerto, de manera que el servidor pueda abrirle una conexión de datos por donde se transferirán los archivos y los listados, en el puerto especificado.

Lo anterior tiene un grave problema de seguridad, y es que la máquina cliente debe estar dispuesta a aceptar cualquier conexión de entrada en un puerto superior al 1024, con los problemas que ello implica si tenemos el equipo conectado a una red insegura como Internet. De hecho, los cortafuegos que se instalen en el equipo para evitar ataques seguramente re

chazarán esas conexiones aleatorias. Para solucionar esto se desarrolló el modo pasivo. Aunque realmente no es así ya que seguramente la seguridad tendrá un problema grave.

### **Modo pasivo**

Cuando el cliente envía un comando PASV sobre el canal de control, el servidor FTP le indica por el canal de control, el puerto (mayor a 1024 del servidor. Ejemplo:2040) al que debe conectarse el cliente. El cliente inicia una conexión desde el puerto siguiente al puerto de control (Ejemplo: 1036) hacia el puerto del servidor especificado anteriormente (Ejemplo: 2040).

Antes de cada nueva transferencia tanto en el modo Activo como en el Pasivo, el cliente debe enviar otra vez un comando de control (PORT o PASV, según el modo en el que haya conectado), y el servidor recibirá esa conexión de datos en un nuevo puerto (aleatorio si es en modo pasivo o por el puerto 20 si es en modo activo).

### **Tipos de transferencia de archivos en FTP**

En el protocolo FTP existen 2 tipos de transferencia en ASCII y en binarios. Es importante conocer cómo debemos transportar un archivo a lo largo de la red, si no utilizamos las opciones adecuadas podemos destruir la información del archivo. Por eso, al ejecutar la aplicación FTP, debemos acordarnos de utilizar uno de estos comandos (o poner la correspondiente opción en un programa con interfaz gráfica):

- Tipo ASCII

Adecuado para transferir archivos que solo contengan caracteres imprimibles (archivos ASCII, no archivos resultantes de un procesador de texto), por ejemplo páginas HTML, pero no las imágenes que puedan contener. Se transforman algunos símbolos de control para mantenerlos compatibles entre diferentes sistemas, por ejemplo, si el archivo está alojado sobre un servidor linux, el salto de línea para los archivos de texto es "\n" (byte 10 en decimal). Si el cliente es un sistema Mac, el salto de línea es "\r" (byte 13 en decimal), este modo cambia estos símbolos de control para que el archivo sea legible en ambos lados, al igual que si se envía a un sistema windows, el salto de línea es "\r\n" (dos bytes, 13 y 10). Si se usa este modo en archivos que no son de texto plano, en el caso de intercambiarse entre diferentes sistemas, ese archivo quedará corrupto.

- Tipo Binario

Este tipo es usado cuando se trata de archivos comprimidos, ejecutables para PC, imágenes, archivos de audio, entre otros.

Ejemplos de cómo transferir algunos tipos de archivo dependiendo de su extensión:

| Extensión de archivo | Tipo de transferencia |
| --- | --- |
| txt (texto) | ascii |
| html (página WEB) | ascii |
| doc (documento) | binario |
| ps (poscript) | ascii |
| hqx (comprimido) | ascii |
| Z (comprimido) | binario |
| ZIP (comprimido) | binario |
| ZOO (comprimido) | binario |
| Sit (comprimido) | binario |
| pit (comprimido) | binario |
| shar (comprimido) | binario |
| uu (comprimido) | binario |
| ARC (comprimido) | binario |
| tar (empaquetado) | binario |

En la red existen diversas soluciones de software que desarrolla este tipo de tecnología, los más conocidos, son Filezilla (software libre) y CuteFTP (shareware).

## Comandos FTP

| Comando y argumentos | Acción que realiza |
| --- | --- |
| open puerta | Inicia una conexión con un servidor FTP. |
| close o disconnect | Finaliza una conexión FTP sin cerrar el programa cliente. |
| bye o quit | Finaliza una conexión FTP y la sesión de trabajo con el programa cliente. |
| cd directorio | Cambia el directorio de trabajo en el servidor. |
| delete archivo | Borra un archivo en el servidor |
| mdelete patrón | Borra múltiples archivos basado en un patrón que se aplica al nombre. |
| dir | Muestra el contenido del directorio en el que estamos en el servidor. |
| get archivo | Obtiene un archivo |
| noop No Operation | Se le comunica al servidor que el cliente está en modo de no operación, el servidor usualmente responde con un «ZZZ» y refresca el contador de tiempo inactivo del usuario. |
| mget archivos | Obtiene múltiples archivos |
| hash | Activa la impresión de caracteres # a medida que se transfieren archivos, a modo de barra de progreso. |
| lcd directorio | Cambia el directorio de trabajo local. |
| ls | Muestra el contenido del directorio en el servidor. |
| prompt | Activa/desactiva la confirmación por parte del usuario de la ejecución de comandos. Por ejemplo al borrar múltiples archivos. |
| put archivo | Envía un archivo al directorio activo del servidor. |
| mput archivos | Envía múltiples archivos. |
| pwd | Muestra el directorio activo en el servidor. |
| rename archivo | Cambia el nombre a un archivo en el servidor. |
| rmdir directorio | Elimina un directorio en el servidor si ese directorio está vacío. |
| status | Muestra el estado actual de la conexión. |
| bin o binary | Activa el modo de transferencia binario. |
| ascii | Activa el modo de transferencia en modo texto ASCII. |
| ! | Permite salir a línea de comandos temporalmente sin cortar la conexión. Para volver, teclear exit en la línea de comandos. |
| ? nombre de comando | Muestra la información relativa al comando. |
| ? o help | Muestra una lista de los comandos disponibles. |
| append nombre del archivo | Continua una descarga que se ha cortado previamente. |
| bell | Activa/desactiva la reproducción de un sonido cuando ha terminado cualquier proceso de transferencia de archivos. |
| glob | Activa/desactiva la visualización de nombres largos de nuestro PC. |
| literal | Con esta orden se pueden ejecutar comandos del servidor de forma remota. Para saber los disponibles se utiliza: literal help. |
| mkdir | Crea el directorio indicado de forma remota. |
| quote | Hace la misma función que literal. |
| send nombre del archivo | Envía el archivo indicado al directorio activo del servidor. |
| user | Para cambiar nuestro nombre de usuario y contraseña sin necesidad de salir de la sesión ftp. |

## Códigos de respuesta de FTP

A continuación se muestra un resumen de la respuesta de los códigos FTP que puede ser devuelto por un servidor FTP. Estos códigos se han estandarizado en RFC 959 por IETF. El código de respuesta es un valor de tres dígitos. El primer dígito se utiliza para indicar una de tres posibles resultados-el éxito, el fracaso o para indicar un error o una respuesta incompleta:

- 2yz - respuesta Éxito
- 4yz o 5yz - No hay respuesta
- 1yz o 3yz - Un error o una respuesta incompleta

El segundo dígito define la clase de error:

- x0z - Sintaxis. Estas respuestas se refieren a errores de sintaxis.
- x1z - Información. Las respuestas a las solicitudes de información.
- x2z - Conexiones. Respuestas en referencia al control y las conexiones de datos.
- x3z - Autenticación y contabilidad. Respuestas para el proceso de inicio de sesión y los procedimientos contables.
- x4z - No definido.
- x5z - Sistema de archivos. Estas respuestas transmiten códigos de estado del sistema de archivos del servidor.

El tercer dígito del código de respuesta se utiliza para proporcionar detalles adicionales para cada una de las categorías definidas por el segundo dígito.

## Conexión a un servidor FTP protegido desde navegador

Para iniciar sesión en un servidor FTP que requiere una contraseña teclee la URL de esta forma:

`ftp://<usuario>:<contraseña>@<servidor ftp>/<url-ruta>`

Donde `<usuario>` es el nombre de usuario, `<servidor ftp>` es el servidor FTP, `<contraseña>` es la contraseña de acceso, y `<url-ruta>` es el directorio donde iniciamos sesión.

Ejemplo: `ftp://alumno:alumnopass@ftp.example.com/public`
