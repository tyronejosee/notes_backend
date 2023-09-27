# Nombre de Dominio

Los nombres de dominio son una parte clave de la infraestructura de Internet. Proporcionan una dirección legible por humanos para cualquier servidor web disponible en Internet.

Cualquier computadora conectada a Internet puede ser alcanzada a través de una dirección IP pública, ya sea una dirección IPv4 (por ejemplo, `192.0.2.172`) o una dirección IPv6 (por ejemplo, `2001:db8:8b73:0000:0000:8a2e:0370:1337`).

Las computadoras pueden manejar fácilmente estas direcciones, pero a las personas les resulta difícil descubrir quién está ejecutando el servidor o qué servicio ofrece el sitio web. Las direcciones IP son difíciles de recordar y pueden cambiar con el tiempo.

Para resolver todos esos problemas, utilizamos direcciones legibles por humanos llamadas nombres de dominio.

## Estructura de los nombres de dominio

Un nombre de dominio tiene una estructura simple compuesta por varias partes (puede ser una parte única, dos, tres...), separadas por puntos y **leídas de derecha a izquierda**:

Cada una de esas partes proporciona información específica sobre el nombre de dominio en su conjunto.

[TLD](https://developer.mozilla.org/es/docs/Glossary/TLD) (Dominio de nivel superior). Los TLDs le dicen a los usuarios el propósito general del servicio detrás del nombre de dominio. Los TLD más genéricos (`.com`, `.org`, `.net`) no requieren que los servicios web cumplan con ningún criterio en particular, pero algunos TLD imponen políticas más estrictas para que quede más claro cuál es su propósito. Por ejemplo:
• Los TLD locales como `.us`, `.fr`, o `.se` pueden requerir que el servicio se ofrezca en un idioma específico o que esté alojado en un país determinado; se supone que indican un recurso en un idioma o país específico.
• Los TLD que contienen `.gov` solo pueden ser utilizados por departamentos gubernamentales.
• El TLD `.edu` solo se usa para instituciones educativas y académicas.
Los TLD pueden contener caracteres especiales además de los latinos. La longitud máxima de un TLD es de 63 caracteres, aunque la mayoría tiene alrededor de 2 a 3.
La lista completa de TLDs es [mantenida por ICANN](https://www.icann.org/resources/pages/tlds-2012-02-25-en).Etiqueta (o componente)Las etiquetas son lo que sigue al TLD. Una etiqueta es una secuencia de caracteres insensible a mayúsculas y minúsculas de uno a sesenta y tres caracteres de longitud, que contiene solo las letras `A` a `Z`, los dígitos del `0` al `9`, y el carácter '-' (que no puede ser el primer ni el último carácter en la etiqueta). `a`, `97` y `hello-strange-person-16-how-are-you` son ejemplos válidos de etiquetas.
La etiqueta que se encuentra justo antes del TLD también se llama *Dominio de Nivel Secundario* (SLD).
Un nombre de dominio puede tener muchas etiquetas (o componentes). No es obligatorio ni necesario tener 3 etiquetas para formar un nombre de dominio. Por ejemplo, [www.inf.ed.ac.uk](http://www.inf.ed.ac.uk/) es un nombre de dominio válido. Para cualquier dominio que controles (por ejemplo, [mozilla.org](https://www.mozilla.org/es-ES/)), puedes crear "subdominios" con contenido diferente ubicado en cada uno, como [developer.mozilla.org](https://developer.mozilla.org/), [iot.mozilla.org](https://iot.mozilla.org/), o [bugzilla.mozilla.org](https://bugzilla.mozilla.org/).

## Compra de un nombre de dominio

### ¿Quién es dueño de un nombre de dominio?

No puedes "comprar un nombre de dominio". Esto se hace para que los nombres de dominio no utilizados eventualmente estén disponibles para que alguien más los use. Si se compraran todos los nombres de dominio, la web se llenaría rápidamente de nombres de dominio no utilizados que estarían bloqueados y no podrían ser utilizados por nadie.

En cambio, pagas por el derecho de usar un nombre de dominio durante uno o más años. Puedes renovar tu derecho, y tu renovación tiene prioridad sobre las solicitudes de otras personas. Pero nunca eres dueño del nombre de dominio.

Las empresas llamadas registradores utilizan registros de nombres de dominio para llevar un registro de la información técnica y administrativa que te conecta con tu nombre de dominio.

**Nota:** Para algunos nombres de dominio, es posible que no sea un registrador el encargado de llevar un registro. Por ejemplo, cada nombre de dominio bajo `.fire` es gestionado por Amazon.

### Encontrar un nombre de dominio disponible

Para averiguar si un nombre de dominio dado está disponible,

- Ve al sitio web de un registrador de nombres de dominio. La mayoría de ellos ofrecen un servicio "whois" que te dice si un nombre de dominio está disponible.
- Alternativamente, si utilizas un sistema con una línea de comandos incorporada, escribe un comando `whois` en él, como se muestra aquí para `mozilla.org`:

Esto mostrará lo siguiente:

```bash
whois mozilla.org

```

```
Nombre de dominio: MOZILLA.ORG
ID de dominio: D1409563-LROR
Fecha de creación: 1998-01-24T05:00:00Z
Fecha de actualización: 2013-12-08T01:16:57Z
Fecha de vencimiento del registro: 2015-01-23T05:00:00Z
Registrador patrocinador: MarkMonitor Inc. (R37-LROR)
ID de la entidad patrocinadora del registrador IANA: 292
Servidor WHOIS:
URL de referencia:
Estado del dominio: prohibido eliminar al cliente
Estado del dominio: prohibido transferir al cliente
Estado del dominio: prohibido actualizar al cliente
ID del registrante: mmr-33684
Nombre del registrante: DNS Admin
Organización del registrante: Fundación Mozilla
Calle del registrante: 650 Castro St Ste 300
Ciudad del registrante: Mountain View
Estado/Provincia del registrante: CA
Código postal del registrante: 94041
País del registrante: EE. UU.
Teléfono del registrante: +1.6509030800

```

Como puedes ver, no puedo registrar `mozilla.org` porque la Fundación Mozilla ya lo ha registrado.

Por otro lado, veamos si podría registrar `afunkydomainname.org`:

BASHCopiar al portapapeles

```bash
whois afunkydomainname.org

```

Esto mostrará lo siguiente (en el momento de escribir esto):

```
NO ENCONTRADO

```

Como puedes ver, el dominio no existe en la base de datos de `whois`, por lo que podríamos solicitar registrarlo. ¡Bueno saberlo!

### Obtener un nombre de dominio

El proceso es bastante sencillo:

1. Ve al sitio web de un registrador.
2. Por lo general, hay un llamado destacado "Obtener un nombre de dominio". Haz clic en él.
3. Completa el formulario con todos los detalles requeridos. Asegúrate, especialmente, de no haber escrito incorrectamente el nombre de dominio deseado. ¡Una vez que lo hayas pagado, será demasiado tarde!
4. El registrador te informará cuando el nombre de dominio esté registrado correctamente. En unas pocas horas, todos los servidores DNS habrán recibido tu información de DNS.

**Nota:** En este proceso, el registrador te pedirá tu dirección del mundo real. Asegúrate de completarla correctamente, ya que en algunos países los registradores pueden verse obligados a cerrar el dominio si no pueden proporcionar una dirección válida.

### Actualización de DNS

Las bases de datos de DNS se almacenan en cada servidor DNS en todo el mundo, y todos estos servidores se refieren a algunos servidores especiales llamados "servidores de nombres autorizados" o "servidores DNS de nivel superior"; estos son como los servidores principales que administran el sistema.

Cada vez que tu registrador crea o actualiza cualquier información para un dominio determinado, la información debe actualizarse en todas las bases de datos de DNS. Cada servidor DNS que conoce un dominio determinado almacena la información durante algún tiempo antes de que se invalide automáticamente y luego se actualice (el servidor DNS consulta a un servidor autorizado y obtiene la información actualizada de él). Por lo tanto, lleva algo de tiempo para que los servidores DNS que conocen este nombre de dominio obtengan la información actualizada.

## ¿Cómo funciona una solicitud de DNS?

Como ya hemos visto, cuando deseas mostrar una página web en tu navegador, es más fácil escribir un nombre de dominio que una dirección IP. Veamos el proceso:

1. Escribe `mozilla.org` en la barra de ubicación de tu navegador.
2. Tu navegador pregunta a tu computadora si ya reconoce la dirección IP identificada por este nombre de dominio (usando una caché DNS local). Si lo hace, el nombre se traduce a la dirección IP y el navegador negocia el contenido con el servidor web. Fin de la historia.
3. Si tu computadora no sabe qué IP está detrás del nombre `mozilla.org`, consulta a un servidor DNS, cuya función es precisamente decirle a tu computadora qué dirección IP coincide con cada nombre de dominio registrado.
4. Ahora que la computadora conoce la dirección IP solicitada, tu navegador puede negociar el contenido con el servidor web.
