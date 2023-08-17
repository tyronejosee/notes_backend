# Bases de Datos NoSQL

## ¿Qué es una base de datos NoSQL?

NoSQL se refiere a una gran variedad de tecnologías de bases de datos que se han desarrollado en respuesta a las necesidades de desarrollo de las aplicaciones modernas:

- Los desarrolladores trabajan con aplicaciones que generan enormes volúmenes de datos nuevos y en constante evolución (estructurados, semiestructurados, no estructurados y polimórficos).
- Aquellos ciclos de desarrollo en cascada que duraban entre 12 y 18 meses hace tiempo que pasaron a la historia. Ahora se trabaja en equipos pequeños, que realizan sprints de desarrollo ágiles con iteraciones rápidas, y que generan código cada semana o cada quince días, algunos incluso varias veces al día.
- Las aplicaciones que antes servían a un conjunto finito de usuarios ahora se proporcionan como servicios, que no solo deben funcionar sin interrupción, sino que además tienen que ser accesibles desde muchos dispositivos distintos y deben poder escalarse a millones de usuarios de todo el mundo.
- Organizations are now turning to scale-out architectures using open software technologies, commodity servers and cloud computing instead of large monolithic servers and storage infrastructure.

Las bases de datos relacionales no se diseñaron para poder hacer frente a la escalabilidad y agilidad que necesitan las aplicaciones modernas, ni para beneficiarse de los sistemas de almacenamiento básicos y de la potencia de proceso que existen hoy en día.

## Tipos de bases de datos NoSQL

- **Bases de datos de documentos**: en estas bases de datos se empareja cada clave con una estructura de datos compleja que se denomina 'documento'. Los documentos pueden contener muchos pares de clave-valor distintos, o pares de clave-matriz, o incluso documentos anidados.
- **Almacenes de grafos**: se utilizan para almacenar información sobre redes de datos, como las conexiones sociales. Ejemplos de almacenes de grafos son Neo4J y Giraph.
- **Almacenes de clave-valor**: son las bases de datos NoSQL más simples. Cada elemento de la base de datos se almacena como un nombre de atributo (o «clave»), junto con su valor. Ejemplos de almacenes de clave-valor son Riak y Berkeley DB. En algunos almacenes de clave-valor, como Redis, cada valor puede tener un tipo, como «entero», lo que le añade funcionalidad.
- **Bases de datos orientadas a columnas**: estas bases de datos, como Cassandra o HBase, permiten realizar consultas en grandes conjuntos de datos y almacenan los datos en columnas, en lugar de filas.

## Ventajas de NoSQL

Si se comparan con las bases de datos relacionales, las bases de datos NoSQL son [más escalables y ofrecen un mayor rendimiento](https://www.mongodb.com/es/mongodb-scale); además, su modelo de datos aborda varias cuestiones que el modelo relacional pasa por alto:

- Grandes volúmenes de datos estructurados, semiestructurados y no estructurados en constante cambio
- Sprints de desarrollo ágiles, iteración rápida de los esquemas y generación frecuente de código
- Programación orientada a objetos flexible y fácil de usar
- Arquitectura de escalado horizontal distribuida geográficamente, en lugar de una arquitectura monolítica

## Esquemas dinámicos.

En las bases de datos relacionales es necesario definir los esquemas antes de añadir los datos. Por ejemplo, si desea almacenar datos de clientes, como el número de teléfono, nombre y apellidos, dirección, ciudad y provincia, la base de datos SQL debe conocer de antemano el tipo de datos que va a almacenar.

Esto dificulta [la agilidad en el desarrollo](https://www.mongodb.com/es/agile-development), porque cada vez que se añaden características, con frecuencia se debe modificar el esquema de la base de datos. Así, si tras varias iteraciones de desarrollo, decide que desea almacenar los artículos favoritos de los clientes además de su dirección y teléfono, deberá añadir esa columna a la base de datos y luego migrar la base de datos entera al nuevo esquema.

Si la base de datos es grande, el proceso será muy lento y la actividad quedará interrumpida de forma prolongada. Si cambia a menudo los datos que almacena la aplicación —porque realiza iteraciones rápidamente— también se interrumpirá la actividad de forma frecuente. En las bases relacionales tampoco se pueden incluir datos sin ningún tipo de estructura o desconocidos de antemano.

Las bases de datos NoSQL están diseñadas para que se puedan insertar datos sin un esquema predefinido. Por ello resulta fácil realizar modificaciones importantes en las aplicaciones en tiempo real sin interrupciones del servicio, de modo que el desarrollo es más rápido, la integración del código es más fiable y los administradores de las bases de datos tienen menos trabajo. Tradicionalmente, los desarrolladores han tenido que añadir código a la aplicación para realizar controles de calidad de los datos, como, por ejemplo, forzar la presencia de campos, tipos de datos o valores permisibles específicos. Las bases de datos NoSQL, al ser más sofisticadas, permiten la aplicación de las regla de validación en la base de datos, de modo que los usuarios pueden aplicar la gobernanza a los datos, aprovechando la agilidad que ofrece un esquema dinámico.

## sharding automático

Por el modo en el que están estructuradas, las bases de datos relacionales se suelen escalar de forma vertical: un solo servidor debe alojar toda la base de datos para garantizar un rendimiento aceptable de las operaciones JOIN y transacciones entre tablas. Esto encarece su coste con rapidez, limita la escalabilidad y crea un número de puntos de fallo relativamente pequeño para la infraestructura de bases de datos. La solución para que las aplicaciones puedan crecer de forma rápida es permitir la escalabilidad horizontal añadiendo servidores, en lugar de concentrar más capacidad en un único servidor.

Es posible aplicar el sharding a una base de datos SQL en un gran número de instancias de servidor, pero para ello normalmente se necesitan sistemas SAN y otras configuraciones complejas para que el hardware actúe como un único servidor. Como las bases de datos relacionales no proporcionan esta función de forma nativa, los equipos de desarrollo deben encargarse de implementar varias base de datos de este tipo en diferentes máquinas. Los datos se almacenan en cada instancia de base de datos de forma autónoma. El código de la aplicación se desarrolla para distribuir los datos, distribuir las consultas y agregar los resultados de los datos en todas las instancias de la base de datos. Se debe desarrollar código adicional para manejar los fallos de los recursos, y realizar operaciones JOIN entre diferentes bases de datos, así como para aplicar otros requisitos, como el reequilibrio de datos y la replicación. Además, muchas de las ventajas de las bases de datos relacionales, como la integridad transaccional, se ven afectadas o eliminadas al utilizar el sharding manual.

Por el contrario, las bases de datos NoSQL suelen admitir el auto-sharding, es decir, pueden distribuir los datos de forma nativa y automática entre un número arbitrario de servidores, sin que la aplicación deba tener constancia de la composición del grupo de servidores. Los datos y la carga de consultas se equilibran automáticamente entre los servidores, y cuando uno falla, se puede sustituir de forma rápida y transparente sin que la aplicación deje de funcionar.

[computación en la nube](https://www.mongodb.com/es/big-data-explained) facilita mucho las cosas, con proveedores como Amazon Web Services, que proporcionan una capacidad prácticamente ilimitada a la carta y se encargan de todas las tareas necesarias relativas a la administración de infraestructuras. Los desarrolladores ya no tienen que construir plataformas caras y complejas para poder ejecutar sus aplicaciones, sino que pueden concentrarse en programar el código. Los servidores básicos pueden proporcionar la misma capacidad de procesamiento y almacenamiento que un solo servidor de gama alta por un precio mucho más reducido.

## Replicación

La mayoría de las bases de datos NoSQL también admiten replicación automática de bases de datos para garantizar la disponibilidad en caso de que se produzcan interrupciones de servicio o paradas de mantenimiento planificadas. Las bases de datos NoSQL más sofisticadas son autorreparables y ofrecen las funciones de conmutación por error y recuperación, así como la posibilidad de distribuir la base de datos entre varias regiones geográficas para soportar fallos regionales y permitir la localización de los datos. A diferencia de las bases de datos relacionales, las bases de datos NoSQL no necesitan utilizar otras aplicaciones o complementos con un precio elevado para implementar la replicación.

## Caché integrada

Para los sistemas de bases de datos SQL existen varios productos que proporcionan un nivel de caché. Estos sistemas pueden mejorar el rendimiento de las operaciones de lectura de forma importante, pero no mejoran el rendimiento de las operaciones de escritura y añaden complejidad operativa a las implementaciones. Si en su aplicación la mayoría de las operaciones realizadas son de lectura, se puede considerar una caché distribuida, pero si solo tiene un volumen moderado de operaciones de escritura, puede que una caché distribuida no mejore la experiencia para los usuarios finales en términos generales, y añadirá complejidad a la hora de gestionar la invalidación de caché.

Muchas tecnologías de base de datos NoSQL incorporan excelentes funcionalidades de caché, que mantienen durante el máximo tiempo posible los datos usados con frecuencia en la memoria del sistema y hacen que sea innecesario disponer de una capa de caché independiente. Algunas bases de datos NoSQL también ofrecen una capa de gestión de la base de datos integrada en la memoria, pensada para cargas de trabajo que requieren el máximo rendimiento y una latencia mínima.

## Resumen sobre la comparativa entre NoSQL y SQL

|  | Bases de datos SQL | Bases de datos NoSQL |
| --- | --- | --- |
| Tipos | Un tipo (base de datos SQL) con pequeñas variaciones. | Muchos tipos, entre los que se incluyen almacenes de clave-valor, https://www.mongodb.com/es/document-databasesbases de datos orientadas a columnas y bases de datos de grafos. |
| Historia sobre el desarrollo | Se desarrollan a finales de la década de 1970 para respaldar la primera ola de aplicaciones de almacenamiento de datos. | Se desarrollan a finales de la década de 2000 para superar las limitaciones de las bases de datos SQL, sobre todo en lo relativo a escalabilidad, datos multiestructurados, distribución geográfica y sprints de desarrollo ágiles. |
| Ejemplos | MySQL, Postgres, Microsoft SQL Server, Oracle Database. | MongoDB, Cassandra, HBase, Neo4j. |
| Modelo de almacenamiento de datos | Los registros individuales (p. ej., «empleados») se almacenan en filas de tablas, y cada columna almacena un dato específico sobre ese registro (p. ej., «director», «fecha de contratación», etc.) al estilo de las hojas de cálculo. Los datos relacionados se almacenan en tablas separadas, y luego se combinan cuando se ejecutan consultas más complejas. Por ejemplo, «oficinas» se puede almacenar en una tabla y «empleados», en otra. Cuando un usuario quiere encontrar la dirección de trabajo de un empleado, el motor de la base de datos une las tablas «empleado» y «oficina» para obtener toda la información necesaria. | Varía en función del tipo de base de datos. Por ejemplo, los almacenes de clave-valor funcionan de forma parecida a las bases de datos SQL, pero solo tienen dos columnas («clave» y «valor»), con información más compleja, que a veces se almacena como objetos BLOB en las columnas «valor». Las bases de datos de documentos evitan por completo el modelo de tablas y filas, almacenando todos los datos relevantes juntos en un único documento en formato JSON, XML u otro formato, que puede anidar valores de forma jerárquica. |
| Esquemas | La estructura y los tipos de datos se establecen de entrada. Para almacenar información sobre un nuevo dato, se debe modificar toda la base de datos, que deja de funcionar durante este tiempo. | Suelen ser dinámicos, y en ocasiones es necesario aplicar algunas reglas de validación de datos. Las aplicaciones pueden ir añadiendo nuevos campos según convenga y, a diferencia de lo que ocurre con las filas de las tablas SQL, en caso necesario se pueden almacenar juntos datos de naturaleza diferente. Para algunas bases de datos (como las orientadas a columnas), resulta un poco más complicado añadir nuevos campos de forma dinámica. |
| Escalabilidad | Escalado vertical, es decir, es necesario añadir más potencia a un único servidor en caso de que aumente la demanda. Es posible repartir las bases de datos SQL por diferentes servidores, pero es una tarea que requiere una participación importante del equipo de ingeniería, y suelen perderse funcionalidades relacionales básicas como las operaciones JOIN, la integridad de las referencias y las transacciones. | Escalado horizontal, es decir, para aumentar la capacidad, el administrador de la base de datos solo tiene que añadir servidores básicos o instancias de la nube. La base de los datos distribuye los datos en los servidores según las necesidades. |
| Modelo de desarrollo | Mix of open technologies (e.g., Postgres, MySQL) and closed source (e.g., Oracle Database) | Open technologies |
| Soporta transacciones ACID de registros múltiples | Sí | Generalmente no. MongoDB 4.0 y posteriores admiten transacciones ACID de múltiples documentos. https://www.mongodb.com/es/transactions |
| Manipulación de datos | Lenguaje específico que utiliza instrucciones Select, Insert y Update, p. ej., SELECT fields FROM table WHERE... | A través de APIs orientadas a objetos |
| Coherencia | Se puede configurar un nivel de consistencia elevado | Depende del producto. Algunos ofrecen una consistencia elevada (p. ej., MongoDB, con consistencia ajustable para las lecturas), mientras que otros ofrecen consistencia eventual (p. ej., Cassandra). |

## Implementar una base de datos NoSQL

Often, organizations will begin with a small-scale trial of a NoSQL database in their organization, which makes it possible to develop an understanding of the technology in a low-stakes way. Most NoSQL databases are also based on open technologies and are free to use, meaning that they can be downloaded, implemented and scaled at little cost. Because development cycles are faster, organizations can also innovate more quickly and deliver superior customer experience at a lower cost.

Puede haber varios motivos para considerar alternativas a las infraestructuras: escalar el sistema que se utiliza o aumentar su rendimiento, identificar alternativas viables a un software de propiedad con un coste elevado o aumentar la velocidad y agilidad de desarrollo. A la hora de seleccionar la base de datos adecuada para su empresa y sus aplicaciones, debe tener en cuenta cinco factores importantes.
