# Memcached

- **Desarrollador(es)**: Brad Fitzpatrick, Comunidad
- **Lanzamiento**: 2003
- **Licencia**: BSD
- **Escrito en**: C
- **Página**: [https://memcached.org/](https://memcached.org/)
- **Documentación**: [https://memcached.org/documentation/](https://memcached.org/documentation/)
- **Repositorio**: [https://github.com/memcached/memcached](https://github.com/memcached/memcached)

**Memcached** (pronunciado de diversas maneras *mem-cash-dee* o *mem-cashed*) es un sistema de almacenamiento en caché de memoria distribuida de propósito general. A menudo se utiliza para acelerar sitios web dinámicos impulsados por bases de datos al almacenar en caché datos y objetos en la RAM para reducir la cantidad de veces que se debe leer una fuente de datos externa (como una base de datos o una API). Memcached es software gratuito y de código abierto, con licencia bajo la licencia Revised BSD. Memcached se ejecuta en sistemas operativos tipo Unix (Linux y macOS) y en Microsoft Windows. Depende de la biblioteca libevent.

Las API de Memcached proporcionan una tabla hash muy grande distribuida en múltiples máquinas. Cuando la tabla está llena, las inserciones posteriores provocan que los datos más antiguos se eliminen en orden de uso menos reciente (LRU). Las aplicaciones que utilizan Memcached suelen intercalar solicitudes y adiciones en la RAM antes de recurrir a un almacenamiento de respaldo más lento, como una base de datos.

Memcached no tiene un mecanismo interno para realizar un seguimiento de los fallos que puedan ocurrir. Sin embargo, algunos programas de terceros ofrecen esta funcionalidad.

Memcached fue desarrollado por primera vez por Brad Fitzpatrick para su sitio web LiveJournal el 22 de mayo de 2003. Originalmente fue escrito en Perl y luego fue reescrito en C por Anatoly Vorobey, quien trabajaba en LiveJournal en ese momento. Ahora Memcached es utilizado por muchos otros sistemas, incluidos YouTube, Reddit, Facebook, Pinterest, Twitter, Wikipedia y Method Studios. Google App Engine, Google Cloud Platform, Microsoft Azure, IBM Bluemix y Amazon Web Services también ofrecen un servicio de Memcached a través de una API.

## **Arquitectura de software**

El sistema utiliza una arquitectura cliente-servidor. Los servidores mantienen una matriz asociativa de clave-valor; los clientes llenan esta matriz y la consultan por clave. Las claves pueden tener hasta 250 bytes de longitud y los valores pueden tener un tamaño de hasta 1 megabyte.

Los clientes utilizan bibliotecas en el lado del cliente para contactar a los servidores que, por defecto, exponen su servicio en el puerto 11211. Se admiten tanto TCP como UDP. Cada cliente conoce a todos los servidores; los servidores no se comunican entre sí. Si un cliente desea establecer o leer el valor correspondiente a una clave determinada, la biblioteca del cliente primero calcula un hash de la clave para determinar qué servidor utilizar. Esto proporciona una forma sencilla de fragmentación y una arquitectura escalable de "shared-nothing" en los servidores. El servidor calcula un segundo hash de la clave para determinar dónde almacenar o leer el valor correspondiente. Los servidores mantienen los valores en la RAM; si un servidor se queda sin RAM, descarta los valores más antiguos. Por lo tanto, los clientes deben tratar a Memcached como una caché transitoria; no pueden asumir que los datos almacenados en Memcached sigan estando allí cuando los necesiten. Otras bases de datos, como MemcacheDB y Couchbase Server, ofrecen almacenamiento persistente manteniendo la compatibilidad con el protocolo Memcached.

Si todas las bibliotecas de cliente utilizan el mismo algoritmo de hash para determinar los servidores, entonces los clientes pueden leer los datos en caché de los demás.

Una implementación típica consta de varios servidores y muchos clientes. Sin embargo, es posible utilizar Memcached en una sola computadora, actuando simultáneamente como cliente y servidor. El tamaño de su tabla hash a menudo es muy grande y está limitado a la memoria disponible en todos los servidores del clúster de servidores en un centro de datos. En situaciones donde se requiere una publicación web de alto volumen y amplia audiencia, esto puede extenderse a muchos gigabytes. Memcached puede ser igualmente valioso en situaciones en las que el número de solicitudes de contenido es alto o el costo de generar un contenido específico es alto.

### **Seguridad**

La mayoría de las implementaciones de Memcached se encuentran en redes de confianza donde los clientes pueden conectarse libremente a cualquier servidor. Sin embargo, en ocasiones, Memcached se despliega en redes no confiables o cuando los administradores desean ejercer control sobre los clientes que se están conectando. Para este propósito, Memcached puede ser compilado con soporte de autenticación SASL (Simple Authentication and Security Layer) opcional. El soporte SASL requiere el protocolo binario.

Una presentación en BlackHat USA 2010 reveló que varios sitios web públicos importantes habían dejado Memcached abierto a la inspección, análisis, recuperación y modificación de datos.

Incluso dentro de una organización de confianza, el modelo de confianza plano de Memcached puede tener implicaciones de seguridad. Para lograr una simplicidad eficiente, todas las operaciones de Memcached se tratan de la misma manera. Los clientes con una necesidad válida de acceso a entradas de baja seguridad en la caché obtienen acceso a *todas* las entradas en la caché, incluso cuando estas son de mayor seguridad y ese cliente no tiene una justificación válida para acceder a ellas. Si la clave de la caché se puede predecir, adivinar o encontrar mediante una búsqueda exhaustiva, se puede recuperar su entrada en la caché.

En situaciones como la publicación web de alto volumen, se puede intentar aislar la configuración y lectura de datos. Una granja de servidores de contenido orientados hacia afuera tiene acceso de *lectura* a Memcached que contiene páginas publicadas o componentes de páginas, pero no tiene acceso de escritura. Cuando se publica contenido nuevo (y aún no está en Memcached), en su lugar se envía una solicitud a servidores de generación de contenido que no son accesibles públicamente para crear la unidad de contenido y agregarla a Memcached. Luego, el servidor de contenido vuelve a intentar recuperarla y servirla hacia afuera.

### Utilizado como vector de ataque DDoS

En febrero de 2018, CloudFlare informó que servidores Memcached mal configurados se utilizaron para lanzar ataques DDoS a gran escala. El protocolo Memcached a través de UDP tiene un gran factor de amplificación, de más de 51,000. Las víctimas de los ataques DDoS incluyen a GitHub, que se vio inundado con un pico de tráfico entrante de 1.35 Tbit/s.

Este problema se mitigó en la versión 1.5.6 de Memcached, que desactivó el protocolo UDP de forma predeterminada.

## Código de ejemplo

*Tenga en cuenta que todas las funciones descritas en esta página son solo seudocódigo. Las llamadas a Memcached y los lenguajes de programación pueden variar según la API utilizada.*

La conversión de consultas de creación de bases de datos u objetos para usar Memcached es simple. Típicamente, al usar consultas directas a la base de datos, el código de ejemplo sería el siguiente:

```
function obtener_foo(int id_usuario)
     datos = db_select("SELECT * FROM usuarios WHERE id_usuario = ?", id_usuario)
     return datos
```

Después de la conversión a Memcached, la misma llamada podría verse de la siguiente manera:

```
function obtener_foo(int id_usuario)
     /* primero intenta la caché */
     datos = memcached_fetch("fila_usuario:" + id_usuario)
     si no datos
         /* no encontrado: solicita a la base de datos */
         datos = db_select("SELECT * FROM usuarios WHERE id_usuario = ?", id_usuario)
         /* luego almacena en caché hasta la próxima obtención */
         memcached_add("fila_usuario:" + id_usuario, datos)
     fin

     return datos
```

El cliente primero verificaría si existe un valor de Memcached con la clave única "fila_usuario:id_usuario", donde id_usuario es algún número. Si el resultado no existe, seleccionaría de la base de datos como de costumbre y establecería la clave única utilizando la llamada a la función de la API de Memcached.

Sin embargo, si solo se modificara esta llamada a la API, el servidor terminaría obteniendo datos incorrectos después de cualquier acción de actualización de la base de datos: la "vista" de Memcached de los datos quedaría desactualizada. Por lo tanto, además de crear una llamada "add", también se necesitaría una llamada de actualización utilizando la función "set" de Memcached.

```
function actualizar_foo(int id_usuario, cadena cadena_actualizacion_bd)
     /* primero actualiza la base de datos */
     resultado = db_execute(cadena_actualizacion_bd)
     si resultado
         /* actualización de la base de datos exitosa: obtener datos para almacenar en la caché */
         datos = db_select("SELECT * FROM usuarios WHERE id_usuario = ?", id_usuario)
         /* la línea anterior también podría parecerse a data = createDataFromDBString(cadena_actualizacion_bd) */
         /* luego almacena en caché hasta la próxima obtención */
         memcached_set("fila_usuario:" + id_usuario, datos)
```

Esta llamada actualizaría los datos en caché actualmente para que coincidan con los nuevos datos en la base de datos, suponiendo que la consulta a la base de datos tenga éxito. Un enfoque alternativo sería invalidar la caché con la función de eliminación de Memcached, de modo que las recuperaciones posteriores resulten en un fallo de caché. Se debería tomar una acción similar cuando se eliminan registros de la base de datos, para mantener una caché correcta o incompleta.

Una estrategia alternativa de invalidación de caché es almacenar un número aleatorio en una entrada de caché acordada e incorporar este número en todas las claves que se utilizan para almacenar un tipo particular de entrada. Para invalidar todas esas entradas a la vez, cambie el número aleatorio. Las entradas existentes (que se almacenaron usando el número anterior) ya no se referenciarán y, eventualmente, expirarán o se reciclarán.

## Uso

- MySQL: admite directamente la API de Memcached a partir de la versión 5.6.
- Oracle Coherence: admite directamente la API de Memcached a partir de la versión 12.1.3.
- Infinispan: admite directamente Memcached.
