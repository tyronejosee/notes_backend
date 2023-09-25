# DNS

El **sistema de nombres de dominio**, abreviado como **DNS**, es un sistema de nomenclatura jerárquico descentralizado utilizado en redes IP, como Internet o redes privadas. Su función principal es asociar información variada con nombres de dominio asignados a dispositivos conectados a la red. El propósito principal del DNS es traducir nombres de dominio inteligibles para las personas en identificadores binarios asociados con equipos conectados a la red, permitiendo así la localización y dirección de estos equipos en todo el mundo.

## Funciones Principales

El DNS desempeña varias funciones esenciales:

- Resolución de Nombres: Traduce nombres de dominio legibles por humanos en direcciones IP asociadas a los dispositivos en la red. Por ejemplo, asocia "www.google.com" con la dirección IP 216.58.210.163.
- Asignación de Nombres a Direcciones IP: La función más conocida del DNS, permite a las personas utilizar nombres de dominio en lugar de direcciones IP al acceder a sitios web y servicios en línea.
- Localización de Servidores de Correo Electrónico: El DNS también se utiliza para encontrar los servidores de correo electrónico asociados con un dominio, facilitando la entrega de correos electrónicos.
  
## Historia

El DNS se desarrolló como una solución al problema de recordar fácilmente los nombres de todos los servidores conectados a Internet. Inicialmente, existía un archivo llamado "HOSTS" que contenía todos los nombres de dominio conocidos y estaba alojado en SRI International. Sin embargo, debido al crecimiento explosivo de la red, este sistema resultó impráctico.

En noviembre de 1983, Jon Postel publicó un plan en el RFC 881, seguido por RFC 882 y RFC 883. Estos documentos establecieron las bases del DNS moderno. Luego, en octubre de 1984, se emitió el RFC 920, que definió el DNS en su forma actual.

A lo largo de los años, el DNS ha evolucionado para incluir cambios dinámicos, extensiones de DNS (EDNS) y nombres de dominio internacionalizados, permitiendo caracteres de otros idiomas en los nombres de dominio.

## Componentes del DNS

El sistema DNS se compone de tres componentes principales:

1. **Clientes DNS**: Estos son programas cliente que se ejecutan en las computadoras de los usuarios y generan solicitudes DNS para resolver nombres a direcciones IP.
2. **Servidores DNS**: Son los encargados de responder a las solicitudes de los clientes. Los servidores recursivos tienen la capacidad de reenviar solicitudes a otros servidores si no tienen la información solicitada.
3. **Zonas de Autoridad**: Cada dominio o subdominio tiene una zona de autoridad, que es responsable de publicar información sobre ese dominio. Por ejemplo, subdominio.Wikipedia.ORG y subdominio.COM tendrían zonas de autoridad separadas.

## Estructura de un Nombre de Dominio

Un nombre de dominio consta de dos o más partes, separadas por puntos. La parte más a la derecha se llama "dominio de nivel superior" (TLD), como "com" o "org". Cada parte a la izquierda especifica un "subdominio", y puede haber hasta 127 niveles de subdominios. La parte más a la izquierda suele ser el nombre de la máquina, seguido de la ruta lógica al recurso requerido.

## Funcionamiento del DNS en el Mundo Real

En la práctica, los usuarios no interactúan directamente con los servidores DNS. Las aplicaciones cliente, como navegadores web o clientes de correo electrónico, realizan solicitudes DNS de forma transparente. Estas solicitudes se envían al servidor DNS local del sistema operativo, que verifica si la respuesta está en la memoria caché. Si no lo está, se envía la solicitud a uno o más servidores DNS.

La mayoría de los usuarios domésticos utilizan los servidores DNS proporcionados por su proveedor de servicios de Internet, aunque también pueden configurar servidores DNS públicos o privados. Los servidores DNS buscan la respuesta en su caché o realizan búsquedas recursivas hasta encontrarla. Una vez que obtienen la respuesta, la almacenan en la caché para futuros usos.

El protocolo DNS generalmente utiliza UDP para transportar solicitudes y respuestas, pero recurre a TCP en casos de respuestas largas o transferencias de zona entre servidores DNS.

En resumen, el sistema de nombres de dominio (DNS) es un componente fundamental de Internet que permite a las personas acceder a recursos en línea utilizando nombres de dominio en lugar de direcciones IP. Facilita la resolución de nombres y la asignación de nombres a direcciones IP, simplificando la navegación en Internet.

## Jerarquía DNS

El espacio de nombres de dominio tiene una estructura arborescente. Las hojas y los nodos del árbol se utilizan como etiquetas de los medios. Un nombre de dominio completo de un objeto consiste en la concatenación de todas las etiquetas de un camino. Las etiquetas son cadenas alfanuméricas (con "-" como único símbolo permitido), deben contar con al menos un carácter y un máximo de 63 caracteres de longitud, y deberá comenzar con una letra (y no con "-"). Las etiquetas individuales están separadas por puntos. Un nombre de dominio termina con un punto (aunque este último punto generalmente se omite, ya que es puramente formal). Un nombre de dominio correctamente formado (FQDN, por sus siglas en inglés), es por ejemplo este: www.ejemplo.com. (incluyendo el punto al final).

Un nombre de dominio debe incluir todos los puntos y tiene una longitud máxima de 255 caracteres.

Un nombre de dominio se escribe siempre de derecha a izquierda. El punto en el extremo derecho de un nombre de dominio separa la etiqueta raíz de la jerarquía. Este primer nivel es también conocido como dominio de nivel superior (TLD, por sus siglas en inglés).

Los objetos de un dominio DNS (por ejemplo, el nombre del equipo) se registran en un archivo de zona, ubicado en uno o más servidores de nombres.

## Tipos de servidores DNS

Estos son los tipos de servidores de acuerdo a su función:

**Primarios o maestros** guardan los datos de un espacio de nombres en sus ficheros.

**Secundarios o esclavos** obtienen los datos de los servidores primarios a través de una transferencia de zona.

**Locales o caché** funcionan con el mismo software, pero no contienen la base de datos para la resolución de nombres. Cuando se les realiza una consulta, estos a su vez consultan a los servidores DNS correspondientes, almacenando la respuesta en su base de datos para agilizar la repetición de estas peticiones en el futuro continuo o libre.

## Tipos de resolución de nombres de dominio

Un servidor DNS puede resolver un nombre de dominio de manera "recursiva" o "iterativa". En una consulta "iterativa", un cliente solicita a un servidor DNS que obtenga por sí mismo la respuesta completa (es decir, dado el dominio "mi.dominio.com", el cliente espera recibir la dirección IP correspondiente). Por otro lado, dada una consulta "recursiva", el servidor DNS no otorga una respuesta completa: para el caso de "mi.dominio.com", el primer servidor al que se le realiza la consulta (un servidor raíz), retorna las direcciones IP de los servidores de nivel superior (TDL) responsables del dominio ".com". De este modo, el cliente ahora debe realizar una nueva consulta a uno de estos servidores, el cual toma nota del sufijo ".dominio.com" y responde con la IP del servidor DNS correspondiente, por ejemplo "dns.dominio.com". Finalmente, el cliente envía una nueva consulta a "dns.dominio.com" para obtener la dirección IP de "mi.dominio.com".

En la práctica, la consulta de un host a un DNS local es recursiva, mientras que las consultas que realiza el DNS local son iterativas. Además, las consultas recursivas sólo se realizan en caso de que el servidor DNS local no posea los datos correspondientes en caché (o en caso de que estos hayan expirado). En resumen, el proceso de resolución normal se lleva a cabo de la siguiente manera:

1. El servidor DNS local recibe una consulta recursiva desde el resolver del host cliente.
2. El servidor DNS local verifica su caché para ver si ya tiene una respuesta almacenada para esa consulta. Si la encuentra, devuelve la respuesta al cliente.
3. Si el servidor DNS local no tiene la respuesta en su caché, realiza las consultas iterativas a los servidores correspondientes.
4. El servidor DNS local entrega la resolución al host que solicitó la información.
5. El resolver del host cliente entrega la respuesta a la aplicación correspondiente.

## Temas de Seguridad

Originalmente, las preocupaciones de seguridad no fueron consideraciones importantes para el diseño en el software DNS o de cualquier otro software para despliegue en la Internet temprana, ya que la red no estaba abierta a la participación del público general. Sin embargo, la expansión de Internet en el sector comercial en los 90s cambió los requisitos de las medidas de seguridad para proteger la integridad de los datos y la autenticación de los usuarios.

Muchos temas de vulnerabilidades fueron descubiertos y explotados por usuarios maliciosos. Uno de esos temas es el envenenamiento de caché DNS, en la cual los datos son distribuidos a los resolvedores de caché bajo el pretexto de ser un servidor de autoridad de origen, contaminando así el almacenamiento de datos con información potencialmente falsa y largos tiempos de expiración (time-to-live). Subsecuentemente, las solicitudes legítimas de las aplicaciones pueden ser redirigidas a equipos de red operados con contenidos maliciosos.

Las respuestas DNS tradicionalmente no estaban firmadas criptográficamente, permitiendo muchas posibilidades de ataque; las extensiones de seguridad del DNS (DNSSEC) modifican el DNS para agregar la posibilidad de tener respuestas firmadas criptográficamente. DNSCurve ha sido propuesto como una alternativa a DNSSEC. Otras extensiones, como TSIG, agregan soporte para autenticación criptográfica entre pares de confianza y se usan comúnmente para autorizar transferencias de zona u operaciones dinámicas de actualización.

Algunos nombres de dominio pueden ser usados para conseguir efectos de engaño. Por ejemplo, paypal.com y paypa1.com son nombres diferentes, pero puede que los usuarios no puedan distinguir la diferencia dependiendo del tipo de letra que estén usando. En muchos tipos de letras la letra "l" y el numeral "1" se ven muy similares o hasta idénticos. Este problema es grave en sistemas que permiten nombres de dominio internacionalizados, ya que muchos caracteres en ISO 10646 pueden aparecer idénticos en las pantallas típicas de computador. Esta vulnerabilidad se explota ocasionalmente en phishing.

Técnicas como el FDNS inverso con confirmación adelantada pueden también usarse para validar los resultados de DNS.

## Registros de recursos

El Sistema de nombres de dominio especifica una base de datos de elementos de información para recursos de red. Los tipos de elementos de información se clasifican y organizan con una lista de tipos de registros de DNS: los registros de recursos (RR). Cada registro tiene un tipo (nombre

 y número), un tiempo de expiración (tiempo de vida), una clase, y datos específicos del tipo. Los registros de recursos del mismo tipo se describen como un conjunto de registros de recursos (RRset) y no tienen un orden específico. Los resolvedores de DNS devuelven el conjunto completo tras la consulta, pero los servidores pueden implementar un ordenamiento round-robin para lograr un balance de carga. Por el contrario, las Extensiones de Seguridad del Sistema de Nombres de Dominio (DNSSEC) funcionan en el conjunto completo de registros de recursos en orden canónico.

Cuando se envían a través de una red de Protocolo de Internet, todos los registros usan el formato común especificado en RFC 1035:

| Campo | Descripción | Longitud (octetos) |
| --- | --- | --- |
| NAME | Nombre del nodo al que pertenece el registro | Variable |
| TYPE | Tipo de RR en forma numérica (por ejemplo, 15 para MX RR) | 2 |
| CLASS | Código de clase | 2 |
| TTL (Tiempo de vida en informática) | Cantidad de segundos en que el RR es válido (el máximo es 2^31−1, que es aproximadamente 68 años) | 4 |
| RDLENGTH | Longitud del campo RDATA (especificado en octetos) | 2 |
| RDATA | Datos adicionales específicos de RR | Variable, según RDLENGTH |

NAME es el nombre de dominio completo del nodo en el árbol. Durante la conexión, el nombre puede acortarse utilizando la compresión de etiquetas donde los extremos de los nombres de dominio mencionados anteriormente en el paquete pueden sustituirse por el final del nombre de dominio actual. Un @ independiente se usa para denotar el origen actual.

TYPE es el tipo de registro. Indica el formato de los datos y da una idea del uso previsto. Por ejemplo, el registro A se usa para traducir de un nombre de dominio a una dirección IPv4, el registro NS enumera qué servidores de nombres pueden responder búsquedas en una zona DNS, y el registro MX especifica el servidor de correo utilizado para manejar el correo de un dominio especificado en una dirección de correo electrónico.

RDATA son datos de tipo específico de relevancia, como la dirección IP para registros de dirección, o la prioridad y el nombre de host para registros MX. Los tipos de registros conocidos pueden usar la compresión de etiquetas en el campo RDATA, salvo los tipos de registros "unknown" (RFC 3597).

CLASS es la clase del registro establecido en IN (Internet) para registros DNS comunes que involucran nombres de host, servidores o direcciones IP. Además, existen las clases Chaos (CH) y Hesiod (HS). Cada clase es un espacio de nombres independiente con delegaciones potencialmente diferentes de zonas DNS.

Además de los registros de recursos definidos en un archivo de zonas, el sistema de nombres de dominio también define varios tipos de solicitud que se usan sólo en la comunicación con otros nodos DNS (en la conexión), como cuando se realizan transferencias de zona (AXFR / IXFR) o para EDNS (OPTAR).

## Registros DNS comodín

El sistema de nombres de dominio soporta registros DNS de tipo comodín, que especifican nombres que comienzan con la etiqueta de asterisco "*", por ejemplo, *.ejemplo. Los registros de DNS pertenecientes a nombres de dominio comodín especifican reglas para generar registros de recursos dentro de una sola zona de DNS mediante la sustitución de etiquetas con componentes coincidentes del nombre, incluyendo cualquier descendientes especificado.

```bash
x.example.       MX   10 a.x.example.
*.x.example.     MX   10 a.x.example.
*.a.x.example.   MX   10 a.x.example.
a.x.example.     MX   10 a.x.example.
a.x.example.     AAAA 2001:db8::1
```

## Tipos de registros DNS

Los tipos de registros más utilizados son:

| Tipo de registro | Significado |
| --- | --- |
| A | Dirección (address). Este registro se usa para traducir nombres de servidores de alojamiento a direcciones IPv4 |
| AAAA | Dirección (address). Este registro se usa en IPv6 para traducir nombres de hosts a Dirección IPv6 |
| CNAME | Nombre canónico (canonical Name). Se usa para crear nombres de servidores de alojamiento adicionales, o alias, para los servidores de alojamiento de un dominio. Es usado cuando se están corriendo múltiples servicios (como FTP y servidor web) en un servidor con una sola Dirección IP. Cada servicio tiene su propia entrada de DNS (como "ftp.ejemplo.com." y "www.ejemplo.com."). Esto también es usado cuando corres múltiples servidores HTTP, con diferentes nombres, sobre el mismo host. Se escribe primero el alias y luego el nombre real. Ej. "Ejemplo1 IN CNAME ejemplo2" |
| NS | Servidor de nombres (name server). Define la asociación que existe entre un nombre de dominio y los servidores de nombres que almacenan la información de dicho dominio. Cada dominio se puede asociar a una cantidad cualquiera de servidores de nombres |
| MX (registro) | Intercambio de correo (mail exchange). Asocia un nombre de dominio a una lista de servidores de intercambio de correo para ese dominio. Tiene un balanceo de carga y prioridad para el uso de uno o más servicios de correo |
| PTR | Indicador (pointer). También conocido como "registro inverso", funciona a la inversa del registro A, traduciendo IPs en nombres de dominio. Se usa en el archivo de configuración de la Búsqueda DNS inversa |
| SOA | Autoridad de la zona (start of authority). Proporciona información sobre el servidor DNS primario de la zona |
| SRV | Service record (SRV record) |
| ANY | Toda la información de todos los tipos que exista. (No es un tipo de registro, sino un tipo de consulta) |

## Registro de pegamento

Un registro "A" y "AAAA" se dice que es un "registro de pegamento" (en inglés: glue record) cuando define un dominio apuntado por un registro NS. Un registro de pegamento asocia una dirección IP "pegada" al subdominio que se quiere usar como servidor de DNS.
