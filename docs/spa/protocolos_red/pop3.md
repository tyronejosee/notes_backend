# POP3

En informática se utiliza el **Post Office Protocol** (**POP3**, *Protocolo de Oficina de Correo* o "Protocolo de Oficina Postal") en clientes locales de correo electrónico para obtener los mensajes de correo electrónico almacenados en un servidor remoto, denominado Servidor POP. Es un protocolo de nivel de aplicación en el Modelo OSI.

Las versiones del protocolo POP, informalmente conocido como POP1 y POP2, se han quedado obsoletas debido a las últimas versiones de POP3. En general cuando se hace referencia al término ***POP***, se refiere a *POP3* dentro del contexto de protocolos de correo electrónico.

## Características

POP3 está diseñado para recibir correo, que en algunos casos no es para enviarlo; esto le permite a los usuarios con conexiones intermitentes o muy lentas (tales como las conexiones por módem), descargar su correo electrónico mientras tienen conexión y revisarlo posteriormente incluso estando desconectados. Cabe mencionar que aunque algunos clientes de correo incluyen la opción de *dejar los mensajes en el servidor*, el funcionamiento general es: un cliente que utilice POP3 se conecta, obtiene todos los mensajes, los almacena en la computadora del usuario como mensajes nuevos, los elimina del servidor y finalmente se desconecta. En contraste, el protocolo IMAP permite los modos de operación conectado y desconectado.

Los clientes de correo electrónico que utilizan IMAP dejan por lo general los mensajes en el servidor hasta que el usuario los elimina directamente. Esto y otros factores hacen que la operación de IMAP permita a múltiples clientes acceder al mismo buzón de correo.

La mayoría de los clientes de correo electrónico soportan POP3 o IMAP; sin embargo, solo unos cuantos proveedores de internet ofrecen IMAP como valor agregado de sus servicios.

Los clientes que utilizan la opción *dejar mensajes en el servidor* por lo general utilizan la orden UIDL (Unique Identification Listing). La mayoría de las órdenes de POP3 identifican los mensajes dependiendo de su número ordinal del servidor de correo. Esto genera problemas al momento que un cliente pretende dejar los mensajes en el servidor, ya que los mensajes con número cambian de una conexión al servidor a otra. Por ejemplo un buzón de correo contenía 5 mensajes en la última conexión, después otro cliente elimina el mensaje número 3, si se vuelve a iniciar otra conexión, ya el número que tiene el mensaje 4 pasará a ser 3, y el mensaje 5 pasará a ser número 4 y la dirección de estos dos mensajes cambiara.

El UIDL proporciona un mecanismo que evita los problemas de numeración. El servidor le asigna una cadena de caracteres única y permanente al mensaje. Cuando un cliente de correo compatible con POP3 se conecta al servidor utiliza la orden UIDL para obtener el mapeo del identificador de mensaje. De esta manera el cliente puede utilizar ese mapeo para determinar qué mensajes hay que descargar y cuáles hay que guardar al momento de la descarga.

Al igual que otros viejos protocolos de internet, POP3 utilizaba un mecanismo de firmado sin cifrado. La transmisión de contraseñas de POP3 en texto plano aún se da. En la actualidad POP3 cuenta con diversos métodos de autenticación que ofrecen una diversa gama de niveles de protección contra los accesos ilegales al buzón de correo de los usuarios. Uno de estos es **APOP**, el cual utiliza funciones MD5 para evitar los ataques de contraseñas. Mozilla, Eudora, Novell Evolution así como Mozilla Thunderbird implementan funciones APP.

## Órdenes

Para establecer una conexión a un servidor POP, el cliente de correo abre una conexión TCP en el puerto 110 del servidor. Cuando la conexión se ha establecido, el servidor POP envía al cliente POP y después las dos máquinas se envían entre sí otras órdenes y respuestas que se especifican en el protocolo.

Como parte de esta comunicación, al cliente POP se le pide que se autentifique (Estado de autenticación), donde el nombre de usuario y la contraseña del usuario se envían al servidor POP. Si la autenticación es correcta, el cliente POP pasa al Estado de transacción, en este estado se pueden utilizar órdenes LIST, RETR y DELE para mostrar, descargar y eliminar mensajes del servidor, respectivamente. Los mensajes definidos para su eliminación no se quitan realmente del servidor hasta que el cliente POP envía la orden QUIT para terminar la sesión. En ese momento, el servidor POP pasa al Estado de actualización, fase en la que se eliminan los mensajes marcados y se limpian todos los recursos restantes de la sesión.

Es posible conectarse manualmente al servidor POP3 haciendo Telnet al puerto 110. Es muy útil cuando envían un mensaje con un fichero muy largo que no se quiere recibir.

- USER <nombre> Identificación de usuario (Solo se realiza una vez).
- PASS <password> Envía la clave del servidor.
- STAT Da el número de mensajes no borrados en el buzón y su longitud total.
- LIST Muestra todos los mensajes no borrados con su longitud.
- RETR <número> Solicita el envío del mensaje especificando el número (no se borra del buzón).
- TOP <número> <líneas> Muestra la cabecera y el número de líneas requerido del mensaje especificando el número.
- DELE <número> Borra el mensaje especificando el número.
- RSET Recupera los mensajes borrados (en la conexión actual).
- UIDL <número> Devuelve una cadena identificatoria del mensaje persistente a través de las sesiones. Si no se especifica <número> se devuelve una lista con los números de mensajes y su cadena identificatoria de los mensajes no borrados.
- QUIT Salir.

## Ventajas

La ventaja con otros protocolos es que entre servidor-cliente no se tienen que enviar tantas órdenes para la comunicación entre ellos. El protocolo POP también funciona adecuadamente si no se utiliza una conexión constante a Internet o a la red que contiene el servidor de correo.
