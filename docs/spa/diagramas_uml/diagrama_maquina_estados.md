# Diagrama de Maquina de Estados

https://www.lucidchart.com/pages/es/diagrama-de-maquina-de-estados

!https://prod-files-secure.s3.us-west-2.amazonaws.com/117043f3-0b4b-44f8-8c43-6d7b267128c8/bf65cd3d-ea48-4391-a6c4-f9616e4255df/FeaturedImage.png

Un diagrama de estados, en ocasiones conocido como diagrama de máquina de estados, es un tipo de diagrama de comportamiento en el Lenguaje Unificado de Modelado (UML) que muestra transiciones entre diversos objetos. Usa nuestro [software de diagramas UML](https://www.lucidchart.com/pages/examples/uml_diagram_tool) colaborativo y genera tu propio diagrama de máquina de estados al crear una cuenta gratuita de Lucidchart hoy mismo.

5 minutos de lectura

¿Deseas crear un diagrama UML por tu cuenta? Prueba Lucidchart. Es rápido, sencillo y totalmente gratis.

[Crea un diagrama UML](https://lucid.app/es/pricing/lucidchart?anonId=0.68c0e0618ab4873c9d&sessionDate=2023-09-20T21%3A37%3A56.385Z&sessionId=0.0babcfe818ab4873ca0&type=discovery)

## ¿Qué es un diagrama de estados en UML?

Una máquina de estados es cualquier dispositivo que almacena el estado de un objeto en un momento dado y puede cambiar el estado o causar otras acciones según la entrada que reciba. Estados se refiere a las diferentes combinaciones de información que un objeto puede mantener, no la forma en que el objeto se comporta. Para comprender los diferentes estados de un objeto, podrías visualizar todos los estados posibles y mostrar cómo un objeto llega a cada estado, y puedes hacerlo con un diagrama de estados UML.

Cada diagrama de estados generalmente empieza con un círculo oscuro que indica el estado inicial y termina con un círculo de contorno blanco que denota el estado final. Sin embargo, a pesar de tener puntos de inicio y finalización definidos, los diagramas de estado no necesariamente son la mejor herramienta para plasmar un desarrollo general de eventos. En lugar de ello, ilustran tipos específicos de comportamiento —en particular, cambios de un estado a otro.

Los diagramas de estado representan principalmente estados y transiciones. Los estados se representan con rectángulos de esquinas redondeadas que se etiquetan con el nombre del estado. Las transiciones se marcan con flechas que fluyen de un estado a otro, mostrando cómo cambian los estados. A continuación podrás ver estos dos elementos en acción en un diagrama básico para la vida estudiantil. Nuestra [herramienta de diagramas UML](https://www.lucidchart.com/pages/examples/uml_diagram_tool) puede ayudarte a diseñar cualquier diagrama personalizado de máquina de estados.

!https://prod-files-secure.s3.us-west-2.amazonaws.com/117043f3-0b4b-44f8-8c43-6d7b267128c8/b7707a84-a017-4d6e-8602-ffdb2fcca2a6/state_diagram_basic_example-500x281.png

## Aplicaciones de los diagramas de estado

De forma similar a la mayoría de los diagramas UML, los diagramas de estado tienen diferentes usos. Las aplicaciones principales son las siguientes:

- 
    
    Representar objetos basados en eventos en un sistema reactivo.
    
- 
    
    Ilustrar escenarios de casos de uso en un contexto de negocios.
    
- 
    
    Describir cómo se mueve un objeto a través de diversos estados a lo largo de su existencia.
    
- 
    
    Mostrar el comportamiento general de una máquina de estados o el comportamiento de un conjunto relacionado de máquinas de estados.
    

Crear diagramas es rápido y sencillo con Lucidchart. Inicia una prueba gratuita hoy mismo para empezar a crear y colaborar.

[Crea un diagrama UML](https://lucid.app/es/pricing/lucidchart?anonId=0.68c0e0618ab4873c9d&sessionDate=2023-09-20T21%3A37%3A56.385Z&sessionId=0.0babcfe818ab4873ca0&type=discovery)

## Símbolos y componentes para diagramas de estados

Puedes incluir muchas figuras diferentes en un diagrama de estados, particularmente si eliges combinarlo con otro diagrama. Esta lista resume las figuras más comunes que puedes encontrar.

### Estado compuesto

Un estado que contiene subestados anidados. Ve el ejemplo siguiente de [diagrama de estados de universidad](https://www.lucidchart.com/pages/uml-state-machine-diagram#section-3). “Inscripción” es el estado compuesto en este ejemplo porque comprende diversos subestados en el proceso.

### Pseudoestado de opción

Un símbolo de diamante que indica una condición dinámica con resultados potenciales ramificados.

### Evento

Una instancia que activa una transición, etiquetada arriba de la flecha de transición aplicable. En este caso, "fin de clases" es el evento que activa el final del estado “Siendo instruidos” y el inicio del estado “Exámenes finales”.

!https://prod-files-secure.s3.us-west-2.amazonaws.com/117043f3-0b4b-44f8-8c43-6d7b267128c8/3273a542-38ab-449d-b766-d55438f65383/EventShape.png

### Punto de salida

El punto en el cual un objeto escapa el estado compuesto o máquina de estados, el cual se indica por medio de un círculo cruzado con una X. El punto de salida generalmente se usa si el proceso no está completado, pero tiene que ser escapado por algún error u otro problema.

### Primer estado

Un marcador para el primer estado en el proceso, que se muestra mediante un círculo oscuro con una flecha de transición.

### Protección

Una condición booleana que permite o detiene una transición. Se escribe arriba de la flecha de transición.

### Estado

Un rectángulo de esquinas redondeadas que indica la naturaleza actual de un objeto.

### Subestado

Un estado contenido dentro de la región de un estado compuesto. En el [diagrama de máquina de estados de universidad](https://www.lucidchart.com/pages/uml-state-machine-diagram#section-3) mostrado a continuación, “Abierto para inscripción” es un subestado en el estado compuesto más grande de “Inscripción”.

### Terminador

Un círculo con un punto en el interior que indica que un proceso está terminado.

### Transición

Una flecha que corre de un estado a otro, que indica un estado cambiante.

### Comportamiento transicional

Un comportamiento que resulta cuando un estado pasa por una transición. Se escribe arriba de la flecha de transición.

### Disparador

Un tipo de mensaje que mueve activamente un objeto de estado en estado. Se escribe arriba de la flecha de transición. En este ejemplo, “Problema con la reservación” es el disparador que enviaría a la persona a la agencia de viajes del aeropuerto en lugar de al siguiente paso en el proceso.

## Ejemplos de diagrama de estados

### Ejemplo de diagrama de estados de disponibilidad en calendario

Este ejemplo de diagrama de máquina de estados muestra el proceso por medio del cual una persona define una cita en su calendario. En el estado compuesto “Revisar fecha”, el sistema revisa el calendario en busca de disponibilidad en algunos subestados diferentes. Si no hay disponibilidad de tiempo en el calendario, el proceso es escapado. Sin embargo, si el calendario muestra disponibilidad, se agregará la cita al calendario.

### Ejemplo de diagrama de estados de universidad

Este diagrama de estados muestra el proceso de inscripción y clases en una universidad. El estado compuesto “Inscripción” se compone de diversos subestados que guían a los estudiantes a través del proceso de inscripción. Una vez que los estudiantes se han inscrito, pasan al estado “Siendo instruidos” y finalmente a “Exámenes finales”.

### Ejemplo de diagrama de estados de registro en aeropuerto

El siguiente ejemplo simplifica los pasos necesarios para registrarse en un aeropuerto. En el caso de las aerolíneas, un diagrama de estados puede ayudar a agilizar procesos y eliminar pasos innecesarios.
