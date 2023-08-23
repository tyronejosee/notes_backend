# Bróker de Mensajería

Un **bróker de mensajería** o **message broker** es un programa intermediario que traduce los mensajes de un sistema desde un lenguaje a otro, a través de un medio de telecomunicaciones.

## Patrón

Un bróker de mensajería es un patrón arquitectónico para la validación, la transformación y el ruteo de mensajes. Es un mecanismo mediador de la comunicación entre aplicaciones, permitiendo minimizar el grado de conocimiento mutuo que estas aplicaciones necesitan tener, para poder intercambiar mensajes, implementando así efectivamente su desacoplamiento.

El propósito del bróker es recibir los mensajes entrantes desde las aplicaciones y llevar a cabo determinadas acciones con ellas. He aquí algunos ejemplos de posibles acciones a emprender por parte del bróker:

- Rutear mensajes a una o más destinaciones distintas
- Transformar mensajes a una representación alternativa
- Realizar una agregación de mensajes, descomponer mensajes en varios mensajes componentes, reenviándolos a sus respectivos destinos, para posteriormente recomponer las respuestas en un único mensaje que será remitido al usuario
- Interactuar con un depósito externo para aumentar un mensaje o almacenarlo
- Invocar un servicio Web para consultar datos
- Responder a eventos o errores
- Proveer un ruteo de los mensajes basado en su contenido o en sus tópicos empleando el modelo de publica/suscribe

## Funcionalidad

Existen numerosos patrones de mensajería que pueden operar sin un bróker de mensajería. Un patrón que sí requiere la intervención de un bróker de mensajería es el de las colas de trabajos, es decir, colas de mensajería manejadas por múltiples receptores. Se requiere que tales colas tengan un mecanismo único y central de administración, transacción y generalmente también almacenamiento confiable.
