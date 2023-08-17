# Bases de Datos Relacional

La **base de datos relacional** (BDR) es un tipo de [base de datos](https://es.wikipedia.org/wiki/Base_de_datos) (BD) que cumple con el [modelo relacional](https://es.wikipedia.org/wiki/Modelo_relacional) (el modelo más utilizado actualmente para implementar las BD ya planificadas). Tras ser postuladas sus bases en [1970](https://es.wikipedia.org/wiki/1970) por [Edgar Frank Codd](https://es.wikipedia.org/wiki/Edgar_Frank_Codd),[1](https://es.wikipedia.org/wiki/Base_de_datos_relacional#cite_note-1) de los laboratorios [IBM](https://es.wikipedia.org/wiki/IBM) en [San José (California)](https://es.wikipedia.org/wiki/San_Jos%C3%A9_(California)), no tardó en consolidarse como un nuevo paradigma en los modelos de base de datos.[2](https://es.wikipedia.org/wiki/Base_de_datos_relacional#cite_note-2)

Un sistema de software utilizado para mantener las bases de datos relacionales es un *relational database management system* (RDBMS) o sistema de gestión de bases de datos relacionales. Virtualmente, todos los sistemas de bases de datos relacionales utilizan [SQL](https://es.wikipedia.org/wiki/SQL) (Structured Query Language) para consultar y mantener la base de datos.

## Características comunes

- Una [base de datos](https://es.wikipedia.org/wiki/Base_de_datos) se compone de varias [tablas](https://es.wikipedia.org/wiki/Tabla_(base_de_datos)), denominadas relaciones.
- No pueden existir dos tablas con el mismo nombre ni registro.
- Cada tabla es a su vez un conjunto de [campos](https://es.wikipedia.org/wiki/Campo_(base_de_datos)) ([columnas](https://es.wikipedia.org/wiki/Columna_(base_de_datos))) y [registros](https://es.wikipedia.org/wiki/Registro_(base_de_datos)) (filas).
- La relación entre una tabla padre y un hijo se lleva a cabo por medio de las llaves primarias y llaves foráneas (o ajenas).
- Las llaves primarias son la clave principal de un registro dentro de una tabla y estas deben cumplir con la [integridad de datos](https://es.wikipedia.org/wiki/Integridad_de_datos).
- Las llaves ajenas se colocan en la tabla hija, contienen el mismo valor que la llave primaria del registro padre; por medio de estas se hacen las formas relacionales.

## Elementos

*Véase también: [Dato](https://es.wikipedia.org/wiki/Dato)*

### Relaciones (características en común)

En una BDR, todos los datos se almacenan y se accede a ellos por medio de relaciones previamente establecidas.

### Relaciones base

Las relaciones que almacenan datos son llamadas **relaciones base** y su implementación es llamada "**[tabla](https://es.wikipedia.org/wiki/Tabla_(base_de_datos))**".

### Relaciones derivadas

Otras relaciones no almacenan datos, pero son calculadas al aplicar operaciones relacionales. Estas relaciones son llamadas **relaciones derivadas** y su implementación es llamada "**vista**" o "**consulta**". Las relaciones derivadas son convenientes, ya que expresan información de varias relaciones actuando como si fuera una sola tabla.

Algunas no son determinadas por los usuarios, sino que son inherentemente definidas por el simple hecho de que la BD sea relacional. Algunas otras restricciones las puede definir el usuario, por ejemplo, usar un campo con valores enteros entre 1 y 10.

Las restricciones proveen un método de implementar "reglas" en la base de datos.

Las restricciones limitan los datos que pueden ser almacenados en las tablas.

Usualmente se definen usando expresiones que dan como resultado un valor booleano, indicando si los datos satisfacen la restricción o no.

Las restricciones no son parte informal y formal del modelo relacional, pero son incluidas porque juegan el rol de organizar mejor los datos. Las restricciones son muy discutidas junto con los conceptos relacionales.

### Dominios

Un dominio describe un conjunto de posibles valores para cierto atributo. Como un dominio restringe los valores del atributo, puede ser considerado como una restricción. Matemáticamente, atribuir un dominio a un atributo significa "cualquier valor de este atributo debe ser elemento del conjunto especificado".

Distintos tipos de dominios son: enteros, cadenas de texto, fecha, no procedurales, etc.

Cada tabla puede tener uno o más campos cuyos valores identifican de forma única cada registro de dicha tabla, es decir, no pueden existir dos o más registros diferentes cuyos valores en dichos campos sean idénticos. Este conjunto de campos se llama clave única. Pueden existir varias claves únicas en una determinada tabla, y a cada una de estas suele llamársele candidata a clave primaria.

### **Clasificación de Claves

### **Clave primaria

Una clave primaria es una clave única (puede estar conformada por uno o más campos de la tabla) elegida entre todas las candidatas que define unívocamente a todos los demás atributos de la tabla para especificar los datos que serán relacionados con las demás tablas. La forma de hacer esto (relación entre tablas) es por medio de claves foráneas.

### **Clave externa o foránea

Una clave foránea es una referencia a una clave en otra tabla, determina la relación existente en dos tablas. Las claves foráneas no necesitan ser claves únicas en la tabla donde están y sí a donde están referenciadas.

Por ejemplo, el código de departamento puede ser una clave foránea en la tabla de empleados. Se permite que haya varios empleados en un mismo departamento, pero habrá uno y solo un departamento por cada clave distinta de departamento en la tabla de departamentos.

### Clave índice

Las claves índice surgen con la necesidad de tener un acceso más rápido a los datos. Los índices pueden ser creados con cualquier combinación de campos de una tabla. Las consultas que filtran registros por medio de estos campos, pueden encontrar los registros de forma no secuencial usando la clave índice.

Las bases de datos relacionales incluyen múltiples técnicas de ordenamiento, cada una de ellas es óptima para cierta distribución de datos y tamaño de la relación.

Los índices generalmente no se consideran parte de la base de datos, pues son un detalle agregado. Sin embargo, las claves índices son desarrolladas por el mismo grupo de programadores que las otras partes de la base de datos.

![https://upload.wikimedia.org/wikipedia/commons/e/ed/Diagrama_Empleado.jpeg](https://upload.wikimedia.org/wikipedia/commons/e/ed/Diagrama_Empleado.jpeg)

### **Procedimientos almacenados

Un procedimiento almacenado es código ejecutable que se asocia y se almacena con la base de datos. Los procedimientos almacenados usualmente recogen y personalizan operaciones comunes, como insertar un registro dentro de una tabla, recopilar información estadística, o encapsular cálculos complejos. Son frecuentemente usados por un [API](https://es.wikipedia.org/wiki/Interfaz_de_programaci%C3%B3n_de_aplicaciones) por seguridad o simplicidad.

Los procedimientos almacenados no son parte del modelo relacional, pero todas las implementaciones comerciales los incluyen.

## Estructura y definiciones

Terminología de una base de datos relacional: [tupla](https://es.wikipedia.org/wiki/Tupla), atributo y relación.

![https://upload.wikimedia.org/wikipedia/commons/thumb/7/7c/Relational_database_terms.svg/langes-350px-Relational_database_terms.svg.png](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7c/Relational_database_terms.svg/langes-350px-Relational_database_terms.svg.png)

La base de datos se organiza en dos marcadas secciones; el esquema y los datos (o instancia).

El esquema es la definición de la estructura de la base de datos y principalmente almacena los siguientes datos:

- El nombre de cada [tabla](https://es.wikipedia.org/wiki/Tabla_(base_de_datos))
- El nombre de cada [columna](https://es.wikipedia.org/wiki/Columna_(base_de_datos))
- El tipo de dato de cada columna
- La tabla a la que pertenece cada columna

Las bases de datos relacionales pasan por un proceso al que se le conoce como [normalización de una base de datos](https://es.wikipedia.org/wiki/Normalizaci%C3%B3n_de_una_base_de_datos). Dicho proceso se basa principalmente en el concepto de [dependencia funcional](https://es.wikipedia.org/wiki/Dependencia_funcional) es un esquema que permite que la base de datos sea usada de manera óptima.[3](https://es.wikipedia.org/wiki/Base_de_datos_relacional#cite_note-3)

Los datos o instancia es el contenido de la base de datos en un momento dado. Es en sí, el contenido de todos los registros.

La tabla inferior resume algunos de los términos más importantes de las bases de datos relacionales y el término SQL correspondiente(en inglés):

| Término SQL | Término de bases de datos relacionales | Descripción |
| --- | --- | --- |
| https://es.wikipedia.org/wiki/Matriz_(matem%C3%A1ticas) | https://es.wikipedia.org/wiki/Tupla o https://es.wikipedia.org/wiki/Registro_(base_de_datos) | Un conjunto de datos, que representa un ítem simple |
| https://es.wikipedia.org/wiki/Columna_(base_de_datos) | Atributo o campo | Un elemento etiquetado de una tupla, p.e. "Dirección" o "Fecha de nacimiento" |
| https://es.wikipedia.org/wiki/Tabla_(base_de_datos) | https://es.wikipedia.org/wiki/Modelo_relacional o Base relvar | Un conjunto de tuplas compartiendo los mismos atributos; un conjunto de filas y columnas. |
| https://es.wikipedia.org/wiki/Vista_(base_de_datos) o https://es.wikipedia.org/w/index.php?title=Conjunto_de_resultados&action=edit&redlink=1 | Relvar derivado | Cualquier conjunto de tuplas; un reporte o informe de datos de una RDBMS en respuesta a una https://es.wikipedia.org/w/index.php?title=Consulta_(inform%C3%A1tica)&action=edit&redlink=1 |

## Manipulación de la información

Para manipular la información utilizamos un lenguaje relacional, actualmente se cuenta con dos lenguajes formales el [álgebra relacional](https://es.wikipedia.org/wiki/%C3%81lgebra_relacional) y el [cálculo relacional](https://es.wikipedia.org/wiki/C%C3%A1lculo_relacional). El álgebra relacional permite describir la forma de realizar una consulta, en cambio, el cálculo relacional solo indica lo que se desea devolver.

El lenguaje más común para construir las consultas a bases de datos relacionales es el [SQL](https://es.wikipedia.org/wiki/SQL) (*Structured Query Language*), un estándar implementado por los principales motores o sistemas de gestión de bases de datos relacionales integradas.

En el [modelo relacional](https://es.wikipedia.org/wiki/Modelo_relacional) los [atributos](https://es.wikipedia.org/wiki/Atributo_(inform%C3%A1tica)) deben estar explícitamente relacionados con un nombre en todas las operaciones, en cambio, el estándar SQL permite usar columnas sin nombre en conjuntos de resultados, como el asterisco taquigráfico (`*`) como notación de consultas.

Al contrario del modelo relacional, el estándar [SQL](https://es.wikipedia.org/wiki/SQL) requiere que las columnas tengan un orden definido, lo cual es fácil de implementar en una computadora, ya que la memoria es lineal.

Es de notar, sin embargo, que en [SQL](https://es.wikipedia.org/wiki/SQL) el orden de las columnas y los registros devueltos en cierto conjunto de resultado nunca está garantizado, a no ser que explícitamente sea especificado por el usuario.

## Gestores de base de datos relacionales

Existe un tipo de [software](https://es.wikipedia.org/wiki/Software) exclusivamente dedicado a tratar con bases de datos relacionales, conocido como [sistema de gestión de bases de datos](https://es.wikipedia.org/wiki/Sistema_de_gesti%C3%B3n_de_bases_de_datos) Relacionales (**SGBDR**, o **RDBMS** del inglés *Relational Database Management System*), también llamados manejadores o gestores de las BDR.

Entre los gestores actuales más populares existen:

- [Microsoft SQL Server](https://es.wikipedia.org/wiki/Microsoft_SQL_Server).
- [Oracle](https://es.wikipedia.org/wiki/Oracle).
- [DB2](https://es.wikipedia.org/wiki/DB2).
- [PostgreSQL](https://es.wikipedia.org/wiki/PostgreSQL).
- [MariaDB](https://es.wikipedia.org/wiki/MariaDB)
- [MySQL](https://es.wikipedia.org/wiki/MySQL).

Otros

## Ventajas y desventajas

**Ventajas**:

- Provee herramientas que garantizan evitar la duplicidad de registros.
- Garantiza la integridad referencial, así, al eliminar un registro elimina todos los registros relacionados dependientes.
- Favorece la normalización por ser más comprensible y aplicable.

**Desventajas**:

- Presentan deficiencias con datos gráficos, multimedia, [CAD](https://es.wikipedia.org/wiki/Dise%C3%B1o_asistido_por_computador) y [sistemas de información geográfica](https://es.wikipedia.org/wiki/Sistema_de_Informaci%C3%B3n_Geogr%C3%A1fica).
- No se manipulan de forma manejable los bloques de texto como tipo de dato.
- Las [bases de datos orientadas a objetos](https://es.wikipedia.org/wiki/Base_de_datos_orientada_a_objetos) (BDOO) se propusieron con el objetivo de satisfacer las necesidades de las aplicaciones anteriores y así, complementar pero no sustituir a las bases de datos relacionales.

## Diseño de las bases de datos relacionales

El primer paso para crear una base de datos, es planificar el tipo de información que se quiere almacenar en la misma, teniendo en cuenta dos aspectos: la información disponible y la información que necesitamos.

La planificación de la estructura de la base de datos, en particular de las tablas, es vital para la gestión efectiva de la misma. El diseño de la estructura de una tabla consiste en una descripción de cada uno de los campos que componen el registro y los valores o datos que contendrá cada uno de esos campos.

Los campos son los distintos tipos de datos que componen la tabla, por ejemplo: nombre, apellido, domicilio. La definición de un campo requiere: el nombre del campo, el tipo de campo, el ancho del campo, etc.

Los registros constituyen la información que va contenida en los campos de la tabla, por ejemplo: el nombre del paciente, el apellido del paciente y la dirección de este. Generalmente los diferentes tipos de campos que se pueden almacenar son los siguientes: Texto (caracteres), Numérico (números), Fecha / Hora, Lógico (informaciones lógicas si/no, verdadero/falso, etc.), imágenes.

En resumen, el principal aspecto a tener en cuenta durante el diseño de una tabla es determinar claramente los campos necesarios, definirlos en forma adecuada con un nombre especificando su tipo y su longitud.
