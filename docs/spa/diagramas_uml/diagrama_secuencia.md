# Diagrama de Secuencia

https://www.lucidchart.com/pages/es/diagrama-de-secuencia

!https://prod-files-secure.s3.us-west-2.amazonaws.com/117043f3-0b4b-44f8-8c43-6d7b267128c8/bca735fb-900e-475b-81ac-0b19f87ba738/UML-sequence-diagram-featured-image.png

Los diagramas de secuencia son una solución de modelado dinámico popular en UML porque se centran específicamente en *líneas de vida* o en los procesos y objetos que coexisten simultáneamente, y los mensajes intercambiados entre ellos para ejecutar una función antes de que la línea de vida termine. Junto con nuestra [herramienta de diagramación UML](https://www.lucidchart.com/pages/examples/uml_diagram_tool), usa esta guía para aprender más sobre los diagramas de secuencia en UML.

7 minutos de lectura

¿Deseas crear un diagrama UML por tu cuenta? Prueba Lucidchart. Es rápido, sencillo y totalmente gratis.

## ¿Qué es un diagrama de secuencia en UML?

Para comprender lo que es un diagrama de secuencia, es importante conocer la función del [Lenguaje Unificado de Modelado](https://www.lucidchart.com/pages/what-is-UML-unified-modeling-language), mejor conocido como UML. El UML es un conjunto de herramientas de modelado que orienta la creación y notación de muchos tipos de diagramas, incluidos los diagramas de comportamiento, los diagramas de interacción y los diagramas de estructuras.

Un diagrama de secuencia es un tipo de diagrama de interacción porque describe cómo —y en qué orden— un grupo de objetos funcionan en conjunto. Tanto los desarrolladores de software como los profesionales de negocios usan estos diagramas para comprender los requisitos de un sistema nuevo o documentar un proceso existente. A los diagramas de secuencia en ocasiones se los conoce como diagramas de eventos o escenarios de eventos.Observa que hay dos tipos de diagramas de secuencia: los diagramas UML y los diagramas que se basan en código. Los últimos se obtienen de un código de programación y no serán cubiertos en esta guía. El [software de diagramas UML](https://www.lucidchart.com/pages/examples/uml_diagram_tool) de Lucidchart está equipado con todas las figuras y funciones que necesitarás para modelar ambos.

## Los beneficios de los diagramas de secuencia

Los diagramas de secuencia pueden ser referencias útiles para las empresas y otras organizaciones. Prueba dibujar un diagrama de secuencia para:

- 
    
    Representa los detalles de un caso de uso en UML.
    
- 
    
    Modelar la lógica de una operación, una función o un procedimiento sofisticados.
    
- 
    
    Ve cómo los objetos y los componentes interactúan entre sí para completar un proceso.
    
- 
    
    Planificar y comprender la funcionalidad detallada de un escenario actual o futuro.
    

## Los casos de uso para los diagramas de secuencia

Los siguientes escenarios son ideales para usar un diagrama de secuencia:

- 
    
    **Escenario de uso:** Un escenario de uso es un diagrama de cómo se podría usar potencialmente tu sistema. Es una excelente manera de asegurar que has estudiado la lógica de cada escenario de uso para el sistema.
    
- 
    
    **Lógica del método:** Al igual que utilizarías un diagrama de secuencia UML para explorar la lógica de un caso de uso, puedes usarlo para explorar la lógica de cualquier función, procedimiento o proceso complejo.
    
- 
    
    **Lógica de servicio:** Si consideras que un servicio es un método de alto nivel empleado por diferentes clientes, un diagrama de secuencia es una forma ideal de trazarlo.
    
- 
    
    **Diagrama de secuencia Visio** - Todo diagrama de secuencia que crees con Visio también se podrá subir a Lucidchart. Lucidchart permite la importación de archivos .vsd y .vdx y es una excelente alternativa a Microsoft Visio. Casi todas las imágenes que ves en la sección UML de este sitio fueron generadas con Lucidchart.
    

Crear diagramas es rápido y sencillo con Lucidchart. Inicia una prueba gratuita hoy mismo para empezar a crear y colaborar.

[Crea un diagrama UML](https://lucid.app/es/pricing/lucidchart?anonId=0.1a38b6df18ab48590a1&sessionDate=2023-09-20T21%3A36%3A06.825Z&sessionId=0.2f99134118ab48590a8&type=discovery)

## Componentes y símbolos básicos

Para comprender qué es un diagrama de secuencia, debes estar familiarizado con sus símbolos y componentes. Los diagramas de secuencia están formados por los siguientes elementos e íconos:

| Símbolo | Nombre | Descripción |
| --- | --- | --- |
|  | Símbolo de objeto | Representa una clase u objeto en UML. El símbolo objeto demuestra cómo se comportará un objeto en el contexto del sistema. Los atributos de las clases no deben aparecer en esta figura. |
|  | Casilla de activación | Representa el tiempo necesario para que un objeto finalice una tarea. Cuanto más tiempo lleve la tarea, más larga será la casilla de activación. |
|  | Símbolo de actor | Muestra entidades que interactúan con el sistema o que son externas al sistema. |
|  | Símbolo de paquete | Se usa en notación UML 2.0 para contener los elementos interactivos del diagrama. También conocida como "marco", esta figura rectangular tiene un pequeño rectángulo interior para etiquetar el diagrama.  |
|  | Símbolo de línea de vida | Representa el paso del tiempo a medida que se extiende hacia abajo. Esta línea vertical discontinua representa eventos secuenciales que le ocurren a un objeto durante el proceso graficado. Las líneas de vida pueden comenzar con una figura rectangular etiquetada o un símbolo de actor. |
|  | Símbolo de bucle de opción | Se emplea para modelar escenarios del tipo "Si... entonces...", es decir, una circunstancia que solo sucederá en determinadas condiciones. |
|  | Símbolo de alternativas | Simboliza una decisión (que, por lo general, es mutuamente exclusiva) entre dos o más secuencias de mensajes. Para representar alternativas, emplea la figura rectangular etiquetada con una línea discontinua en su interior. |

### Símbolos comunes de mensajes

Usa los siguientes símbolos de mensaje y flechas para indicar cómo se transmite la información entre objetos. Estos símbolos pueden reflejar el inicio y la ejecución de una operación o el envío y la recepción de una señal.

| Símbolo | Nombre | Descripción |
| --- | --- | --- |
|  | Símbolo de mensaje sincrónico | Representados por una línea continua y una punta de flecha sólida. Este símbolo se utiliza cuando un remitente debe esperar una respuesta a un mensaje antes de proseguir. El diagrama debe mostrar el mensaje y la respuesta. |
|  | Símbolo de mensaje asincrónico | Representados por una línea continua y una punta de flecha simple. Los mensajes asincrónicos no necesitan una respuesta para que el remitente siga adelante. Solo la llamada se debe incluir en el diagrama. |
|  | Símbolo de mensaje de respuesta asincrónico | Representados por una línea discontinua y una punta de flecha simple. |
|  | Símbolo de crear mensaje asincrónico | Representados por una línea discontinua y una punta de flecha simple. Este mensaje crea un nuevo objeto. |
|  | Símbolo de mensaje de respuesta | Están representados con una línea discontinua y una punta de flecha simple. Estos mensajes son las respuestas a las llamadas. |
|  | Símbolo de eliminar mensaje | Están representados por una línea continua y una punta de flecha sólida, seguida de una X. Este mensaje destruye un objeto. |

## Ejemplos de diagramas de secuencia

### Diagrama de secuencia para un sistema administrativo hospitalario

La tecnología ha transformado por completo el campo de la medicina, como lo ha hecho con la mayoría de las industrias. Un sistema administrativo hospitalario, también conocido como sistema informático hospitalario, ayuda a los médicos, los administradores y el personal hospitalario que administran todas las actividades e información recopilada en el hospital, incluidos exámenes, prescripciones, citas e información sobre los pacientes y sus cuidadores. El siguiente diagrama proporciona una visión simple de cómo los procesos primarios operan entre sí a lo largo del tiempo. Puedes usar Lucidchart para rediseñar el diagrama de cualquier forma que elijas y compartirlo con tus colegas o colaboradores.

*[Haz clic aquí para usar esta plantilla.](https://www.lucidchart.com/documents/editNewOrRegister/34722cd4-8874-4869-a2ee-135c0ca60ed6?anonId=0.1a38b6df18ab48590a1&sessionDate=2023-09-20T21%3A36%3A06.825Z&sessionId=0.2f99134118ab48590a8)*

### Diagrama de secuencia para sistemas de cajero automático ATM

Un cajero ATM permite a los clientes acceder a sus cuentas bancarias a través de un proceso completamente automatizado. Puedes examinar los pasos de este proceso de una forma manejable dibujando o visualizando un diagrama de secuencia. El siguiente ejemplo describe el orden secuencial de las interacciones en el sistema ATM. Solo haz clic para editar la plantilla y personaliza el diagrama de secuencia para que se adapte a tus necesidades.

[Haz clic aquí para usar esta plantilla.](https://www.lucidchart.com/documents/editNewOrRegister/8fef4499-ae84-4345-a48f-4e98f417a693/0?anonId=0.1a38b6df18ab48590a1&sessionDate=2023-09-20T21%3A36%3A06.825Z&sessionId=0.2f99134118ab48590a8)

## Cómo trazar un diagrama de secuencia

En Lucidchart, crear un diagrama de secuencia desde cero es sorprendentemente simple. Solo sigue estos pasos:

1. 
    
    Abre un documento en blanco o empieza con una plantilla.
    
2. 
    
    A la izquierda del editor, haz clic en "Figuras" para abrir el Administrador de bibliotecas de figuras.
    
3. 
    
    Marca "UML" para habilitar todas las bibliotecas de figuras UML o "UML" para habilitar figuras específicas de los diagramas de secuencia UML. Haz clic en "Guardar".
    
4. 
    
    Arrastra los símbolos que necesites de la caja de herramientas al lienzo.
    
5. 
    
    Luego modela el flujo de procesos trazando líneas entre las figuras mientras agregas texto.
    

Analiza en detalle esta guía sobre [cómo dibujar un diagrama de secuencia en UML](https://www.lucidchart.com/pages/how-to-draw-a-sequence-diagram-in-UML) para obtener una perspectiva adicional. En Lucidchart, es sencillo modificar el tamaño y el estilo de cualquier elemento. Puedes incluso generar un diagrama de secuencia UML completo a través del marcado de texto. Si deseas aprender más sobre UML, echa un vistazo a nuestro tutorial "[¿Qué es UML?](https://www.lucidchart.com/pages/what-is-UML-unified-modeling-language)"
