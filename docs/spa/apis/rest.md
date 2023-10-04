# REST

La **transferencia de estado representacional** (en *representational state transfer*) o **REST** es un estilo de arquitectura software para sistemas distribuidos como la World Wide Web. El término se originó en el año 2000, en una tesis doctoral sobre la web escrita por Roy Fielding, uno de los principales autores de la especificación del protocolo HTTP y ha pasado a ser ampliamente utilizado por la comunidad de desarrollo.

## Historia

La Web empezó a ser de uso diario en 1993-4, cuando empezaron a estar disponibles sitios web para uso general. En ese momento, solo había una descripción fragmentada de la arquitectura web y había presión en la industria para acordar algún estándar para los protocolos de interfaz web. Por ejemplo, se habían agregado varias extensiones experimentales al protocolo de comunicación (HTTP) para admitir proxies y se estaban proponiendo más extensiones, pero existía la necesidad de una arquitectura web formal con la que evaluar el impacto de estos cambios.

Juntos, los grupos de trabajo del W3C y del IETF comenzaron a trabajar en la creación de descripciones formales de los tres estándares principales de la web: URI, HTTP y HTML. Roy Fielding estuvo involucrado en la creación de estos estándares (específicamente HTTP 1.0 y 1.1, y URI), y durante los siguientes seis años desarrolló el estilo arquitectónico REST, probando sus restricciones en los estándares de protocolo de la web y usándolo como un medio para definir mejoras arquitectónicas y para identificar desajustes arquitectónicos. Fielding definió REST en su disertación de doctorado de 2000 "Estilos arquitectónicos y el diseño de arquitecturas de software basadas en redes" en UC Irvine.

## Descripción

Si bien el término *REST* se refería originalmente a un conjunto de principios de arquitectura, en la actualidad se usa en el sentido más amplio para describir cualquier interfaz entre sistemas que utilice directamente HTTP para obtener datos o indicar la ejecución de operaciones sobre los datos, en cualquier formato (XML, JSON, etc) sin las abstracciones adicionales de los protocolos basados en patrones de intercambio de mensajes, como por ejemplo SOAP. Es posible diseñar sistemas de servicios web de acuerdo con el estilo arquitectural REST de Fielding y también es posible diseñar interfaces XMLHttpRequest de acuerdo con el estilo de llamada a procedimiento remoto (RPC), pero sin usar SOAP. Estos dos usos diferentes del término *REST* causan cierta confusión en las discusiones técnicas, aunque RPC no es un ejemplo de REST.

REST afirma que la web ha disfrutado de escalabilidad como resultado de una serie de diseños fundamentales clave:

- Un *protocolo cliente/servidor sin estado*: cada mensaje HTTP contiene toda la información necesaria para comprender la petición. Como resultado, ni el cliente ni el servidor necesitan recordar ningún estado de las comunicaciones entre mensajes. Sin embargo, en la práctica, muchas aplicaciones basadas en HTTP utilizan cookies y otros mecanismos para mantener el estado de la sesión (algunas de estas prácticas, como la reescritura de URLs, no son permitidas por REST)
- Un conjunto de *operaciones bien definidas* que se aplican a todos los recursos de información: HTTP en sí define un conjunto pequeño de operaciones, las más importantes son **POST**, **GET**, **PUT** y **DELETE**. Con frecuencia estas operaciones se equiparan a las operaciones CRUD en bases de datos (crear, leer, actualizar, borrar) que se requieren para la persistencia de datos, aunque POST no encaja exactamente en este esquema.
- Una *sintaxis universal* para identificar los recursos. En un sistema REST, cada recurso es direccionable únicamente a través de su URI.
- El *uso de hipermedios*, tanto para la información de la aplicación como para las transiciones de estado de la aplicación: la representación de este estado en un sistema REST son típicamente HTML o XML. Como resultado de esto, es posible navegar de un recurso REST a muchos otros, simplemente siguiendo enlaces sin requerir el uso de registros u otra infraestructura adicional.

## Recursos

Un concepto importante en REST es la existencia de recursos (elementos de información), que pueden ser accedidos utilizando un identificador global (un Identificador Uniforme de Recurso). Para manipular estos recursos, los componentes de la red (clientes y servidores) se comunican a través de una interfaz estánd

ar (generalmente HTTP) y utilizan métodos estándar (por ejemplo, GET, POST, PUT o DELETE) para realizar acciones en los recursos.

### Características clave de los recursos en REST:

- **Identificación**: Cada recurso se identifica de forma única mediante un URI (Identificador Uniforme de Recurso). Por ejemplo, una URL (Localizador Uniforme de Recurso) en la web es una forma común de representar un URI.

- **Manipulación**: Los recursos son manipulados mediante una serie de operaciones estándar, como GET (para obtener información), POST (para crear un nuevo recurso), PUT (para actualizar un recurso existente) y DELETE (para eliminar un recurso).

- **Representación**: Los recursos pueden tener múltiples representaciones, como HTML, XML o JSON. Estas representaciones son utilizadas para transmitir información entre el cliente y el servidor. Por ejemplo, un recurso puede tener una representación en HTML para ser visualizado en un navegador web y una representación en JSON para ser procesada por una aplicación móvil.

- **Estado**: Los recursos pueden tener estados diferentes en un momento dado. Por ejemplo, un recurso que representa un pedido en una tienda en línea puede tener estados como "pendiente", "enviado" o "entregado". Estos estados pueden cambiar a medida que se realizan operaciones en el recurso.

- **Enlaces**: Los recursos pueden contener enlaces a otros recursos relacionados. Estos enlaces permiten la navegación y la descubierta de recursos relacionados en la aplicación.

## Ventajas de REST

REST presenta varias ventajas como estilo arquitectónico:

- **Sencillez**: REST se basa en protocolos y estándares web ampliamente utilizados, como HTTP. Esto hace que sea fácil de entender y utilizar.

- **Escalabilidad**: Gracias a su naturaleza sin estado y su uso de URI como identificadores de recursos, REST es altamente escalable y puede manejar grandes cantidades de solicitudes y recursos.

- **Flexibilidad**: Los recursos pueden tener múltiples representaciones, lo que permite a las aplicaciones clientes elegir el formato de datos que prefieren (por ejemplo, JSON o XML).

- **Independencia de plataforma**: REST no está vinculado a ninguna plataforma o tecnología específica, lo que facilita la interoperabilidad entre sistemas heterogéneos.

- **Descubrimiento de recursos**: Los enlaces entre recursos permiten a las aplicaciones cliente descubrir y navegar por la aplicación de manera dinámica.

- **Caché**: HTTP, que es ampliamente utilizado en REST, admite el almacenamiento en caché de recursos, lo que puede mejorar el rendimiento y reducir la carga en el servidor.

## Desventajas de REST

A pesar de sus ventajas, REST también tiene algunas limitaciones y desventajas:

- **Complejidad de diseño**: Diseñar una API RESTful eficiente y coherente puede requerir una planificación y un diseño cuidadosos, especialmente en aplicaciones complejas.

- **Sobrecarga de ancho de banda**: En algunas situaciones, el uso de representaciones de recursos más grandes, como XML o JSON, puede generar una sobrecarga de ancho de banda en comparación con formatos binarios más compactos.

- **Rendimiento en tiempo real**: REST puede no ser la mejor opción para aplicaciones en tiempo real que requieren una comunicación de baja latencia.

- **Seguridad**: REST no proporciona un mecanismo de seguridad integrado, lo que significa que los desarrolladores deben implementar la seguridad por sí mismos, como autenticación y autorización.

## Ejemplos de uso de REST

REST se utiliza en una amplia variedad de aplicaciones y servicios web. Algunos ejemplos comunes de uso de REST incluyen:

- **API web**: Muchas empresas y servicios proporcionan APIs web RESTful que permiten a los desarrolladores acceder a sus datos y funcionalidades a través de HTTP. Ejemplos incluyen la API de Twitter, la API de Google Maps y la API de GitHub.

- **Sitios web y aplicaciones web**: Los sitios web y aplicaciones web utilizan REST para comunicarse con servidores y acceder a recursos como imágenes, videos y datos. Las páginas web a menudo hacen solicitudes AJAX a servicios REST para obtener o enviar datos sin necesidad de recargar la página completa.

- **Aplicaciones móviles**: Las aplicaciones móviles a menudo utilizan REST para comunicarse con servidores y sincronizar datos con servicios en la nube. Esto permite a las aplicaciones móviles acceder y compartir datos con otros dispositivos y plataformas.

- **IoT (Internet de las cosas)**: Los dispositivos IoT pueden utilizar REST para enviar y recibir datos a través de la web. Esto permite la monitorización y el control remoto de dispositivos IoT desde cualquier ubicación.

- **Microservicios**: En arquitecturas de microservicios, cada servicio suele exponer una API REST para comunicarse con otros servicios y aplicaciones. Esto facilita la escalabilidad y la independencia de los servicios.

## Conclusión

REST es un estilo arquitectónico popular y ampliamente utilizado en el diseño de sistemas distribuidos, especialmente en la World Wide Web. Proporciona una forma sencilla y escalable de acceder y manipular recursos a través de HTTP, lo que lo hace adecuado para una amplia variedad de aplicaciones y servicios. Sin embargo, es importante recordar que REST no es la única opción disponible y que el diseño de una API RESTful eficiente requiere un enfoque cuidadoso. Además, en algunos casos, otros estilos arquitectónicos, como GraphQL, pueden ofrecer ventajas específicas en términos de flexibilidad y rendimiento. La elección del estilo arquitectónico adecuado depende de los requisitos específicos de la aplicación y de las necesidades del proyecto.
