# Inyección SQL

En informática, la **inyección SQL** es una técnica de **inyección de código** utilizada para atacar aplicaciones impulsadas por datos, en la que se insertan declaraciones SQL maliciosas en un campo de entrada para su ejecución (por ejemplo, para volcar el contenido de una base de datos al atacante). La inyección SQL debe aprovechar una vulnerabilidad de seguridad en el software de una aplicación, por ejemplo, cuando la entrada del usuario no se filtra correctamente para escapar caracteres literales de cadena incrustados en las declaraciones SQL o cuando la entrada del usuario no está fuertemente tipificada y se ejecuta de manera inesperada. La inyección SQL es conocida principalmente como un vector de ataque para sitios web, pero puede usarse para atacar cualquier tipo de base de datos SQL.

Los ataques de inyección SQL permiten a los atacantes suplantar identidades, manipular datos existentes, causar problemas de repudiación como anular transacciones o cambiar saldos, permitir la divulgación completa de todos los datos en el sistema, destruir los datos o hacer que no estén disponibles de otra manera, y convertirse en administradores del servidor de la base de datos. Las bases de datos NoSQL orientadas a documentos también pueden verse afectadas por esta vulnerabilidad de seguridad.

En un estudio realizado en 2012, se observó que la aplicación web promedio recibía cuatro campañas de ataque por mes, y los minoristas recibían el doble de ataques que otras industrias.

## Historia

Las primeras discusiones públicas sobre la inyección SQL comenzaron a aparecer alrededor de 1998; por ejemplo, un artículo de 1998 en la revista Phrack.

## Forma

La inyección SQL (SQLI) se consideró una de las 10 principales vulnerabilidades de aplicaciones web en 2007 y 2010 según el Proyecto de Seguridad de Aplicaciones Web Abiertas (OWASP). En 2013, SQLI ocupó el primer lugar en la lista de los diez principales ataques de OWASP. Hay cuatro subclases principales de inyección SQL:

- SQLI clásica
- Inyección SQL ciega o de inferencia
- SQLI específica del sistema de administración de bases de datos
- SQLI compuesta
- Inyección SQL + autenticación insuficiente
• Inyección SQL + ataques DDoS
• Inyección SQL + secuestro de DNS
• Inyección SQL + XSS

El gusano Storm es una representación de la SQLI compuesta.

Esta clasificación representa el estado de la SQLI, respetando su evolución hasta 2010; se está llevando a cabo una mayor refinación.

## Implementaciones técnicas

### Declaraciones SQL incorrectamente construidas

Esta forma de inyección se basa en el hecho de que las declaraciones SQL consisten tanto en datos utilizados por la declaración SQL como en comandos que controlan cómo se ejecuta la declaración SQL. Por ejemplo, en la declaración SQL **`select** * **from** person **where** name = 'susan' **and** age = 2`, la cadena 'susan' es un dato y el fragmento **`and** age = 2` es un ejemplo de un comando (el valor 2 también es un dato en este ejemplo).

La inyección SQL ocurre cuando una entrada de usuario especialmente diseñada es procesada por el programa receptor de una manera que permite que la entrada salga de un contexto de datos y entre en un contexto de comando. Esto permite al atacante alterar la estructura de la declaración SQL que se ejecuta.

Como ejemplo sencillo, imagina que los datos 'susan' en la declaración anterior fueron proporcionados por la entrada de un usuario. El usuario ingresó la cadena 'susan' (sin las comillas) en un campo de entrada de texto de un formulario web, y el programa utilizó declaraciones de concatenación de cadenas para formar la declaración SQL anterior a partir de tres fragmentos **`select** * **from** person **where** name='`, la entrada de usuario de 'susan', y `' **and** age = 2`.

Ahora imagina que en lugar de ingresar 'susan', el atacante ingresó `' **or** 1=1; *--*`.

El programa utilizará el mismo enfoque de concatenación de cadenas con los 3 fragmentos de **`select** * **from** person **where** name='`, la entrada de usuario de `' **or** 1=1; *--*`, y `' **and** age = 2`, y construirá la declaración **`select** * **from** person **where** name='' **or** 1=1; *-- and age = 2*`. Muchas bases de datos ignorarán el texto después de la cadena '--' ya que esto denota un comentario. La estructura del comando SQL es ahora **`select** * **from** person **where** name='' **or** 1=1;` y esto seleccionará todas las filas de personas en lugar de solo las que tienen el nombre 'susan' y la edad 2. El atacante ha logrado crear una cadena de datos que sale del contexto de datos y entra en un contexto de comando.

Un ejemplo más complejo se presenta a continuación.

Imagina que un programa crea una declaración SQL utilizando el siguiente comando de asignación de cadenas:

- *`var** statement = "SELECT * FROM users WHERE name = '" + userName + "'";`

Este código SQL está diseñado para extraer los registros del nombre de usuario especificado de su tabla de usuarios. Sin embargo, si la variable "userName" es manipulada de una manera específica por un usuario malintencionado, es posible que la declaración SQL haga más de lo que el autor del código pretendía. Por ejemplo, configurar la variable "userName" de la siguiente manera:

```bash
' OR '1'='1

```

o usando comentarios para bloquear incluso el resto de la consulta (existen tres tipos de comentarios SQL[[15]]). Todas las líneas tienen un espacio al final:

```bash
' OR '1'='1' --
' OR '1'='1' {
' OR '1'='1' /*

```

esto genera una de las siguientes declaraciones SQL en el lenguaje padre:

- *`SELECT** * **FROM** users **WHERE** name = '' **OR** '1'='1';`
- *`SELECT** * **FROM** users **WHERE** name = '' **OR** '1'='1' *-- ';*`

Si este código se usara en un procedimiento de autenticación, este ejemplo podría usarse para forzar la selección de todos los campos de datos (*) de *todos* los usuarios en lugar de un usuario específico como el autor del código pretendía, ya que la evaluación de '1'='1' siempre es verdadera.

El siguiente

valor de "userName" en la declaración a continuación provocaría la eliminación de la tabla "users" y la selección de todos los datos de la tabla "userinfo" (en esencia, revelando la información de cada usuario), utilizando una API que permite múltiples declaraciones:

```sql
a';DROPTABLE users;SELECT *FROM userinfo WHERE 't' = 't

```

Esta entrada genera la siguiente declaración SQL final:

- *`SELECT** * **FROM** users **WHERE** name = 'a';**DROP** **TABLE** users; **SELECT** * **FROM** userinfo **WHERE** 't' = 't';`

Si bien la mayoría de las implementaciones de servidores SQL permiten que se ejecuten varias declaraciones con una sola llamada de esta manera, algunas API de SQL como la función `mysql_query()` de PHP no permiten esto por razones de seguridad. Esto evita que los atacantes inyecten consultas completamente separadas, pero no les impide modificar consultas.

### Inyección SQL Ciega

La inyección SQL ciega se utiliza cuando una aplicación web es vulnerable a una inyección SQL, pero los resultados de la inyección no son visibles para el atacante. La página con la vulnerabilidad puede no ser una que muestre datos, pero se mostrará de manera diferente según los resultados de una declaración lógica inyectada en la declaración SQL legítima llamada para esa página. Este tipo de ataque ha sido tradicionalmente considerado intensivo en tiempo, ya que se necesitaba crear una nueva declaración para cada bit recuperado, y dependiendo de su estructura, el ataque podría consistir en muchas solicitudes infructuosas. Los avances recientes han permitido que cada solicitud recupere múltiples bits, sin solicitudes infructuosas, lo que permite una extracción más constante y eficiente. Hay varias herramientas que pueden automatizar estos ataques una vez que se ha establecido la ubicación de la vulnerabilidad y la información objetivo.

### Respuestas Condicionales

Un tipo de inyección SQL ciega fuerza a la base de datos a evaluar una declaración lógica en una pantalla de aplicación ordinaria. Como ejemplo, un sitio web de reseñas de libros utiliza una cadena de consulta para determinar qué reseña de libros mostrar. Entonces, la URL `https://books.example.com/review?id=5` haría que el servidor ejecutara la consulta

- *`SELECT** * **FROM** bookreviews **WHERE** ID = '5';`

a partir de la cual llenaría la página de reseñas con datos de la reseña con el ID 5, almacenada en la tabla bookreviews. La consulta se realiza completamente en el servidor; el usuario no conoce los nombres de la base de datos, la tabla ni los campos, ni conoce la cadena de consulta. El usuario solo ve que la URL anterior devuelve una reseña de un libro. Un hacker puede cargar las URLs `https://books.example.com/review?id=5 **OR** 1=1` y `https://books.example.com/review?id=5 **AND** 1=2`, lo que puede resultar en las consultas

- *`SELECT** * **FROM** bookreviews **WHERE** ID = '5' **OR** '1'='1'; **SELECT** * **FROM** bookreviews **WHERE** ID = '5' **AND** '1'='2';`

respectivamente. Si la reseña original se carga con la URL "1=1" y se devuelve una página en blanco o de error desde la URL "1=2", y la página devuelta no ha sido creada para alertar al usuario de que la entrada no es válida, o en otras palabras, no ha sido detectada por un script de prueba de entrada, es probable que el sitio sea vulnerable a un ataque de inyección SQL, ya que es probable que la consulta haya pasado con éxito en ambos casos. El hacker puede continuar con esta cadena de consulta diseñada para revelar la versión de MySQL que se ejecuta en el servidor: `https://books.example.com/review?id=5 **AND** substring(@@version, 1, INSTR(@@version, '.') - 1)=4`, lo que mostraría la reseña de un libro en un servidor que ejecuta MySQL 4 y una página en blanco o de error en caso contrario. El hacker puede continuar utilizando código dentro de cadenas de consulta para lograr su objetivo directamente o para obtener más información del servidor con la esperanza de descubrir otra vía de ataque.

### Inyección SQL de Segundo Orden

La inyección SQL de segundo orden ocurre cuando los valores enviados contienen comandos maliciosos que se almacenan en lugar de ejecutarse inmediatamente. En algunos casos, la aplicación puede codificar correctamente una declaración SQL y almacenarla como una SQL válida. Luego, otra parte de esa aplicación sin controles para protegerse contra la inyección SQL podría ejecutar esa declaración SQL almacenada. Este ataque requiere un mayor conocimiento sobre cómo se utilizan posteriormente los valores enviados. Los escáneres automatizados de seguridad de aplicaciones web no detectarían fácilmente este tipo de inyección SQL y es posible que deban recibir instrucciones manuales sobre dónde buscar evidencia de que se está intentando.

## Mitigación

La inyección SQL es un ataque bien conocido y se puede prevenir fácilmente mediante medidas simples. Después de un aparente ataque de inyección SQL a TalkTalk en 2015, la BBC informó que los expertos en seguridad estaban sorprendidos de que una empresa tan grande fuera vulnerable a esto.

### Mapeadores Objeto-Relacional (ORM)

Los desarrolladores pueden utilizar marcos ORM como Hibernate para crear consultas de bases de datos de manera segura y amigable para el desarrollador. Dado que las consultas a la base de datos ya no se construyen como cadenas, no existe el peligro de una vulnerabilidad de inyección.

### Firewalls de Aplicaciones Web

Aunque los productos WAF como ModSecurity CRS no pueden prevenir que las vulnerabilidades de inyección SQL se introduzcan en una base de código, pueden dificultar significativamente el descubrimiento y la explotación para un atacante.

### Declaraciones Parametrizadas

Con la mayoría de las plataformas de desarrollo, se pueden usar declaraciones parametrizadas que funcionan con parámetros (a veces llamados marcadores o variables vinculadas) en lugar de incrustar la entrada del usuario en la declaración. Un marcador solo puede almacenar un valor del tipo dado y no un fragmento SQL arbitrario. Por lo tanto, la inyección SQL simplemente se trataría como un valor de parámetro extraño (y probablemente no válido). En muchos casos, la declaración SQL está fija, y cada parámetro es un escalar, no una tabla. Luego, la entrada del usuario se asigna (

se vincula) a un parámetro.

### Aplicación en el Nivel de Codificación

El uso de bibliotecas de mapeo objeto-relacional evita la necesidad de escribir código SQL. La biblioteca ORM generará en efecto declaraciones SQL parametrizadas a partir del código orientado a objetos.

### Escapado

Una forma popular, aunque propensa a errores, de prevenir inyecciones es intentar escapar todos los caracteres que tienen un significado especial en SQL. El manual de un sistema de gestión de bases de datos SQL explica qué caracteres tienen un significado especial, lo que permite crear una lista negra exhaustiva de caracteres que necesitan ser traducidos. Por ejemplo, cada aparición de una comilla simple (`'`) en un parámetro debe reemplazarse por dos comillas simples (`''`) para formar un literal de cadena SQL válido. Por ejemplo, en PHP es habitual escapar los parámetros usando la función `mysqli_real_escape_string();` antes de enviar la consulta SQL:

```php
$mysqli = new mysqli('nombre_de_host', 'nombre_de_usuario_de_bd', 'contraseña_de_bd', 'nombre_de_bd');
$consulta = sprintf("SELECT * FROM `Usuarios` WHERE Usuario='%s' AND Contraseña='%s'",
                    $mysqli->real_escape_string($nombre_de_usuario),
                    $mysqli->real_escape_string($contraseña));
$mysqli->query($consulta);
```

Esta función agrega barras diagonales invertidas (`\\`) a los siguientes caracteres: `\\x00`, `\\n`, `\\r`, `\\\\`, `'`, `"` y `\\x1a`. Esta función se usa normalmente para hacer que los datos sean seguros antes de enviar una consulta a MySQL.

### Comprobación de Patrones

Los parámetros enteros, de punto flotante o booleanos, así como las cadenas, se pueden comprobar si su valor es una representación válida para el tipo dado. Las cadenas que deben seguir un patrón estricto (fecha, UUID, solo alfanuméricos, etc.) se pueden comprobar si coinciden con este patrón.

### Permisos de la Base de Datos

Limitar los permisos en el inicio de sesión de la base de datos utilizado por la aplicación web solo a lo que se necesita puede ayudar a reducir la efectividad de cualquier ataque de inyección SQL que explote errores en la aplicación web.

```sql
DENY SELECT ON sys.sysobjects TO webdatabaselogon;
DENY SELECT ON sys.objects TO webdatabaselogon;
DENY SELECT ON sys.tables TO webdatabaselogon;
DENY SELECT ON sys.views TO webdatabaselogon;
DENY SELECT ON sys.packages TO webdatabaselogon;
```
