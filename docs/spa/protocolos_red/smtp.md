# SMTP

El **Protocolo Simple de Transferencia de Correo** (en inglés: **Simple Mail Transfer Protocol** o **SMTP**) es un protocolo de red utilizado para el intercambio de mensajes de correo electrónico entre computadoras u otros dispositivos (PDA, teléfonos móviles, impresoras, etc.). Se encuentra en la capa de aplicación del modelo OSI, la última de este modelo, en la que se dispone la interfaz entre las aplicaciones de comunicación y la red que transmite los mensajes. Fue definido inicialmente en agosto de 1982 por el RFC 821 (para la transferencia) y el RFC 822 (para el mensaje), dos estándares oficiales de Internet que fueron reemplazados respectivamente por el RFC 2821 y el RFC 2822, posteriormente destituidos por los estándares RFC 5321 y RFC 5322.

El funcionamiento de este protocolo se da en línea, de manera que opera en los servicios de correo electrónico. Sin embargo, posee algunas limitaciones en cuanto a la recepción de mensajes en el servidor de destino (cola de mensajes recibidos), por lo que se ejecuta normalmente en relación con otros, como POP3 o IMAP, otorgando a SMTP la tarea específica de enviar correos y delegando la de recibirlos a los protocolos antes mencionados.

## Historia

En 1982 se diseñó el primer sistema basado en SMTP para intercambiar correos electrónicos en ARPANET, definido en los *request for comments* RFC 821 y RFC 822. La primera de ellas define este protocolo y la segunda la forma del mensaje que este protocolo debía transportar.

La estructura de SMTP se basa en el modelo cliente-servidor, donde un cliente envía un mensaje a uno o varios servidores para recibir una respuesta. La comunicación entre el cliente y el servidor consiste enteramente en líneas de texto compuestas por caracteres Unicode, aunque originalmente estaba limitado a caracteres ASCII. El tamaño máximo permitido para estas líneas es de 1000 caracteres.

Las respuestas del servidor constan de un código numérico de tres dígitos, seguido de un texto explicativo. El número va dirigido a un procesado automático de la respuesta, mientras que el texto permite que un humano interprete la respuesta.

En el protocolo SMTP todas las órdenes, réplicas o datos son líneas de texto, son delimitadas por el carácter CRLF. Todas las réplicas tienen un código numérico al comienzo de la línea central.

## Modelo de procesamiento de correo

El correo electrónico es presentado por un cliente de correo (MUA, agente de usuario de correo) a un servidor de correo (MSA, agente de sumisión de correo) usando SMTP a través del puerto 587. Una gran parte de los proveedores de correo todavía permiten el envío a través del puerto 25. Desde allí, el MSA entrega el correo a su agente de transferencia postal mejor conocido como el MTA (Mail Transfer Agent, Agente de Transferencia de Correo). En algunas ocasiones, estos dos agentes son casos diferentes aunque hay que destacar que provienen del mismo software de donde fueron lanzados sólo que presentan opciones diferentes dentro de la misma máquina.

El procesamiento local que se presenta puede ser realizado en una sola máquina o partido entre varias aplicaciones; en este segundo caso, los procesos implicados pueden compartir archivos; aquí SMTP es usado para la transferencia de mensajes internamente, con cada uno de los hosts configurados para usar la siguiente aplicación como un anfitrión elegante. Para lograr la localización del servidor objetivo, el MTA divisorio tiene que usar el sistema de nombre de dominio (DNS) para lograr la búsqueda del registro interno de cambiado de correo conocido como registro MX para la esfera del recipiente (la parte de la dirección a la derecha). Es en ese instante cuando el registro de MX devuelto contiene el nombre del anfitrión objetivo.

Luego el MTA se une al servidor de cambio como un cliente SMTP. Una vez que MX acepta el mensaje entrante, este a su vez se lo da a un agente de entrega de correo (MDA) para luego ser llevado a la entrega de correo local. El MDA, además de entregar mensajes es también capaz de salvar mensajes en un buzón de formato, y la recepción de correo puede ser realizada usando muchas computadoras. Hay dos formas en que un MDA puede entregar mensajes: ya sea enviándolos directamente al almacenamiento, o expedirlos sobre una red usando SMTP. Una vez entregado al servidor de correo local, dicho correo es almacenado para la recuperación de la hornada. Su recuperación se logra por medio de las aplicaciones de usuario final, conocidas como clientes de correo electrónico, usando el Protocolo de Acceso de Mensaje de Internet (IMAP), este protocolo que facilita tanto el acceso para enviar, como el manejo de correo almacenado.

### Puertos

Los administradores de servidor pueden elegir si los clientes utilizan TCP puerto 25 (SMTP) o el puerto 587 (Presentación) para retransmitir el correo saliente a una inicial del servidor de correo. Las especificaciones y muchos servidores soportan ambos. Aunque algunos servidores soportan el puerto 465 para el legado SMTP seguro en violación de las especificaciones, es preferible utilizar los puertos estándar y comandos SMTP estándar de acuerdo con RFC 3207, si se debe utilizar una sesión segura entre el cliente y el servidor.

Algunos servidores están configurados para rechazar toda la retransmisión en el puerto 25, pero los usuarios válidos de autenticación en el puerto 587 pueden retransmitir correo a cualquier dirección válida. Algunos proveedores de servicios de Internet interceptan el puerto 25, volviendo a dirigir el tráfico a su propio servidor SMTP, independientemente de la dirección de destino. Esto significa que no es posible para sus usuarios acceder a un servidor SMTP fuera de la red del ISP a través del puerto 25.

Algunos servidores SMTP soportan el acceso autenticado en otro puerto que no sea 587 o 25 para permitir a los usuarios conectarse a ellos, incluso si el puerto 25 está bloqueado, pero 587 es el puerto estándar y ampliamente apoyada por los usuarios enviar correo nuevo. Microsoft Exchange Server 2013 SMTP puede escuchar en los puertos 25, 587, 465, 475, y 2525, en función de servidor y si los roles se combinan en un solo servidor. Los puertos 25 y 587 se utilizan para proporcionar la conectividad del cliente con el servicio de transporte en la parte delantera de la función de servidor de acceso de cliente (CAS). Los puertos 25, 465 y 475 son utilizados por el servicio de transporte de buzón de correo. Sin embargo, cuando la

 función de buzón se combina con la función de CAS en un único servidor, el puerto 2525 se utiliza por la función de buzón de SMTP desde el servicio de transporte de extremo delantero del CAS, CAS, mientras que continúa para utilizar el puerto 25. Puerto 465 es utilizado por el servicio de transporte de buzón de correo para recibir las conexiones de cliente proxy de la función CAS. Puerto 475 es utilizado por la función de buzón para comunicarse directamente con otras funciones de buzón, la transferencia de correo entre el servicio de envío de transporte de buzón de correo y el servicio de entrega de transporte buzón.

## Descripción del Protocolo

SMTP. Una transacción de SMTP se compone de tres secuencias de comando / respuesta (véase el ejemplo a continuación).

Ellos son:

- **MAIL FROM**: comando para establecer la dirección de retorno, también conocido como Return-Path, remitente o sobre. Esta es la dirección para mensajes de despedida.
- **RCPT TO**: comando, para establecer un destinatario de este mensaje. Este mandato puede emitirse varias veces, una para cada destinatario. Estas direcciones son también parte de la envolvente.
- **DATA**: para enviar el mensaje de texto. Este es el contenido del mensaje, en lugar de su envoltura. Se compone de una cabecera de mensaje y el cuerpo del mensaje separado por una línea en blanco. DATA es en realidad un grupo de comandos, y el servidor responde dos veces: una vez para el comando de datos adecuada, para reconocer que está listo para recibir el texto, y la segunda vez después de la secuencia final de los datos, para aceptar o rechazar todo el mensaje.

### Resumen simple del funcionamiento del protocolo SMTP

- Cuando un cliente establece una conexión con el servidor SMTP, espera a que este envíe un mensaje **“220 Service ready”** o **“421 Service non available”**.
- Se envía un **HELO** desde el cliente. Con ello el servidor se identifica. Esto puede usarse para comprobar si se conectó con el servidor SMTP correcto.
- El cliente comienza la transacción del correo con la orden **MAIL FROM**. Como argumento de esta orden se puede pasar la dirección de correo al que el servidor notificará cualquier fallo en el envío del correo (Por ejemplo, **MAIL FROM:<fuente@host0>**). Luego si el servidor comprueba que el origen es válido, el servidor responde **“250 OK”**.
- Ya le hemos dicho al servidor que queremos mandar un correo, ahora hay que comunicarle a quien. La orden para esto es **RCPT TO:<destino@host>**. Se pueden mandar tantas órdenes RCPT como destinatarios del correo queramos. Por cada destinatario, el servidor contestará **“250 OK”** o bien **“550 No such user here”**, si no encuentra al destinatario.
- Una vez enviados todos los RCPT, el cliente envía una orden **DATA** para indicar que a continuación se envían los contenidos del mensaje. El servidor responde **“354 Start mail input, end with <CRLF>.<CRLF>”** Esto indica al cliente como ha de notificar el fin del mensaje.
- Ahora el cliente envía el cuerpo del mensaje, línea a línea. Una vez finalizado, se termina con un <CRLF>.<CRLF> (la última línea será un punto), a lo que el servidor contestará **“250 OK”**, o un mensaje de error apropiado.
- Tras el envío, el cliente, si no tiene que enviar más correos, con la orden **QUIT** corta la conexión. También puede usar la orden **TURN**, con lo que el cliente pasa a ser el servidor, y el servidor se convierte en cliente. Finalmente, si tiene más mensajes que enviar, repite el proceso hasta completarlos.

Puede que el servidor SMTP soporte las extensiones definidas en el [RFC 1651], en este caso, la orden HELO puede ser sustituida por la orden EHLO, con lo que el servidor contestará con una lista de las extensiones admitidas. Si el servidor no soporta las extensiones, contestará con un mensaje "500 Syntax error, command unrecognized".

### Comandos

- HELO, para abrir una sesión con el servidor
- EHLO, para abrir una sesión, en el caso de que el servidor soporte extensiones definidas en el [RFC 1651]
- MAIL FROM, para indicar quien envía el mensaje
- RCPT TO, para indicar el destinatario del mensaje
- DATA, para indicar el comienzo del mensaje, este finalizará cuando haya una línea únicamente con un punto.
- QUIT, para cerrar la sesión
- RSET Aborta la transacción en curso y borra todos los registros.
- SEND Inicia una transacción en la cual el mensaje se entrega a una terminal.
- SOML El mensaje se entrega a un terminal o a un buzón.
- SAML El mensaje se entrega a un terminal y a un buzón.
- VRFY Solicita al servidor la verificación de todo un argumento.
- EXPN Solicita al servidor la confirmación del argumento.
- HELP Permite solicitar información sobre un comando.
- NOOP No decir nada, se emplea para mantener la sesión abierta
- TURN Solicita al servidor que intercambien los papeles.

De los tres dígitos del código numérico, el primero indica la categoría de la respuesta, estando definidas las siguientes categorías:

- 2XX, la operación solicitada mediante el comando anterior ha sido concluida con éxito
- 3XX, la orden ha sido aceptada, pero el servidor está pendiente de que el cliente le envíe nuevos datos para terminar la operación
- 4XX, para una respuesta de error, pero se espera a que se repita la instrucción
- 5XX, para indicar una condición de error permanente, por lo que no debe repetirse la orden

Una vez que el servidor recibe el mensaje finalizado con un punto puede almacenarlo si es para un destinatario que pertenece a su dominio, o bien retransmitirlo a otro servidor para que finalmente llegue a un servidor del dominio del receptor.

### **Ejemplo de una comunicación SMTP**

En primer lugar se ha de establecer una conexión entre el emisor (cliente) y el receptor (servidor). Esto puede hacerse automáticamente con un programa cliente de correo o mediante un cliente telnet.

En el siguiente ejemplo se muestra una conexión típica. Se nombra con la letra C al cliente y con S al servidor.

```bash
S: 220 Servidor SMTP
C: HELO miequipo.midominio.com
S: 250 Hello, please to meet you
C: MAIL FROM: <yo@midominio.com>
S: 250 Ok
C: RCPT TO: <destinatario@sudominio.com>
S: 250 Ok
C: DATA
S: 354 End data with <CR><LF>.<CR><LF>
C: Subject: Campo de asunto
C: From: yo@midominio.com
C: To: destinatario@sudominio.com
C:
C: Hola.
C: Esto es una prueba.
C: Hasta luego.
C:
C: .
C: <CR><LF>.<CR><LF>
S: 250 Ok: queued as 12345
C: quit
S: 221 Bye
```

### **Formato del mensaje**

Como se muestra en el ejemplo anterior, el mensaje es enviado por el cliente después de que este manda la orden DATA al servidor. El mensaje está compuesto por dos partes:

- **Cabecera**: en el ejemplo las tres primeras líneas del mensaje son la cabecera. En ellas se usan unas palabras clave para definir los campos del mensaje. Los más típicos son *subject* (asunto), *from* (emisor) y *to* (receptor). Estos dos últimos campos no hay que confundirlos con las órdenes MAIL FROM y RCPT TO, que pertenecen al protocolo, pero no al formato del mensaje.

- **Cuerpo del mensaje**: es el mensaje propiamente dicho. En el SMTP básico está compuesto únicamente por texto, y finalizado con una línea en la que el único carácter es un punto.

### **SMTP vs Recuperación de correo**

El protocolo de transferencia de correo simple (SMTP) solo se encarga de entregar el mensaje. En cuanto se reciben, los mensajes son enviados al servidor de correo de destino o al servidor de correo de siguiente salto. El correo se enruta en base al servidor de destino, no a las direcciones de los usuarios individuales. Otros protocolos como el protocolo de oficina de correos (POP) y el protocolo de acceso a mensaje de internet (IMAP) su estructura es para usuarios individuales, recuperación de mensajes, gestión de buzones de correo. SMTP usa una función, el procesamiento de colas de correo en un servidor remoto, permite que un servidor de correo de forma intermitente conectado a mandar mensajes desde un servidor remoto. El IMAP y el POP son protocolos inadecuados para la retransmisión de correo de máquinas de forma intermitente-conectados, sino que están diseñados para funcionar después de la entrega final.

### **Inicio remoto de mensaje en cola**

Es una característica de SMTP que permite a un host remoto para iniciar el procesamiento de la cola de correo en el servidor por lo que puede recibir mensajes destinados a ella mediante el envío del comando TURN. Esta característica se considera insegura pero usando el comando ETRN en la extensión RFC 1985 funciona de forma más segura.

### **Petición de Reenvío de Correo Bajo Demanda (ODMR)**

On-Demand Mail Relay (ODMR por sus siglas en Inglés) es una extensión de SMTP estandarizada en la RFC 2645 que permite que el correo electrónico sea transmitido al receptor después de que él ha sido aprobado. Usa la orden de SMTP ampliada ATRN, disponible para la direcciones de IP dinámicas. El cliente publica EHLO y órdenes de AUTH de servicios ODMR de correo, ODMR comienza a actuar como un cliente SMTP y comienza a enviar todos los mensajes dirigidos a un cliente usando el protocolo SMTP, al iniciar sesión el cortafuegos o el servidor pueden bloquear la sesión entrante debido a IP dinámicas. Sólo el servidor ODMR, el proveedor del servicio, debe escuchar las sesiones SMTP en una dirección de IP fija.

### **Internacionalización**

Muchos usuarios cuyo lenguaje base no es el latín han tenido dificultades con el requisito de correo electrónico en América. RFC 6531 fue creado para resolver ese problema, proporcionando características de internacionalización de SMTP, la extensión SMTPUTF8. RFC 6531 proporciona soporte para caracteres de varios bytes y no para ASCII en las direcciones de correo electrónico. El soporte del internacionalización actualmente es limitada pero hay un gran interés en la ampliación del RFC 6531. RFC en países como en China, que tiene una gran base de usuarios en América.

## Correo saliente con SMTP

Un cliente de correo electrónico tiene que saber la dirección IP de su servidor SMTP inicial y esto tiene que ser dado como parte de su configuración (usualmente dada como un nombre DNS). Este servidor enviará mensajes salientes en nombre del usuario.

### Restricción de acceso y salida al servidor de correo

En un ambiente de servidores, los administradores deben tomar medidas de control en donde los servidores estén disponibles para los clientes. Esto permite implementar seguridad frente a posibles amenazas. Anteriormente, la mayoría de los sistemas imponían restricciones de uso de acuerdo a la ubicación del cliente, sólo estaba permitido su uso por aquellos clientes cuya dirección IP es una de las controladas por los administradores del servidor. Los servidores SMTP modernos se caracterizan por ofrecer un sistema alternativo, el cual requiere de una autenticación mediante credenciales por parte de los clientes antes de permitir el acceso.

### Restringir el acceso por ubicación

Mediante este sistema, el servidor SMTP relativo al ISP no permitirá el acceso de los usuarios que están fuera de la red del ISP. Específicamente, el servidor solo puede permitir el acceso de aquellos usuarios cuya dirección IP fue proporcionada por el ISP, lo cual es equivalente a exigir que estén conectados a internet mediante el mismo ISP. Un usuario móvil suele estar a menudo en una red distinta a la normal de su ISP, y luego descubrir que el envío de correo electrónico falla porque la elección del servidor SMTP configurado ya no es accesible. Este sistema tiene distintas variaciones, por ejemplo, el servidor SMTP de la organización sólo puede proporcionar servicio a los usuarios en la misma red, esto se hace cumplir mediante cortafuegos para bloquear el acceso de los usuarios en general a través de Internet. O puede que el servicio realice comprobaciones de alcance en la dirección IP del cliente. Estos métodos son utilizados normalmente por empresas e instituciones, como las universidades que proporcionan un servidor SMTP para el correo saliente solo para su uso interno dentro de la organización. Sin embargo, la mayoría de estos organismos utilizan ahora métodos de autenticación de cliente, tal como se describe a continuación. Al restringir el acceso a determinadas direcciones IP, los administradores de servidores pueden reconocer fácilmente la dirección IP de cualquier agresor. Como esta representa una dirección significativa para ellos, los administradores pueden hacer frente a la máquina o usuario sospechoso. Cuando un usuario es móvil, y puede utilizar diferentes proveedores para conectarse a internet, este tipo de restricción de uso es costoso, y la alteración de la configuración perteneciente a la dirección de correo electrónico del servidor SMTP saliente resulta ser poco práctica. Es altamente deseable poder utilizar la información de configuración del cliente de correo electrónico que no necesita cambiar.

## Seguridad y *spam*

Una de las limitaciones del SMTP original es que no facilita métodos de autenticación a los emisores, así que se definió la extensión SMTP-AUTH en RFC 2554.

A pesar de esto, el spam es aún el mayor problema. No se cree que las extensiones sean una forma práctica para prevenirlo. Internet Mail 2000 es una de las propuestas para reemplazarlo.

Diferentes metodologías han aparecido para combatir el spam. Entre ellas destacan DKIM, Sender Policy Framework (SPF) y desde 2012 Domain-based Message Authentication, Reporting and Conformance (DMARC).
