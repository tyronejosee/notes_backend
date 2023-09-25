# Websockets

**WebSocket** es un protocolo de comunicaciones de computadoras que proporciona canales de comunicación bidireccional sobre una única conexión TCP. El protocolo WebSocket fue estandarizado por la IETF como RFC 6455 en 2011. La especificación actual de la API que permite a las aplicaciones web utilizar este protocolo se conoce como *WebSockets*. Es un estándar en constante evolución mantenido por WHATWG y sucesor de *The WebSocket API* del W3C.

WebSocket es distinto de HTTP. Ambos protocolos se encuentran en el nivel 7 del modelo OSI y dependen de TCP en el nivel 4. Aunque son diferentes, RFC 6455 establece que WebSocket "está diseñado para funcionar en los puertos 443 y 80, así como para admitir proxies e intermediarios HTTP", lo que lo hace compatible con HTTP. Para lograr esta compatibilidad, el proceso de inicio de WebSocket utiliza la cabecera de actualización HTTP para cambiar del protocolo HTTP al protocolo WebSocket.

El protocolo WebSocket permite la interacción entre un navegador web (u otra aplicación cliente) y un servidor web con menor sobrecarga que las alternativas de comunicación semidúplex, como la encuesta HTTP, facilitando la transferencia de datos en tiempo real desde y hacia el servidor. Esto se logra proporcionando una forma estandarizada para que el servidor envíe contenido al cliente sin que este lo solicite primero, y permitiendo el intercambio de mensajes mientras se mantiene la conexión abierta. De esta manera, puede tener lugar una conversación bidireccional continua entre el cliente y el servidor. Normalmente, las comunicaciones se realizan a través del puerto TCP número 443 (o 80 en el caso de conexiones no seguras), lo que es beneficioso en entornos que bloquean las conexiones a Internet que no son web a través de un cortafuegos. Comunicaciones similares bidireccionales entre el navegador y el servidor se han logrado de manera no estandarizada mediante tecnologías temporales como Comet o Adobe Flash Player.

La mayoría de los navegadores admiten el protocolo, incluidos Google Chrome, Firefox, Microsoft Edge, Internet Explorer, Safari y Opera.

A diferencia de HTTP, WebSocket proporciona comunicación bidireccional y permite el flujo de mensajes sobre TCP. TCP por sí solo trabaja con flujos de bytes sin un concepto inherente de mensaje. Antes de WebSocket, la comunicación bidireccional en el puerto 80 se podía lograr mediante canales Comet, pero la implementación de Comet es complicada y, debido a la sobrecarga de la negociación TCP y las cabeceras HTTP, es ineficiente para mensajes pequeños. El protocolo WebSocket busca resolver estos problemas sin comprometer las suposiciones de seguridad de la web.

La especificación del protocolo WebSocket define "ws" (WebSocket) y "wss" (WebSocket Seguro) como dos nuevos esquemas de identificación de recursos uniformes (URI) que se utilizan para conexiones sin cifrar y cifradas, respectivamente. Además del nombre del esquema y el fragmento (es decir, "#" no es compatible), el resto de los componentes de URI se definen para utilizar la sintaxis genérica de URI.

Mediante las herramientas de desarrollo del navegador, los desarrolladores pueden inspeccionar el proceso de inicio de WebSocket y los tramas de WebSocket.

## Historia

WebSocket se mencionó por primera vez como TCPConnection en la especificación de HTML5, como un marcador de posición para una API de socket basada en TCP. En junio de 2008, una serie de discusiones lideradas por Michael Carter resultó en la primera versión del protocolo conocido como WebSocket. El nombre "WebSocket" fue acuñado por Ian Hickson y Michael Carter poco después, a través de la colaboración en la sala de chat IRC #whatwg, y posteriormente fue incluido en la especificación de HTML5 por Ian Hickson. En diciembre de 2009, Google Chrome 4 fue el primer navegador en enviar soporte completo para el estándar, con WebSocket habilitado de forma predeterminada. El desarrollo del protocolo WebSocket luego pasó del grupo W3C y WHATWG a la IETF en febrero de 2010 y fue escrito por Ian Hickson en dos revisiones. Después de que el protocolo se implementara y habilitara de forma predeterminada en varios navegadores, RFC 6455 se finalizó bajo la dirección de Ian Fette en diciembre de 2011. RFC 7692 introdujo la extensión de compresión para WebSocket utilizando el algoritmo DEFLATE por mensaje.

## Implementación en el navegador

Una versión segura del protocolo WebSocket se implementa en Firefox 6, Safari 6, Google Chrome 14, Opera 12.10 e Internet Explorer 10. Un informe detallado de pruebas de protocolo lista la conformidad de esos navegadores con aspectos específicos del protocolo. Una versión más antigua y menos segura del protocolo se implementó en Opera 11 y Safari 5, así como en la versión móvil de Safari en iOS 4.2. El navegador BlackBerry en OS7 implementa WebSockets. Debido a vulnerabilidades, se deshabilitó en Firefox 4 y 5, y en Opera 11.

## Implementación del servidor web

Nginx ha admitido WebSockets desde 2013, implementado en la versión 1.3.13, incluyendo su función como proxy inverso y equilibrador de carga de aplicaciones WebSocket. Apache HTTP Server ha admitido WebSockets desde julio de 2013, implementado en la versión 2.4.5. Internet Information Services agregó soporte para WebSockets en la versión 8, que se lanzó con Windows Server 2012. Lighttpd ha admitido WebSockets desde 2017, implementado en la versión 1.4.46. El módulo lighttpd mod_proxy puede actuar como proxy inverso y equilibrador de carga de aplicaciones WebSocket, mientras que el módulo lighttpd mod_wstunnel puede construir túneles WebSocket para transmitir datos arbitrarios, incluyendo en formato JSON, a una aplicación backend.

## Protocolo

### Saludo del protocolo

Para establecer una conexión WebSocket, el cliente envía una solicitud de saludo WebSocket, a la que el servidor responde con una respuesta de saludo WebSocket, como se muestra en el siguiente ejemplo.

Solicitud del cliente (similar a HTTP, cada línea termina con \r\n y debe haber una línea en blanco adicional al final):

```bash
GET /chat HTTP/1.1
Host: server.example.com
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: x3JJHMbDL1EzLkh9GBhXDw==
Sec-WebSocket-Protocol: chat, superchat
Sec-WebSocket-Version: 13
Origin: http://example.com

```

Respuesta del servidor:

```bash
HTTP/1.1 101 Switching Protocols
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Accept: HSmrc0sMlYUkAGmm5OPpG2HaGWk=
Sec-WebSocket-Protocol: chat
```

El saludo comienza con una solicitud/respuesta HTTP, lo que permite a los servidores manejar conexiones HTTP y conexiones WebSocket en el mismo puerto. Una vez que se establece la conexión, la comunicación cambia a un protocolo binario bidireccional que no cumple con el protocolo HTTP.

Además de las cabeceras de Upgrade, el cliente envía una cabecera Sec-WebSocket-Key que contiene bytes aleatorios codificados en base64, y el servidor responde con un hash de la clave en la cabecera Sec-WebSocket-Accept. Esto está destinado a evitar que un proxy de almacenamiento en caché reenvíe una conversación WebSocket previa y no proporciona autenticación, privacidad ni integridad. La función hash agrega la cadena fija 258EAFA5-E914-47DA-95CA-C5AB0DC85B11 (un UUID) al valor de la cabecera Sec-WebSocket-Key (que no se decodifica a partir de base64), aplica la función hash SHA-1 y codifica el resultado usando base64.

### Protocolo de enmarcado base

Una vez que se establece la conexión, el cliente y el servidor pueden enviar datos WebSocket o tramas de texto de un extremo a otro en modo bidireccional. Los datos están enmarcados de forma mínima, con una pequeña cabecera seguida de datos útiles. Las transmisiones WebSocket se describen como "mensajes", donde un solo mensaje opcionalmente se puede dividir en varias tramas de datos. Esto permite el envío de mensajes en los que los datos iniciales están disponibles pero no se conoce la longitud completa del mensaje (envía una trama de datos tras otra hasta llegar al final y se confirma con el bit FIN).

FIN: Indica el fragmento final en un mensaje. RSV debe ser 0 a menos que lo defina una extensión. Opcode: Código de operación. Mask: Establecido en 1 si los datos útiles están enmascarados. Longitud de datos útiles: La longitud de los datos útiles. Clave de enmascaramiento: Todas las tramas enviadas desde el cliente deben estar enmascaradas con esta clave. Este campo está ausente si el bit de enmascaramiento está configurado en 0. Datos útiles: Los datos útiles del fragmento.

Con extensiones del protocolo, esto también se puede utilizar para multiplexar varios flujos simultáneamente (por ejemplo, para evitar la monopolización del uso de un socket para una única carga útil grande).

### Enmascaramiento del cliente al servidor

Los datos útiles enviados desde el cliente deben estar enmascarados con la clave de enmascaramiento. La clave de enmascaramiento es un valor aleatorio de 4 bytes elegido por el cliente y debe ser impredecible. La imprevisibilidad de la clave de enmascaramiento es esencial para evitar que las aplicaciones maliciosas seleccionen los bytes que ya aparecen. El siguiente algoritmo se aplica para enmascarar los datos útiles:

```bash
j = i MOD 4
transformed-octet[i] = original-octet[i] XOR masking-key-octet[j]
```

## Consideraciones de seguridad

A diferencia de las solicitudes HTTP regulares entre dominios, las solicitudes WebSocket no están restringidas por la política del mismo origen. Por lo tanto, los servidores WebSocket deben validar la cabecera "Origin" con los orígenes esperados durante el establecimiento de la conexión para evitar ataques de secuestro de WebSocket entre sitios, que pueden ser posibles cuando la conexión está autenticada con cookies o autenticación HTTP. Es mejor utilizar tokens u otros mecanismos de protección similares para autenticar la conexión WebSocket cuando se transfieren datos sensibles (privados) a través de WebSocket. Un ejemplo en vivo de vulnerabilidad se vio en 2020 en forma de Cable Haunt.

## Traversal de proxy

Las implementaciones de clientes del protocolo WebSocket intentan detectar si el agente de usuario está configurado para utilizar un proxy al conectarse al host y puerto de destino, y si es así, utilizan el método HTTP CONNECT para establecer un túnel persistente.

Aunque el protocolo WebSocket en sí mismo no es consciente de los servidores proxy y los firewalls, presenta

 un saludo compatible con HTTP, lo que permite a los servidores HTTP compartir sus puertos HTTP y HTTPS predeterminados (80 y 443 respectivamente) con una puerta de enlace o servidor WebSocket. El protocolo WebSocket define un prefijo ws:// y wss:// para indicar una conexión WebSocket y una conexión WebSocket segura respectivamente. Ambos esquemas utilizan un mecanismo de actualización HTTP para cambiar al protocolo WebSocket. Algunos servidores proxy son transparentes y funcionan bien con WebSocket; otros evitarán que WebSocket funcione correctamente, lo que provocará que la conexión falle. En algunos casos, puede ser necesario configurar un servidor proxy adicional y es posible que se deba actualizar ciertos servidores proxy para admitir WebSocket.

Si el tráfico de WebSocket no cifrado fluye a través de un servidor proxy explícito o transparente sin soporte para WebSocket, es probable que la conexión falle.

Si se utiliza una conexión WebSocket cifrada, entonces el uso de Transport Layer Security (TLS) en la conexión WebSocket segura garantiza que se emita un comando HTTP CONNECT cuando el navegador esté configurado para utilizar un servidor proxy explícito. Esto establece un túnel que proporciona una comunicación TCP de extremo a extremo de bajo nivel a través del proxy HTTP entre el cliente WebSocket seguro y el servidor WebSocket. En el caso de servidores proxy transparentes, el navegador no es consciente del servidor proxy, por lo que no se envía ningún HTTP CONNECT. Sin embargo, dado que el tráfico de cable está cifrado, es posible que los servidores proxy transparentes intermedios simplemente permitan el tráfico cifrado, por lo que hay muchas más posibilidades de que la conexión WebSocket tenga éxito si se utiliza WebSocket Secure. El uso de la encriptación no es gratuito en términos de recursos, pero a menudo proporciona la tasa de éxito más alta, ya que viajaría a través de un túnel seguro.

Un borrador de mediados de 2010 (versión hixie-76) rompió la compatibilidad con proxies inversos y pasarelas al incluir ocho bytes de datos de clave después de las cabeceras, pero sin anunciar esos datos en una cabecera Content-Length: 8. Esto no fue reenviado por todos los intermediarios, lo que podría provocar un fallo del protocolo. Borradores más recientes (por ejemplo, hybi-09) ponen los datos de clave en una cabecera Sec-WebSocket-Key, lo que resuelve este problema.
