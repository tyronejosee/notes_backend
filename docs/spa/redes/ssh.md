# SSH

SSH (Secure SHell) es un protocolo y programa diseñado para el acceso remoto seguro a un servidor a través de un canal cifrado. Además de permitir la conexión a otros dispositivos, SSH facilita la transferencia segura de datos, la gestión de claves RSA para evitar el uso de contraseñas al conectarse a dispositivos, y la creación de canales seguros para transmitir datos de otras aplicaciones. También puede redirigir el tráfico del Sistema de Ventanas X (X Window System) para ejecutar programas gráficos de manera remota. El puerto TCP utilizado por SSH es el 22.

Este protocolo establece comunicaciones seguras entre dos sistemas utilizando una arquitectura cliente/servidor, permitiendo a los usuarios conectarse a un host de forma remota. A diferencia de otros protocolos de comunicación remota como FTP o Telnet, SSH cifra la sesión de conexión, lo que impide que alguien pueda obtener contraseñas en texto plano. SSH se diseñó para reemplazar métodos más antiguos y menos seguros de acceso remoto a través de la línea de comandos, como telnet o rsh. Un programa relacionado, scp, sustituye a otros programas diseñados para copiar archivos entre hosts, como rcp, ya que estas aplicaciones antiguas no cifran las contraseñas durante la transmisión entre el cliente y el servidor.

## Funcionamiento

Necesita tres puntos indispensables: usuario, puerto y servidor. El cliente SSH va a contactar con el servidor para iniciar la conexión. Ese servidor está escuchando a través del puerto 22 o el que se le haya asignado. Posteriormente el servidor va a enviar la clave pública y comienzan a organizar los parámetros y abrir un canal seguro. El cliente inicia sesión para conectarse a ese servidor.

## Seguridad

SSH trabaja de forma similar a como se hace con telnet. La diferencia principal es que SSH usa técnicas de cifrado que hacen que la información que viaja por el medio de comunicación vaya de manera no legible, evitando que terceras personas puedan descubrir el usuario y contraseña de la conexión ni lo que se escribe durante toda la sesión; aunque es posible atacar este tipo de sistemas por medio de ataques de REPLAY y manipular así la información entre destinos.

El protocolo SSH proporciona los siguientes tipos de protección:

- Después de la conexión inicial, el cliente puede verificar que se está conectando al mismo servidor al que se conectó anteriormente.
- El cliente transmite su información de autenticación al servidor usando una encriptación robusta de 128 bits.
- Todos los datos enviados y recibidos durante la sesión se transfieren por medio de encriptación de 128 bits, lo cual los hace extremadamente difícil de descifrar y leer.
- El cliente tiene la posibilidad de reenviar aplicaciones X11 desde el servidor. Esta técnica, llamada reenvío por X11, proporciona un medio seguro para usar aplicaciones gráficas sobre una red.

Ya que el protocolo SSH encripta todo lo que envía y recibe, se puede usar para asegurar protocolos inseguros. El servidor SSH puede convertirse en un conducto para convertir en seguros los protocolos inseguros mediante el uso de una técnica llamada reenvío por puerto.

Hay diferentes estructuras de criptografía que pueden ser aplicadas a la hora de usar el protocolo SSH en esa demanda. Son, básicamente, tres alternativas:

- Simétrica
- Asimétrica
- Hashing

La criptografía simétrica es realizada por medio de una clave secreta, esa que es compartida apenas entre el servidor y el usuario. Su papel es encriptar o desencriptar el mensaje que es transferido en ese proceso, sin embargo, el Secure Shell solo ofrece la lectura del contenido mediante la presentación de esa clave.

La criptografía asimétrica usa dos claves, una para el cliente y otra para el servidor, para que haya la criptografía de los datos transferidos. Las claves son llamadas públicas y privadas, formando entonces la combinación necesaria para generar el SSH y su protocolo de seguridad. En ese modelo, la clave pública es distribuida de forma abierta y compartida. Sin embargo, a partir de ella no es posible descubrir cuál es la clave privada. Eso sucede gracias a un proceso que funciona de la siguiente manera: mensajes criptografiados por claves públicas solo pueden ser desencriptados por la clave privada de la misma máquina.

El Hashing es un método unidireccional de criptografía usado en el SSH. Esta práctica consiste en crear un hash, por medio de un algoritmo, para garantizar que el mensaje será protegido en una forma específica de criptografía y códigos de autenticación.

## Ataque más Común

El ataque más común consiste en un ataque de fuerza bruta, estos funcionan probando cada combinación posible que el usuario podría usar como contraseña y luego la prueba para ver si es la contraseña correcta. Para ver si la contraseña es correcta o no, verifica si hay errores en la respuesta del servidor. A medida que aumenta la longitud de la contraseña, la cantidad de tiempo utilizada para encontrar la contraseña correcta también aumenta rápidamente. Eso significa que las contraseñas cortas son bastante fáciles de descifrar. Para hacer más efectivo este ataque se usa el apoyo de diccionarios estos son herramientas con la lista de posibles contraseñas para usar contra el sistema de destino hasta que obtenga la contraseña correcta para el usuario.

## Historia

Al principio solo existían los r-commands, que eran los basados en el programa rlogin, el cual funciona de una forma similar a telnet.

La primera versión del protocolo y el programa eran libres y los creó un finlandés llamado Tatu Ylönen, pero su licencia fue cambiando y terminó apareciendo la compañía SSH Communications Security, que lo ofrecía gratuitamente para uso doméstico y académico, pero exigía el pago a otras empresas. En el año 1997 (dos años después de que se creara la primera versión) se propuso como borrador en la IETF.

A principios de 1999 se empezó a escribir una versión que se convertiría en la implementación libre por excelencia, la de OpenBSD, llamada OpenSSH.

## Versiones

Existen 2 versiones de SSH, la versión 1 de SSH hace uso de muchos algoritmos de cifrado patentados (sin embargo, algunas de estas patentes han expirado) y es vulnerable a un agujero de seguridad que potencialmente permite a un intruso insertar datos en la corriente de comunicación. La suite OpenSSH bajo Red Hat Enterprise Linux utiliza por defecto la versión 2 de SSH, la cual tiene un algoritmo de intercambio de claves mejorado que no es vulnerable al agujero de seguridad en la versión 1. Sin embargo, la suite OpenSSH también soporta las conexiones de la versión 1.
