# Redis

- **Desarrollador(es)**: Salvatore Sanfilippo
- **Lanzamiento**: 2009
- **Licencia**: Licencia BSD
- **Escrito en**: C
- **Página**: [https://redis.io/](https://redis.io/)
- **Documentación**: [https://redis.io/documentation](https://redis.io/documentation)
- **Repositorio**: [https://github.com/antirez/redis](https://github.com/antirez/redis)

**Redis** (pronunciado como "Redis") es un almacén en memoria de código abierto utilizado como base de datos clave-valor en memoria, caché y broker de mensajes, con durabilidad opcional. Debido a que almacena todos los datos en la memoria y su diseño, Redis ofrece una baja latencia en lecturas y escrituras, lo que lo hace especialmente adecuado para casos de uso que requieren una caché. Redis es la base de datos NoSQL más popular y una de las bases de datos más populares en general. Empresas como Twitter, Airbnb, Tinder, Yahoo, Adobe, Hulu, Amazon y OpenAi utilizan Redis.

Redis admite diferentes tipos de estructuras de datos abstractas, como cadenas, listas, mapas, conjuntos, conjuntos ordenados, HyperLogLogs, mapas de bits, flujos e índices espaciales.

El proyecto fue desarrollado y mantenido por Salvatore Sanfilippo a partir de 2009. Desde 2015 hasta 2020, lideró un equipo central del proyecto patrocinado por Redis Labs. Salvatore Sanfilippo dejó de ser el mantenedor de Redis en 2020. En 2021, Redis Labs eliminó "Labs" de su nombre y ahora se conoce simplemente como "Redis".

Redis se distribuye bajo una licencia BSD de 3 cláusulas.

## Historia

El nombre *Redis* significa Remote Dictionary Server. El proyecto Redis comenzó cuando Salvatore Sanfilippo, apodado *antirez*, el desarrollador original de Redis, intentaba mejorar la escalabilidad de su startup italiana mientras desarrollaba un analizador de registros web en tiempo real. Después de encontrar problemas significativos al escalar algunos tipos de cargas de trabajo con sistemas de bases de datos tradicionales, Sanfilippo comenzó a prototipar una primera versión de concepto de Redis en Tcl en 2009. Posteriormente, Sanfilippo tradujo ese prototipo al lenguaje C e implementó el primer tipo de dato, la lista. Después de unas semanas de éxito utilizando el proyecto internamente, Sanfilippo decidió hacerlo de código abierto y anunció el proyecto en Hacker News. El proyecto comenzó a ganar tracción, especialmente entre la comunidad de Ruby, con GitHub e Instagram entre las primeras empresas que lo adoptaron.

En marzo de 2010, Sanfilippo fue contratado por VMware.

En mayo de 2013, Redis fue patrocinado por Pivotal Software (una empresa derivada de VMware).

En junio de 2015, el desarrollo fue patrocinado por Redis Labs.

En octubre de 2018, se lanzó Redis 5.0, introduciendo Redis Stream, una nueva estructura de datos que permite el almacenamiento de múltiples campos y valores de cadena con una secuencia automática basada en el tiempo en una sola clave.

En junio de 2020, Salvatore Sanfilippo dejó de ser el mantenedor de Redis.

## Diferencias respecto a otros sistemas de bases de datos

Redis popularizó la idea de un sistema que puede considerarse tanto un almacén como una caché al mismo tiempo. Fue diseñado de manera que los datos siempre se modifican y leen desde la memoria principal de la computadora, pero también se almacenan en disco en un formato que no es adecuado para el acceso aleatorio a datos. Los datos formateados solo se reconstruyen en memoria una vez que el sistema se reinicia.

Redis también proporciona un modelo de datos que es muy inusual en comparación con un sistema de gestión de bases de datos relacionales (RDBMS). Los comandos de usuario no describen una consulta que debe ser ejecutada por el motor de la base de datos, sino operaciones específicas que se realizan en tipos de datos abstractos dados. Por lo tanto, los datos deben almacenarse de una manera que sea adecuada para una recuperación rápida posterior. La recuperación se realiza sin la ayuda del sistema de bases de datos en forma de índices secundarios, agregaciones u otras características comunes de los RDBMS tradicionales. La implementación de Redis hace un uso intensivo de la llamada al sistema "fork" para duplicar el proceso que contiene los datos, de manera que el proceso principal continúe atendiendo a los clientes mientras el proceso secundario crea una copia en memoria de los datos en disco.

## Popularidad

Según las clasificaciones mensuales de DB-Engines, Redis suele ser la base de datos clave-valor más popular. Redis también ha sido clasificado como la cuarta base de datos NoSQL en satisfacción del usuario y presencia en el mercado según las revisiones de los usuarios, la base de datos NoSQL más popular en contenedores y la cuarta base de datos en el ranking de sitios web stackshare.io en 2019. Además, Redis fue votado como la base de datos más querida en la Encuesta de Desarrolladores de Stack Overflow en 2017, 2018, 2019, 2020 y 2021.

## Idiomas compatibles

Desde la versión 2.6, Redis ofrece scripting en el lado del servidor en el lenguaje Lua. Muchos lenguajes de programación tienen bibliotecas de lenguaje de cliente para Redis, incluyendo ActionScript, C, C++, C#, Chicken, Clojure, Common Lisp, Crystal, D, Dart, Delphi, Elixir, Erlang, Go, Haskell, Haxe, Io, Java, Nim, JavaScript (Node.js), Julia, Lua, Objective-C, OCaml, Perl, PHP, Pure Data, Python, R, Racket, Ruby, Rust, Scala, Smalltalk, Swift y Tcl. Existen varios programas de software cliente en estos idiomas.

## Tipos de Datos

Redis asigna claves a tipos de valores. Una diferencia importante entre Redis y otros sistemas de almacenamiento estructurado es que Redis no solo admite cadenas, sino también tipos de datos abstractos, que incluyen:

- Listas de cadenas.
- Conjuntos de cadenas (colecciones de elementos no repetidos y no ordenados).
- Conjuntos ordenados de cadenas (colecciones de elementos no repetidos ordenados por un número de punto flotante llamado puntaje).
- Tablas hash donde las claves y los valores son cadenas.
- HyperLogLogs utilizados para estimaciones de la cardinalidad de conjuntos aproximados, disponibles desde Redis 2.8.9 en abril de 2014.
- Secuencias de entradas con grupos de consumidores, que permiten almacenar múltiples campos y valores de cadena con una secuencia automática basada en el tiempo en una sola clave, disponible desde Redis 5.0 en octubre de 2018.
- Datos geoespaciales a través de la implementación de la técnica de geohash, disponible desde Redis 3.2.

El tipo de un valor determina qué operaciones (llamadas comandos) están disponibles para el valor. Redis admite operaciones de alto nivel, atómicas y en el lado del servidor, como la intersección, la unión y la diferencia entre conjuntos, y la ordenación de listas, conjuntos y conjuntos ordenados.

Se admiten más tipos de datos basados en la API de módulos de Redis. Ten en cuenta que algunos de ellos tienen licencias duales y no están bajo la licencia BSD de 3 cláusulas.

- JSON: RedisJSON implementa ECMA-404 (el Estándar de Intercambio de Datos de Notación de Objetos de JavaScript) como un tipo de datos nativo.
- Búsqueda: un motor de consultas para Redis que proporciona indexación secundaria, búsqueda de texto completo, búsqueda de similitud de vectores y agregaciones.
- Series temporales: RedisTimeSeries implementa una estructura de datos de series temporales.
- Filtros de Bloom, filtros Cuckoo, esbozos Count-Min y Top-K: RedisBloom implementa un conjunto de estructuras de datos probabilísticas para Redis.
- Otros.

Implementaciones anteriores incluyen:

- Grafos: RedisGraph implementa un grafo de propiedades consultable.
- RedisGraph ha sido descontinuado y continúa en forma de un fork llamado FalkorDB.

## Persistencia

Redis generalmente mantiene todo el conjunto de datos en memoria. Las versiones hasta la 2.4 podían configurarse para utilizar lo que llaman "memoria virtual", en la que parte del conjunto de datos se almacenaba en disco, pero esta característica está obsoleta. La persistencia en Redis se puede lograr a través de dos métodos diferentes. El primero es mediante "snapshotting", donde el conjunto de datos se transfiere de forma asincrónica de la memoria al disco en intervalos regulares como un volcado binario, utilizando el formato de archivo de volcado RDB de Redis. Alternativamente, mediante "journaling", donde se agrega un registro de cada operación que modifica el conjunto de datos a un archivo solo de anexado (AOF) en un proceso en segundo plano. Redis puede reescribir el archivo solo de anexado en segundo plano para evitar un crecimiento indefinido del registro. El journaling se introdujo en la versión 1.1 y generalmente se considera el enfoque más seguro.

Por defecto, Redis escribe datos en el sistema de archivos al menos cada 2 segundos, con opciones más o menos robustas disponibles si es necesario. En el caso de un fallo completo del sistema con la configuración predeterminada, solo se perderían unos pocos segundos de datos.

## Replicación

Redis admite la replicación maestro-replica. Los datos de cualquier servidor Redis pueden replicarse en cualquier número de réplicas. Una réplica puede ser maestra para otra réplica. Esto permite que Redis implemente un árbol de replicación con una única raíz. Las réplicas de Redis pueden configurarse para aceptar escrituras, lo que permite inconsistencias intencionales y no intencionales entre las instancias. La característica de publicar-suscribir está completamente implementada, por lo que un cliente de una réplica puede suscribirse a un canal y recibir un flujo completo de mensajes publicados en el maestro, en cualquier punto del árbol de replicación. La replicación es útil para la escalabilidad de lectura (pero no de escritura) o la redundancia de datos.

## Rendimiento

Cuando no se necesita la durabilidad de los datos, la naturaleza en memoria de Redis le permite rendir bien en comparación con los sistemas de bases de datos que escriben cada cambio en disco antes de considerar una transacción como confirmada. Redis opera como un único proceso y es de un solo hilo o de doble hilo cuando reescribe el archivo de solo anexado (AOF). Por lo tanto, una sola instancia de Redis no puede utilizar la ejecución paralela de tareas como los procedimientos almacenados.

## Clúster

Redis introdujo el clúster en abril de 2015 con el lanzamiento de la versión 3.0. La especificación de clúster implementa un subconjunto de comandos de Redis: todos los comandos de una sola clave están disponibles, las operaciones con múltiples claves (comandos relacionados con uniones e intersecciones) están restringidas a claves pertenecientes al mismo nodo y los comandos relacionados con operaciones de selección de base de datos no están disponibles. Un clúster de Redis puede escalar hasta 1,000 nodos, lograr una seguridad de escritura "aceptable" y continuar operaciones cuando algunos nodos fallan.

## Casos de Uso

Debido a la naturaleza del diseño de la base de datos, los casos de uso típicos incluyen el almacenamiento en caché de sesiones, la caché de páginas completas, aplicaciones de colas de mensajes, clasificaciones y conteo, entre otros. El paradigma de mensajería publicar-suscribir permite la comunicación en tiempo real entre servidores.

Amazon Web Services ofrece un servicio gestionado de Redis llamado ElastiCache para Redis, Google ofrece un servicio gestionado de Redis llamado Cloud Memorystore, Microsoft ofrece Azure Cache para Redis en Azure y Alibaba ofrece ApsaraDB for Redis en Alibaba Cloud.

## Usuarios

Redis se utiliza en empresas como Twitter, Airbnb, Tinder, Yahoo, Adobe, Hulu y Amazon.
