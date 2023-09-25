# MQTT

**MQTT** (originalmente un **acrónimo** de **MQ Telemetry Transport**) es un protocolo de red ligero de tipo **publicación-suscripción** para redes de **máquina a máquina** (M2M). Está diseñado para conexiones con ubicaciones remotas que tienen dispositivos con limitaciones de recursos o ancho de banda de red limitado, como en el **Internet de las cosas** (IoT). Debe ejecutarse sobre un protocolo de transporte que proporcione conexiones bidireccionales, ordenadas y sin pérdidas, típicamente **TCP/IP**, pero posiblemente también **QUIC**. Es un estándar abierto de **OASIS** y una recomendación de la **ISO/IEC 20922**.

## Historia

Andy Stanford-Clark (IBM) y Arlen Nipper (entonces trabajando para Eurotech, Inc.) fueron los autores de la primera versión del protocolo en 1999. Se utilizó para monitorear oleoductos dentro del sistema de control industrial **SCADA**. El objetivo era tener un protocolo eficiente en términos de ancho de banda, liviano y que consumiera poca energía de la batería, ya que los dispositivos estaban conectados a través de enlaces satelitales que en ese momento eran extremadamente costosos.

Históricamente, la "MQ" en "MQTT" provenía de la línea de productos **IBM MQ** (entonces 'MQSeries'), donde significaba "Message Queue". Sin embargo, el protocolo proporciona mensajería de tipo publicación y suscripción (sin colas, a pesar del nombre). En la especificación abierta por IBM como versión 3.1, el protocolo se denominó "MQ Telemetry Transport". Versiones posteriores lanzadas por OASIS se refieren estrictamente al protocolo como "MQTT", aunque el comité técnico en sí se llama "OASIS Message Queuing Telemetry Transport Technical Committee". Desde 2013, "MQTT" no significa nada.

En 2013, IBM presentó MQTT v3.1 al organismo de especificación de **OASIS** con un estatuto que garantizaba que solo se podían aceptar cambios menores en la especificación. Después de asumir el mantenimiento del estándar de IBM, OASIS lanzó la versión 3.1.1 el 29 de octubre de 2014. Se lanzó una actualización más sustancial a MQTT versión 5, que agregó varias características nuevas, el 7 de marzo de 2019.

MQTT-SN (MQTT para redes de sensores) es una variante del protocolo principal dirigida a dispositivos integrados alimentados por batería en redes que no utilizan TCP/IP, como **Zigbee**.

## Descripción general

El protocolo MQTT define dos tipos de entidades de red: un **broker de mensajes** y varios clientes. Un broker MQTT es un servidor que recibe todos los mensajes de los clientes y luego enruta los mensajes a los clientes de destino apropiados. Un cliente MQTT puede ser cualquier dispositivo (desde un microcontrolador hasta un servidor completo) que ejecute una biblioteca MQTT y se conecte a un broker MQTT a través de una red.

La información se organiza en una jerarquía de temas. Cuando un editor tiene un nuevo elemento de datos para distribuir, envía un mensaje de control con los datos al broker conectado. El broker luego distribuye la información a los clientes que se han suscrito a ese tema. El editor no necesita tener datos sobre el número o la ubicación de los suscriptores, y los suscriptores, a su vez, no necesitan estar configurados con datos sobre los editores.

Si un broker recibe un mensaje en un tema para el cual no hay suscriptores actuales, el broker descarta el mensaje a menos que el editor del mensaje haya designado el mensaje como un mensaje retenido. Un mensaje retenido es un mensaje MQTT normal con el indicador de retención activado. El broker almacena el último mensaje retenido y la calidad de servicio (QoS) correspondiente para el tema seleccionado. Cada cliente que se suscribe a un patrón de tema que coincide con el tema del mensaje retenido recibe el mensaje retenido inmediatamente después de suscribirse. El broker almacena solo un mensaje retenido por tema. Esto permite que los nuevos suscriptores en un tema reciban el valor más actual en lugar de esperar la próxima actualización de un editor.

Cuando un cliente editor se conecta por primera vez al broker, puede configurar un mensaje predeterminado para enviar a los suscriptores si el broker detecta que el cliente editor se desconectó inesperadamente del broker.

Los clientes solo interactúan con un broker, pero un sistema puede contener varios servidores de broker que intercambian datos según los temas de suscriptores actuales.

Un mensaje de control MQTT mínimo puede tener tan solo dos bytes de datos. Un mensaje de control puede transportar casi 256 megabytes de datos si es necesario. Hay catorce tipos de mensajes definidos que se utilizan para conectar y desconectar un cliente de un broker, publicar datos, confirmar la recepción de datos y supervisar la conexión entre el cliente y el servidor.

MQTT se basa en el protocolo TCP para la transmisión de datos. Existe una variante, MQTT-SN, que se utiliza en otros medios de transporte como UDP o Bluetooth.

MQTT envía credenciales de conexión en formato de texto sin formato y no incluye medidas de seguridad ni autenticación. Esto se puede proporcionar utilizando **TLS** para cifrar y proteger la información transferida contra interceptación, modificación o falsificación.

El puerto MQTT sin cifrar por defecto es el 1883. El puerto cifrado es el 8883.

## Broker MQTT

El broker MQTT es un software que se ejecuta en una computadora (en las instalaciones o en la nube) y puede ser desarrollado por el usuario o alojado por un tercero. Está disponible en implementaciones de código abierto y propietarias.

El broker actúa como una oficina de correos. Los clientes MQTT no utilizan una dirección de conexión directa del destinatario previsto, sino que utilizan la línea de asunto llamada "Tema". Cualquiera que se suscriba recibe una copia de todos los mensajes para ese tema. Varios clientes pueden suscribirse a un tema desde un solo broker (capacidad de uno a muchos),

 y un solo cliente puede registrar suscripciones a temas con varios brokers (capacidad de muchos a uno).

Cada cliente puede tanto producir como recibir datos, publicando y suscribiéndose, es decir, los dispositivos pueden publicar datos de sensores y aún así recibir información de configuración o comandos de control (MQTT es un protocolo de comunicación bidireccional). Un cliente no puede transmitir los mismos datos a una serie de temas, sino que debe publicar múltiples mensajes en el broker, cada uno con un único tema específico.

Con la arquitectura del broker MQTT, los dispositivos clientes y la aplicación del servidor quedan desacoplados. De esta manera, los clientes desconocen la información de los demás. MQTT, si está configurado para hacerlo, puede utilizar el cifrado TLS con certificado, conexiones protegidas por nombre de usuario y contraseña. Opcionalmente, la conexión puede requerir una certificación en forma de un archivo de certificado que un cliente proporciona y que debe coincidir con la copia del servidor.

En caso de falla, el software del broker y los clientes pueden cambiar automáticamente a un broker de respaldo automático/redundante. Los brokers de respaldo también se pueden configurar para compartir la carga de los clientes entre múltiples servidores en el sitio, en la nube o una combinación de ambos.

El broker puede admitir tanto MQTT estándar como MQTT para especificaciones compatibles como Sparkplug. Esto se puede hacer en el mismo servidor, al mismo tiempo y con los mismos niveles de seguridad.

El broker realiza un seguimiento de toda la información de la sesión a medida que el dispositivo se conecta y desconecta, en una función llamada "sesiones persistentes". En este estado, el broker almacena la información de conexión para cada cliente, los temas a los que se ha suscrito cada cliente y cualquier mensaje para un tema con un QoS de 1 o 2. Esto permite que el broker mantenga un registro del estado de la sesión de cada cliente incluso cuando se desconecta y reconecta.

Las principales ventajas del broker MQTT son:

1. Elimina conexiones de clientes vulnerables e inseguras, si está configurado para hacerlo.
2. Puede escalar fácilmente desde un solo dispositivo hasta miles.
3. Gestiona y realiza un seguimiento de todos los estados de conexión de los clientes, incluidas las credenciales de seguridad y los certificados, si está configurado para hacerlo.
4. Reduce la tensión en la red sin comprometer la seguridad, si está configurado para hacerlo (red celular o satelital).

## Tipos de mensajes

### **Conectar**

Espera a que se establezca una conexión con el servidor y crea un enlace entre los nodos.

### **Desconectar**

Espera a que el cliente MQTT finalice cualquier trabajo que deba hacer y que la sesión TCP/IP se desconecte.

### **Publicar**

Vuelve de inmediato al hilo de la aplicación después de pasar la solicitud al cliente MQTT.

## Versión 5.0

En 2019, OASIS lanzó oficialmente el estándar MQTT 5.0. La versión 5.0 incluye las siguientes características principales:

- Códigos de razón: las confirmaciones ahora admiten códigos de retorno, que proporcionan una razón para un fallo.
- Suscripciones compartidas: permiten equilibrar la carga entre los clientes y, por lo tanto, reducen el riesgo de problemas de carga.
- Expiración de mensajes: los mensajes pueden incluir una fecha de vencimiento y se eliminan si no se entregan en este período de tiempo.
- Alias de tema: el nombre de un tema se puede reemplazar por un solo número.

MQTT 5.0 también admite conexiones MQTT sobre el protocolo de transporte **QUIC**. MQTT sobre QUIC ofrece un mejor rendimiento al reducir el número de intercambios durante el proceso de conexión, reducir la latencia general y ofrecer un mejor manejo de la congestión de red y los cambios.

## Calidad de servicio

Cada conexión con el broker puede especificar una medida de calidad de servicio (QoS). Estas se clasifican en orden creciente de sobrecarga:

- Como máximo una vez: el mensaje se envía solo una vez y el cliente y el broker no toman medidas adicionales para confirmar la entrega (envío y olvido).
- Al menos una vez: el mensaje se reintenta varias veces por el remitente hasta que se reciba una confirmación (entrega confirmada).
- Exactamente una vez: el remitente y el receptor realizan un proceso de confirmación de dos niveles para asegurar que solo se reciba una copia del mensaje (entrega asegurada).

Este campo no afecta el manejo de las transmisiones de datos TCP subyacentes; solo se utiliza entre los remitentes y receptores MQTT.

## Seguridad

La seguridad del protocolo MQTT se vio comprometida en 2020 por investigadores italianos que ejecutaron ataques de **Slow DoS** en dicho protocolo.
