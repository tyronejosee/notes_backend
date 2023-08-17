# Modelo entidad-relación

Ejemplo de diagrama E-R

![https://upload.wikimedia.org/wikipedia/commons/thumb/f/f6/Ejemplo_Diagrama_E-R_extendido.PNG/400px-Ejemplo_Diagrama_E-R_extendido.PNG](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f6/Ejemplo_Diagrama_E-R_extendido.PNG/400px-Ejemplo_Diagrama_E-R_extendido.PNG)

Un **modelo entidad-relación** es una herramienta para el [modelo de datos](https://es.wikipedia.org/wiki/Modelo_de_datos), la cual facilita la representación de entidades de una [base de datos](https://es.wikipedia.org/wiki/Base_de_datos).[1](https://es.wikipedia.org/wiki/Modelo_entidad-relaci%C3%B3n#cite_note-1) Fue definido por [Peter Chen](https://es.wikipedia.org/wiki/Peter_Chen) en 1976.

## Uso

Se suelen desarrollar en dos fases:

1. Se elabora el diagrama (o diagramas) entidad-relación.
2. Se completa el modelo con listas de atributos y una descripción de otras restricciones que no se pueden reflejar en el diagrama.

El modelado de datos no acaba con el uso de esta técnica. Son necesarias otras técnicas para lograr un modelo directamente implementable en una base de datos. Brevemente:

Permite mostrar resultados entre otras entidades pertenecientes a las existentes de manera que se encuentre la normalidad de archivos que se almacenarán.

- Transformación de relaciones múltiples en binarias.
- [Normalización de una base de datos](https://es.wikipedia.org/wiki/Normalizaci%C3%B3n_de_bases_de_datos) de relaciones (algunas relaciones pueden transformarse en atributos y viceversa).
- Conversión en tablas (en caso de utilizar una [base de datos relacional](https://es.wikipedia.org/wiki/Base_de_datos_relacional)).

## Base teórica y conceptual

El modelo de datos entidad-relación está basado en una percepción del mundo real que consta de una colección de objetos básicos, llamados entidades, y de relaciones entre esos objetos amorfos.

### **Entidad[[editar](https://es.wikipedia.org/w/index.php?title=Modelo_entidad-relaci%C3%B3n&action=edit&section=3)]**

Representa una “cosa”, "objeto", o "concepto" del mundo real con existencia independiente, es decir, se diferencia únicamente de otro objeto o cosa, incluso siendo del mismo tipo, o una misma entidad.

Algunos ejemplos:

- Una persona: se diferencia de cualquier otra persona, incluso siendo gemelos.
- Un automóvil: aunque sean de la misma marca, el mismo modelo, etc, tendrán atributos diferentes, por ejemplo, el número de chasis.
- Una casa: aunque sea exactamente igual a otra, aún se diferenciará en su dirección.

Una entidad puede ser un objeto con existencia física como: una persona, un animal, una casa, etc. (entidad concreta); o un objeto con existencia conceptual como: un puesto de trabajo, una asignatura de clases, un nombre, etc. (entidad abstracta).

Una entidad está descrita y se representa por sus características o atributos. Por ejemplo, la entidad *Persona* tiene como características: Nombre, Apellido, Género, Estatura, Peso, Fecha de nacimiento.

### **Atributos[[editar](https://es.wikipedia.org/w/index.php?title=Modelo_entidad-relaci%C3%B3n&action=edit&section=4)]**

Los atributos son las características que definen o identifican a una entidad. Éstas pueden ser muchas, y el diseñador sólo utiliza o implementa las que considere más relevantes.

En un conjunto de entidades del mismo tipo, cada entidad tiene **valores** específicos asignados para cada uno de sus atributos, de esta forma, es posible su identificación unívoca.

Ejemplos:

A la colección de entidades «alumnos», con el siguiente conjunto de atributos en común, (id, nombre, edad, semestre), pertenecen las entidades:

- (1, Sophia, 15 años, 2)
- (2, Josefa, 19 años, 1)
- (3, Carlos, 20 años, 2)
- ...

Cada una de las entidades pertenecientes a este conjunto se diferencia de las demás por el valor de sus atributos. Nótese que dos o más entidades diferentes pueden tener los mismos valores para algunos de sus atributos, pero nunca para todos.

En particular, los **atributos identificativos** son aquellos que permiten diferenciar a una instancia de la entidad de otra distinta. Por ejemplo, el atributo identificativo que distingue a un alumno de otro es su número de id.

Para cada atributo, existe un **dominio** del mismo que hace referencia al tipo de datos que será almacenado a restricciones en los valores que el atributo puede tomar (cadenas de caracteres, números, sólo dos letras, sólo números mayores que cero, sólo números enteros...).

Cuando algún atributo correspondiente a una entidad no tiene un valor determinado, recibe el **valor nulo**, bien sea porque no se conoce, porque no existe o porque no se sabe nada al respecto del mismo.

### **Conjunto de relaciones[[editar](https://es.wikipedia.org/w/index.php?title=Modelo_entidad-relaci%C3%B3n&action=edit&section=5)]**

Consiste en una colección, o conjunto, de relaciones de la misma naturaleza.

Ejemplo:

Dados los **conjuntos de entidades** "Habitación" y "Huésped", todas las relaciones de la forma habitación-huésped, permiten obtener la información de los huéspedes y sus respectivas habitaciones.

La dependencia o asociación entre los conjuntos de entidades es llamada **participación**. En el ejemplo anterior los conjuntos de entidades "Habitación" y "Huésped" **participan** en el conjunto de relaciones habitación-huésped.

Se llama **grado** del conjunto de relaciones a la cantidad de conjuntos de entidades participantes en la relación.

## Restricciones[[editar](https://es.wikipedia.org/w/index.php?title=Modelo_entidad-relaci%C3%B3n&action=edit&section=6)]

Son reglas que deben respetar las entidades y relaciones almacenadas en la base de datos.

### **Correspondencia de cardinalidades[[editar](https://es.wikipedia.org/w/index.php?title=Modelo_entidad-relaci%C3%B3n&action=edit&section=7)]**

Dado un conjunto de relaciones en el que participan dos o más conjuntos de entidades, la cardinalidad de la correspondencia indica el número de entidades con las que puede estar relacionada una entidad dada.

Dado un conjunto de relaciones binarias y los conjuntos de entidades A y B, las cardinalidades pueden ser:

- **Uno a Uno:** (1:1) Un registro de una entidad A se relaciona con solo un registro en una entidad B. (ejemplo dos entidades, profesor y departamento, con llaves primarias, código_profesor y jefe_depto respectivamente, un profesor solo puede ser jefe de un departamento y un departamento solo puede tener un jefe).
- **Uno a Varios:** (1:N) Un registro en una entidad en A se relaciona con uno o muchos registros en una entidad B. Pero los registros de B solamente se relacionan con un registro en A. (ejemplo: dos entidades, vendedor y ventas, con llaves primarias, código_vendedor y venta, respectivamente, un vendedor puede tener muchas ventas pero una venta solo puede tener un vendedor).
- **Varios a Uno:** (N:1) Una entidad en A se relaciona exclusivamente con una entidad en B. Pero una entidad en B se puede relacionar con 1 o muchas entidades en A (ejemplo empleado-centro de trabajo).
- **Varios a Varios:** (N:M) Una entidad en A se puede relacionar con 1 o con muchas entidades en B y viceversa (ejemplo asociaciones-ciudadanos, donde muchos ciudadanos pueden pertenecer a una misma asociación, y cada ciudadano puede pertenecer a muchas asociaciones distintas).

### **Restricciones de participación[[editar](https://es.wikipedia.org/w/index.php?title=Modelo_entidad-relaci%C3%B3n&action=edit&section=8)]**

Dado un conjunto de relaciones R en el cual participa un conjunto de entidades A, dicha participación puede ser de dos tipos:

- **Total:** Cuando cada entidad en A participa en al menos una relación de R.
- **Parcial:** Cuando al menos una entidad en A NO participa en alguna relación de R.

## Claves[[editar](https://es.wikipedia.org/w/index.php?title=Modelo_entidad-relaci%C3%B3n&action=edit&section=9)]

Es un subconjunto del conjunto de atributos comunes en una colección de entidades, que permite identificar inequívocamente cada una de las entidades pertenecientes a dicha colección. Asimismo, permiten distinguir entre sí las relaciones de un conjunto de relaciones.

Dentro de los conjuntos de entidades existen los siguientes tipos de claves:

- **Superclave:** Es un subconjunto de atributos que permite distinguir unívocamente cada una de las entidades de un conjunto de entidades. Si se añade un atributo al anterior subconjunto, el resultado seguirá siendo una superclave.
- **Clave candidata:** Se trata de superclave mínima, es decir, cualquier subconjunto de atributos de la misma no puede ser una superclave.
- **Clave primaria:** Es una clave candidata, elegida por el diseñador de la base de datos, para identificar unívocamente las entidades en un conjunto de entidades.

Los valores de los atributos de una clave, no pueden ser todos iguales para dos o más instancias.

Para poder distinguir unívocamente las relaciones en un conjunto de relaciones R, se deben considerar dos casos:

- **R NO tiene atributos asociados:** En este caso, se usa como clave primaria de R la unión de las claves primarias de todos los conjuntos de entidades participantes.
- **R tiene atributos asociados:** En este caso, se usa como clave primaria de R la unión de los atributos asociados y las claves primarias de todos los conjuntos de entidades participantes.

Si el conjunto de relaciones, R, sobre las que se pretende determinar la clave primaria está compuesto de relaciones binarias, con los conjuntos de entidades participantes A y B, se consideran los siguientes casos, según sus cardinalidades:

- **R es de muchos a uno de A a B** entonces solo se toma la clave primaria de A, como clave primaria de R.
- **R es de uno a muchos de A a B** entonces se toma solo la clave primaria de B, como clave primaria de R.
- **R es de uno a uno de A a B** entonces se toma cualquiera de las dos claves primarias, como clave primaria de R, y se crea una restricción de no repetición para la otra clave.
- **R es de muchos a muchos de A a B** entonces se toma la unión de los atributos que conforman las claves primarias de A y de B, como clave primaria de R.

## Diagrama entidad-relación[[editar](https://es.wikipedia.org/w/index.php?title=Modelo_entidad-relaci%C3%B3n&action=edit&section=10)]

Anteriormente detallamos los conceptos relacionados al modelo ER, en esta sección profundizaremos en como representarlos gráficamente. Cabe destacar que para todo proceso de modelado, siempre hay que tener en claro los conceptos, estos nos brindan conocimiento necesario y además fundamentan nuestro modelo al momento de presentarlo a terceros.

Formalmente, los diagramas ER son un lenguaje gráfico para describir conceptos. Informalmente, son simples dibujos o gráficos que describen información que trata un sistema de información y el *software* que lo automatiza.

### **Entidades[[editar](https://es.wikipedia.org/w/index.php?title=Modelo_entidad-relaci%C3%B3n&action=edit&section=11)]**

Las entidades son el fundamento del modelo entidad relación. Podemos adoptar como definición de entidad cualquier cosa o parte del mundo que es distinguible del resto. Por ejemplo, en un sistema bancario, las personas y las cuentas bancarias se podrían interpretar como entidades. Las entidades pueden representar entes concretos, como una persona o un avión, o abstractas, como por ejemplo un préstamo o una reserva. Se representan por medio de un rectángulo y pueden ser de tipo: maestras, transaccionales, históricas y temporales.

### **Atributos[[editar](https://es.wikipedia.org/w/index.php?title=Modelo_entidad-relaci%C3%B3n&action=edit&section=12)]**

Se representan mediante un círculo o elipse etiquetado con un nombre en su interior. Cuando un atributo es identificativo de la entidad se suele subrayar dicha etiqueta.

Por motivos de legibilidad, los atributos suelen no aparecer representados en el diagrama entidad-relación, sino descritos textualmente en otros documentos adjuntos.

### **Relación[[editar](https://es.wikipedia.org/w/index.php?title=Modelo_entidad-relaci%C3%B3n&action=edit&section=13)]**

Describe cierta dependencia entre entidades o permite la asociación de las mismas.

Por ejemplo:

Si tenemos dos entidades, CLIENTE y HABITACIÓN, podemos entender la relación entre ambas al tomar un caso concreto (ocurrencia) de cada una de ellas. Entonces, podríamos tener la ocurrencia Habitación 502, de la entidad HABITACIÓN y la ocurrencia Henry Johnson McFly Bogard, de la entidad CLIENTE, entre las que es posible relacionar que la habitación 502 se encuentra ocupada por el huésped de nombre Henry Johnson McFly Bogard.

## Diagramas extendidos[[editar](https://es.wikipedia.org/w/index.php?title=Modelo_entidad-relaci%C3%B3n&action=edit&section=14)]

DER extendido

![https://upload.wikimedia.org/wikipedia/commons/thumb/f/fc/Diagrama_Entidad_Relacion.svg/300px-Diagrama_Entidad_Relacion.svg.png](https://upload.wikimedia.org/wikipedia/commons/thumb/f/fc/Diagrama_Entidad_Relacion.svg/300px-Diagrama_Entidad_Relacion.svg.png)

Los diagramas Entidad-Relación no cumplen su propósito con eficacia debido a que tienen limitaciones semánticas. Por ese motivo se suelen utilizar los *diagramas Entidad-Relación extendidos* (EER) que incorporan algunos elementos más al lenguaje:

### **Entidades fuertes y débiles[[editar](https://es.wikipedia.org/w/index.php?title=Modelo_entidad-relaci%C3%B3n&action=edit&section=15)]**

Cuando una entidad participa en una relación puede adquirir un papel *fuerte* o *débil*. Una entidad débil es aquella que no puede existir sin participar en la relación; es decir, aquella que no puede ser unívocamente identificada solamente por sus atributos.

Una entidad fuerte (también conocida como entidad regular) es aquella que sí puede ser identificada unívocamente. En los casos en que se requiera, se puede dar que una entidad fuerte "preste" algunos de sus atributos a una entidad débil para que esta última se pueda identificar.

Las entidades débiles se representan mediante un **doble rectángulo**; es decir, un rectángulo con doble línea.

Se puede hablar de la existencia de dos tipos de dependencias en las entidades débiles:

**Dependencia por existencia**Las ocurrencias de la entidad débil pueden identificarse mediante un atributo identificador clave sin necesidad de identificar la entidad fuerte relacionada.

**Dependencia por identidad**La entidad débil no puede ser identificada sin la entidad fuerte relacionada. (Ejemplo: si tenemos una entidad LIBRO y otra relacionada EDICIÓN, para identificar una edición necesitamos conocer el identificador del libro).

### **Cardinalidad de las relaciones[[editar](https://es.wikipedia.org/w/index.php?title=Modelo_entidad-relaci%C3%B3n&action=edit&section=16)]**

Cardinalidad es el número de entidades con la cual otra entidad puede asociar mediante una relación binaria; la cardinalidad puede ser: Uno a uno, uno a muchos o muchos a uno y muchos a muchos. El tipo de cardinalidad se representa mediante una etiqueta en el exterior de la relación, respectivamente: "1:1", "1:N" y "N:M", aunque la notación depende del lenguaje utilizado, la que más se usa actualmente es el unificado. Otra forma de expresar la cardinalidad es situando un símbolo cerca de la línea que conecta una entidad con una relación:

- **"0"** si cada instancia de la entidad no está obligada a participar en la relación.
- **"1"** si toda instancia de la entidad está obligada a participar en la relación y, además, solamente participa una vez.
- **"N" , "M", ó "*"** si cada instancia de la entidad no está obligada a participar en la relación y puede hacerlo cualquier número de veces.

(también se puede representar como N:M) Ejemplos de relaciones que expresan cardinalidad:

- Un policía (entidad) tiene (relación) un arma (entidad) siempre y cuando no realice funciones de oficina, pudiendo entonces tenerla o no asignada. Es una relación 0:1.
- Cada esposo (entidad) está casado (relación) con una única esposa (entidad) y viceversa. Es una relación 1:1.
- Una factura (entidad) se emite (relación) a una persona (entidad) y solo una, pero una persona puede tener varias facturas emitidas a su nombre. Todas las facturas se emiten a nombre de alguien. Es una relación N:1.
- Varios clientes (entidad) pueden comprar (relación) varios servicios (entidad) y varios servicios pueden ser comprados, contratados o alquilados por varios clientes distintos. Es una relación N:M.

### **Atributos en relaciones[[editar](https://es.wikipedia.org/w/index.php?title=Modelo_entidad-relaci%C3%B3n&action=edit&section=17)]**

Las relaciones también pueden tener atributos asociados. Se representan igual que los atributos de las entidades. Un ejemplo típico son las relaciones de tipo "histórico" donde debe constar una fecha o una hora. Por ejemplo, supongamos que es necesario hacer constar la fecha de emisión de una factura a un cliente, y que es posible emitir duplicados de la factura (con distinta fecha). En tal caso, el atributo "Fecha de emisión" de la factura debería colocarse en la relación "se emite".

### **Herencia[[editar](https://es.wikipedia.org/w/index.php?title=Modelo_entidad-relaci%C3%B3n&action=edit&section=18)]**

La herencia es un intento de adaptación de estos diagramas al paradigma orientado a objetos. La herencia es un tipo de relación entre una entidad "padre" y una entidad "hijo". La entidad "hijo" hereda todos los atributos y relaciones de la entidad "padre". Por tanto, no necesitan ser representadas dos veces en el diagrama. La relación de herencia se representa mediante un triángulo invertido interconectado por líneas a las entidades. La entidad conectada por la parte superior del triángulo es la entidad "padre". Solamente puede existir una entidad "padre" (herencia simple). Las entidades "hijo" se conectan por la parte inferior del triángulo.

### Agregación

Ejemplo agregación

![https://upload.wikimedia.org/wikipedia/commons/thumb/f/fb/Ejemplo_de_Agregaci%C3%B3n.svg/400px-Ejemplo_de_Agregaci%C3%B3n.svg.png](https://upload.wikimedia.org/wikipedia/commons/thumb/f/fb/Ejemplo_de_Agregaci%C3%B3n.svg/400px-Ejemplo_de_Agregaci%C3%B3n.svg.png)

Es un tipo de relación dinámica, donde el tiempo de vida de una o más entidades de bajo nivel que están incluidas en una entidad de alto nivel es independiente a la entidad que la incluye(entidad de alto nivel).

Es una abstracción a través de la cual las relaciones se tratan como entidades de un nivel más alto. Se utiliza para expresar relaciones entre relaciones o entre entidades y relaciones. Se representa englobando la relación abstraída y las entidades que participan en ella en un rectángulo. En la figura se muestra un ejemplo de agregación en el que se representa la situación en la que un profesor, cuando está impartiendo una clase, puede poner una incidencia ocurrida a lo largo de ésta (se fue la luz, falta la configuración de un determinado *software*, etc.).
