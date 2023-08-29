# **ACID**

## ¿Qué es una Base de Datos Compatible con ACID?

La mayoría de las bases de datos SQL modernas utilizan estándares transaccionales como ACID para asegurar la integridad de los datos y evitar que los usuarios vean datos incorrectos o desactualizados. Esta publicación explora cómo funcionan estos estándares.

Cuando estás construyendo y manteniendo una aplicación, **lo último que deseas es preocuparte por la integridad de los datos**. Cobrarle incorrectamente a un cliente o perder sus datos puede ser catastrófico. Afortunadamente, las bases de datos que estás utilizando, como MySQL y Postgres, toman medidas especiales para asegurarse de que eso no suceda. Pero, ¿qué está pasando detrás de escena? La mayoría de las bases de datos SQL modernas utilizan estándares transaccionales como ACID para asegurar la integridad de los datos y evitar que los usuarios vean datos incorrectos o desactualizados. Esta publicación explora cómo funcionan.

## Todas las Xosas que Pueden Salir Mal con tus Transacciones

Los científicos de datos se preocupan por las largas consultas analíticas y el almacenamiento de datos, pero para los desarrolladores, las bases de datos se tratan de transacciones. Una transacción de base de datos es una serie de operaciones de base de datos agrupadas de manera lógica: insertar una fila aquí, actualizar un registro allá y más cosas por el estilo. Tu código de aplicación está realizando transacciones constantemente cada vez que registras un nuevo usuario o ese usuario actualiza su información de cuenta.

Sin embargo, lo que ocurre con las transacciones es que pueden salir muy mal. Puede ocurrir cualquier cantidad de cosas cuando estás tratando de escribir en tu base de datos: puedes perder la conexión con una instancia remota, puedes encontrarte con errores de valor o cualquier otra cosa bajo el sol. Lo has visto, lo has enfrentado y puede significar un desastre para tus datos subyacentes. Echemos un vistazo a un ejemplo rápido que una empresa como Amazon podría enfrentar:

- El usuario actualiza la cantidad del pedido y hace clic en "ordenar ahora" →
- Actualizar la cantidad del pedido en la tabla de pedidos pendientes
- Agregar una fila a la tabla de pedidos
- Aplicar la compra al saldo del usuario / cargar la tarjeta de crédito

Si algo sale mal en medio de este grupo de operaciones pero el sistema sigue ejecutándolas, el usuario será cobrado por una cantidad incorrecta. Y si el cargo no funciona, obtendrán su pedido gratis. Resulta que **estos tipos de errores de datos tienen nombres** y hay muchos de ellos. Algunos ejemplos:

### Lecturas Sucias

Si una transacción está en medio de la actualización de algunos datos y aún no se ha confirmado, y se permite que otra transacción lea esos datos no confirmados, eso es sucio y podría llevar a que tu aplicación muestre datos incorrectos que se deshicieron.

Un ejemplo de lectura sucia podría ser una transacción que invalide tokens de inicio de sesión cuando un usuario cambia su contraseña. Si, mientras la primera transacción carga el token, una segunda lee ese token antes de que la primera lo invalide, tendrías una lectura sucia.

En términos de **SQL** real, así es como podría verse una lectura sucia:

```sql
### Transacción 1 ###

SELECT id_token_inicio_sesion_usuario
FROM tokens

UPDATE tokens
SET estado_token = "INVALIDO"
WHERE id_token = id_token_inicio_sesion_usuario

### Transacción 2 ###

SELECT id_token_inicio_sesion_usuario
FROM tokens

```

### Lecturas No Repetibles

Si tienes dos lecturas consecutivas en una transacción con una actualización concurrente en el medio, esas lecturas mostrarán resultados diferentes aunque sean parte de la misma transacción.

Un ejemplo podría ser dos escritores que trabajan en un blog. Nuestro primer usuario inicia una transacción que lee el título de una publicación, escribe en la publicación y luego lee nuevamente el título de esa publicación. Si un segundo usuario cambia el título de esa publicación en medio de la transacción del primer usuario, este verá valores diferentes para el título en las dos lecturas; o en otras palabras, una lectura no repetible.

Así es como podría verse una lectura no repetible en SQL:

```sql
### Transacción 1 ###

SELECT titulo_publicacion
FROM publicaciones

SELECT
    titulo_publicacion,
    contenido_publicacion
FROM publicaciones

### Transacción 2 ###

UPDATE publicaciones
SET titulo_publicacion = "algo_nuevo"
WHERE titulo_publicacion = titulo_publicacion

```

### Lecturas Fantasma

Si una transacción lee datos y luego una transacción concurrente inserta datos que habrían sido leídos en la transacción original, eso es una lectura fantasma.

Utilicemos el mismo ejemplo que una lectura no repetible: si nuestro segundo usuario agrega contenido entre las dos lecturas de nuestro primer usuario, la primera lectura no contendrá los datos que aparecen en la segunda lectura (esto es en realidad muy similar a una lectura no repetible, por eso funciona el mismo ejemplo).

En SQL, una lectura fantasma podría verse así:

```sql
### Transacción 1 ###

SELECT titulo_publicacion
FROM publicaciones

SELECT
    titulo_publicacion,
    contenido_publicacion
FROM publicaciones

### Transacción 2 ###

INSERT INTO publicaciones
VALUES "algo_nuevo", ...

```

Estos son los 3 errores transaccionales **según lo define el estándar SQL**: los tres grandes, podríamos decir. Muchos de estos errores suenan parecidos entre sí y tienden a superponerse en la práctica, así que no te preocupes por los detalles. Para obtener información más detallada, consulta la **serie de blogs de Vlad Mihalcea sobre el tema**.

Ahora, la pregunta importante: ¿cómo evitamos estos errores?

## ACID, pero en su forma buena

Las bases de datos relacionales populares como MySQL evitan estos tipos de problemas de integridad de datos siguiendo algunos principios fundamentales que rigen cómo funcionan las transacciones. Se ajustan a un estándar transaccional llamado ACID. ACID es un acrónimo de cuatro palabras diferentes, pero realmente se divide en dos principios fundamentales: integridad y concurrencia. Primero, aquí tienes lo que significa ACID:

- **Atomicidad**: la regla de "todo o nada": la transacción ocurre por completo o no ocurre en absoluto
- **Consistencia**: los datos son consistentes antes y después de una transacción sin pasos faltantes
- **Aislamiento**: múltiples transacciones pueden ocurrir simultáneamente sin leer datos incorrectos
- **Durabilidad**: el éxito transaccional es robusto ante fallas del sistema

Estos se superponen mucho, así que solo recuerda: el punto de cualquier base de datos compatible con ACID es asegurarse de que

- Las transacciones pueden fallar sin dañar la integridad de los datos
- Múltiples transacciones pueden ocurrir simultáneamente sin leer y escribir datos incorrectos

ACID es un conjunto de propiedades, pero no es un proceso: ¿cómo logran las bases de datos SQL que utilizamos realmente cumplir con ACID? Utilizan un sistema llamado bloqueo para mantener la base de datos en espera mientras ocurren las transacciones. El bloqueo funciona como imaginas: cuando comienza una transacción, el motor de la base de datos bloquea los datos con los que está trabajando hasta que se complete la transacción (y a veces incluso después). De esta manera, las transacciones concurrentes no pueden trabajar con los datos que está cambiando la primera transacción.

Una vez que una transacción comienza y adquiere un bloqueo, puede terminar con éxito y confirmarse, o puede encontrarse con un error y abortarse. Es algo así como escribir en una hoja de cálculo de Excel antes de guardar tu trabajo: las cosas cambian, pero solo de manera suave, hasta que las guardas (confirmas) o las reviertes (abortas). Volviendo a nuestro ejemplo de Amazon: si nuestra base de datos se encuentra con un error justo después de actualizar la cantidad de un pedido de un usuario, la transacción se abortará y será como si esa actualización nunca hubiera ocurrido. Y si el error ocurriera durante la actualización, la tarjeta de crédito nunca se cargará. O todo ocurre o nada ocurre, y eso es ACID.

Los detalles de la confirmación y los bloqueos son bastante complejos, pero un buen comienzo es el excelente artículo de **Methods and Tools** sobre el tema.

## Conceptos ACID en Sistemas NoSQL y Distribuidos

ACID fue un pilar de las confiables bases de datos relacionales con las que estamos familiarizados hoy en día, pero NoSQL ha cambiado el juego: muchas bases de datos NoSQL están construidas como sistemas distribuidos y no siempre pueden garantizar una consistencia transaccional completa. En realidad, existe una teoría que gobierna esto, llamada **teorema CAP**, que en sistemas distribuidos, no puedes tener una consistencia y disponibilidad totales al mismo tiempo; debes elegir una. Entonces, ¿cómo se ve ACID para algo como MongoDB o Cassandra?

Ha surgido un nuevo cuasi-estándar para las bases de datos NoSQL llamado BASE (una rara coincidencia entre bromas de SQL y química), y es un modelo de consistencia débil o suave que relaja algunas de las suposiciones de ACID para lograr escalabilidad:

- **Disponibilidad Básica**: la base de datos funciona básicamente la mayor parte del tiempo, aunque no sea perfecta
- **Estado Suave**: los nodos de la base de datos no son necesariamente consistentes entre sí todo el tiempo
- **Consistencia Eventual**: los datos serán consistentes en los nodos eventualmente, como en el momento de la lectura

En muchos aspectos, esto es exactamente lo contrario de ACID y prioriza la disponibilidad sobre la consistencia perfecta; pero ese es un poco el punto de NoSQL en primer lugar. A medida que NoSQL se convierte en una parte más establecida del desarrollo de aplicaciones (más del 25% de los desarrolladores ya están utilizando MongoDB), espera más avances en este frente.

Hoy en día, estamos tratando con más datos de los que nunca hemos tenido, y estamos construyendo sistemas de bases de datos que pueden escalar y manejar esa carga. ACID podría no ser el estándar transaccional exacto para el futuro, pero sus componentes seguramente se integrarán. Y si estás construyendo con una base de datos y deseas una manera rápida y sencilla de agregar funcionalidad adicional, echa un vistazo a Retool.
