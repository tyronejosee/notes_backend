# API

## ¿Qué es una API?

Las API son mecanismos que permiten a dos componentes de software comunicarse entre sí mediante un conjunto de definiciones y protocolos. Por ejemplo, el sistema de software del instituto de meteorología contiene datos meteorológicos diarios. La aplicación meteorológica de su teléfono “habla” con este sistema a través de las API y le muestra las actualizaciones meteorológicas diarias en su teléfono.

## ¿Qué significa API?

API significa “interfaz de programación de aplicaciones”. En el contexto de las API, la palabra aplicación se refiere a cualquier software con una función distinta. La interfaz puede considerarse como un contrato de servicio entre dos aplicaciones. Este contrato define cómo se comunican entre sí mediante solicitudes y respuestas. La documentación de su API contiene información sobre cómo los desarrolladores deben estructurar esas solicitudes y respuestas.

## ¿Cómo funcionan las API?

La arquitectura de las API suele explicarse en términos de cliente y servidor. La aplicación que envía la solicitud se llama cliente, y la que envía la respuesta se llama servidor. En el ejemplo del tiempo, la base de datos meteorológicos del instituto es el servidor y la aplicación móvil es el cliente.

Las API pueden funcionar de cuatro maneras diferentes, según el momento y el motivo de su creación.

### API de SOAP

Estas API utilizan el protocolo simple de acceso a objetos. El cliente y el servidor intercambian mensajes mediante XML. Se trata de una API menos flexible que era más popular en el pasado.

### API de RPC

Estas API se denominan llamadas a procedimientos remotos. El cliente completa una función (o procedimiento) en el servidor, y el servidor devuelve el resultado al cliente.

### API de WebSocket

La [API de WebSocket](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-websocket-api-overview?pg=wianapi&cta=websocketapi) es otro desarrollo moderno de la API web que utiliza objetos JSON para transmitir datos. La API de WebSocket admite la comunicación bidireccional entre las aplicaciones cliente y el servidor. El servidor puede enviar mensajes de devolución de llamada a los clientes conectados, por lo que es más eficiente que la API de REST.

### API de REST

Estas son las API más populares y flexibles que se encuentran en la web actualmente. El cliente envía las solicitudes al servidor como datos. El servidor utiliza esta entrada del cliente para iniciar funciones internas y devuelve los datos de salida al cliente. Veamos las API de REST con más detalle a continuación.

## ¿Qué son las API de REST?

REST significa transferencia de estado representacional. REST define un conjunto de funciones como GET, PUT, DELETE, etc. que los clientes pueden utilizar para acceder a los datos del servidor. Los clientes y los servidores intercambian datos mediante HTTP.

La principal característica de la [API de REST](https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api-vs-rest?pg=wianapi&cta=restapi) es que no tiene estado. La ausencia de estado significa que los servidores no guardan los datos del cliente entre las solicitudes. Las solicitudes de los clientes al servidor son similares a las URL que se escriben en el navegador para visitar un sitio web. La respuesta del servidor son datos simples, sin la típica representación gráfica de una página web.

## ¿Qué es una API web?

Una API web o API de servicios web es una interfaz de procesamiento de aplicaciones entre un servidor web y un navegador web. Todos los servicios web son API, pero no todas las API son servicios web. La API de REST es un tipo especial de API web que utiliza el estilo arquitectónico estándar explicado anteriormente.

Los diferentes términos relacionados con las API, como API de Java o API de servicios, existen porque históricamente las API se crearon antes que la World Wide Web. Las API web modernas son API de REST y los términos pueden utilizarse indistintamente.

## ¿Qué son las integraciones de las API?

Las integraciones de las API son componentes de software que actualizan automáticamente los datos entre los clientes y los servidores. Algunos ejemplos de integraciones de las API son la sincronización automática de datos en la nube desde la galería de imágenes de su teléfono o la sincronización automática de la hora y la fecha en su laptop cuando viaja a otra zona horaria. Las empresas también pueden utilizarlas para automatizar de manera eficiente muchas funciones del sistema.

![https://d1.awsstatic.com/whatisimg/New-API-GW-Diagram.c9fc9835d2a9aa00ef90d0ddc4c6402a2536de0d%20(1).67a41a2ef9823282fe672434ddd56dd22c13d5a5.png](https://d1.awsstatic.com/whatisimg/New-API-GW-Diagram.c9fc9835d2a9aa00ef90d0ddc4c6402a2536de0d%20(1).67a41a2ef9823282fe672434ddd56dd22c13d5a5.png)

## ¿Qué beneficios ofrecen las API de REST?

Las API de REST ofrecen cuatro beneficios principales:

### 1. Integración

Las API se utilizan para integrar nuevas aplicaciones con los sistemas de software existentes. Esto aumenta la velocidad de desarrollo, ya que no hay que escribir cada funcionalidad desde cero. Puede utilizar las API para aprovechar el código existente.

### 2. Innovación

Sectores enteros pueden cambiar con la llegada de una nueva aplicación. Las empresas deben responder con rapidez y respaldar la rápida implementación de servicios innovadores. Para ello, pueden hacer cambios en la API sin tener que reescribir todo el código.

### 3. Ampliación

Las API presentan una oportunidad única para que las empresas satisfagan las necesidades de sus clientes en diferentes plataformas. Por ejemplo, la API de mapas permite la integración de información de los mapas en sitios web, Android, iOS, etc. Cualquier empresa puede dar un acceso similar a sus bases de datos internas mediante el uso de API gratuitas o de pago.

### 4. Facilidad de mantenimiento

La API actúa como una puerta de enlace entre dos sistemas. Cada sistema está obligado a hacer cambios internos para que la API no se vea afectada. De este modo, cualquier cambio futuro que haga una de las partes en el código no afectará a la otra.

## ¿Cuáles son los diferentes tipos de API?

Las API se clasifican tanto en función de su arquitectura como de su ámbito de uso. Ya exploramos los principales tipos de arquitecturas de API, ahora veamos el ámbito de uso.

### API privadas

Estas son internas de una empresa y solo se utilizan para conectar sistemas y datos dentro de la empresa.

### API públicas

Están abiertas al público y pueden cualquier persona puede utilizarlas. Puede haber o no alguna autorización y coste asociado a este tipo de API.

### API de socios

Solo pueden acceder a ellas los desarrolladores externos autorizados para ayudar a las asociaciones entre empresas.

### API compuestas

Estas combinan dos o más API diferentes para abordar requisitos o comportamientos complejos del sistema.

## ¿Qué es un punto de conexión de la API y por qué es importante?

Los puntos de conexión de las API son los últimos puntos de contacto del sistema de comunicación de las API. Se trata de las URL de servidores, servicios y otras ubicaciones digitales específicas desde las que se envía y recibe información entre sistemas. Los puntos de conexión de las API son fundamentales para las empresas por dos motivos principales:

### 1. Seguridad

Los puntos de conexión de las API hacen que el sistema sea vulnerable a los ataques. La supervisión de las API es crucial para evitar su uso indebido.

### 2. Rendimiento

Los puntos de conexión de las API, especialmente los de alto tráfico, pueden provocar cuellos de botella y afectar al rendimiento del sistema.

## ¿Cómo proteger una API de REST?

Todas las API deben protegerse mediante una autenticación y una supervisión adecuadas. Las dos maneras principales de proteger las API de REST son las siguientes:

### 1. Tokens de autenticación

Se utilizan para autorizar a los usuarios a hacer la llamada a la API. Los tokens de autenticación comprueban que los usuarios son quienes dicen ser y que tienen los derechos de acceso para esa llamada concreta a la API. Por ejemplo, cuando inicia sesión en el servidor de correo electrónico, el cliente de correo electrónico utiliza tokens de autenticación para un acceso seguro.

### 2. Claves de API

Las claves de API verifican el programa o la aplicación que hace la llamada a la API. Identifican la aplicación y se aseguran de que tiene los derechos de acceso necesarios para hacer la llamada a la API en cuestión. Las claves de API no son tan seguras como los tokens, pero permiten supervisar la API para recopilar datos sobre su uso. Es posible que haya notado una larga cadena de caracteres y números en la URL de su navegador cuando visita diferentes sitios web. Esta cadena es una clave de la API que el sitio web utiliza para hacer llamadas internas a la API.

## ¿Cómo crear una API?

Se requiere la debida diligencia y esfuerzo para crear una API con la que otros desarrolladores quieran trabajar y en la que confíen. Los siguientes son los cinco pasos necesarios para un diseño de API de alta calidad:

### 1. Planificación de la API

Las especificaciones de la API, como OpenAPI, proporcionan el esquema para el diseño de su API. Es mejor pensar en los diferentes casos de uso por adelantado y asegurarse de que la API cumple con los estándares de desarrollo actuales.

### 2. Creación de la API

Los diseñadores de API crean prototipos de API mediante código reutilizable. Una vez probado el prototipo, los desarrolladores pueden personalizarlo a las especificaciones internas.

### 3. Prueba de la API

Las pruebas de la API son las mismas que las del software y deben hacerse para evitar errores y defectos. Las herramientas de pruebas de la API pueden utilizarse para reforzar la prueba de la API contra los ciberataques.

### 4. Documentación de la API

Aunque las API son explicativas, la documentación de las mismas sirve de guía para mejorar su uso. Las API bien documentadas que ofrecen una gama de funciones y casos de uso tienden a ser más populares en una arquitectura orientada a servicios.

### 5. Comercialización de la API

Así como Amazon es un mercado en línea para la venta minorista, los mercados de API existen para que los desarrolladores compren y vendan otras API. Publicar su API puede permitirle monetizarla.

## ¿Qué son las pruebas de API?

Las estrategias de pruebas de API son similares a otras metodologías de pruebas de software. El objetivo principal es validar las respuestas del servidor. Las pruebas de API incluyen lo siguiente:

- Hacer varias solicitudes a los puntos de conexión de la API para probar el rendimiento.
- Escribir pruebas de unidades para comprobar la lógica empresarial y la corrección funcional.
- Probar la seguridad mediante la simulación de ataques al sistema.

## ¿Cómo escribir la documentación de la API?

La escritura de la documentación completa de la API forma parte del [proceso de administración de la API](https://aws.amazon.com/api-gateway/api-management/?pg=wianapi&cta=apimgtprcs). La documentación de la API puede generarse automáticamente mediante herramientas o escribirse manualmente. Entre algunas de las prácticas recomendadas se encuentran las siguientes:

- Escribir las explicaciones en un inglés sencillo y fácil de leer. Los documentos generados por las herramientas pueden resultar farragosos y requerir su edición.
- Utilizar ejemplos de código para explicar la funcionalidad.
- Mantener la documentación para que sea precisa y esté actualizada.
- Orientar el estilo de escritura a los principiantes
- Cubrir todos los problemas que la API puede resolver por los usuarios.

## ¿Cómo utilizar una API?

Entre los pasos para implementar una nueva API se encuentran:

1. Obtener una clave de API. Esto se hace mediante la creación de una cuenta verificada con el proveedor de la API.
2. Configurar un cliente de API HTTP. Esta herramienta permite estructurar fácilmente las solicitudes de la API mediante las claves de la API recibidas.
3. Si no tiene un cliente de API, puede intentar estructurar la solicitud por su cuenta en su navegador. Para ello, consulte la documentación de la API.
4. Una vez que se acostumbre a la nueva sintaxis de la API, puede comenzar a utilizarla en su código.

## ¿Dónde puedo encontrar nuevas API?

Las nuevas API web se pueden encontrar en los sitios web y directorios de API. Los sitios web de API son plataformas abiertas en las que cualquiera puede poner a la venta una API. Los directorios de API son repositorios controlados y regulados por el propietario del directorio. Los diseñadores de API expertos pueden evaluar y probar una nueva API antes de agregarla a su directorio.

Entre algunos de los sitios web de API populares se encuentran los siguientes:

- Rapid API: el mayor sitio web global de API con más de 10 000 API públicas y 1 millón de desarrolladores activos en el sitio. RapidAPI permite a los usuarios probar las API directamente en la plataforma antes de confirmar su compra.
- Public APIs: la plataforma agrupa las API remotas en 40 categorías de nicho, lo que facilita la navegación y la búsqueda de la más adecuada para satisfacer sus necesidades.
- APIForThat y APIList: estos dos sitios web tienen listas de más de 500 API web, junto con información detallada sobre cómo utilizarlas.

## ¿Qué es una puerta de enlace de API?

Una puerta de enlace de API es una herramienta de administración de API para clientes empresariales que utilizan una amplia gama de servicios de backend. Las puertas de enlace de API suelen encargarse de tareas comunes, como la autenticación de usuarios, las estadísticas y la administración de tarifas que se aplican a todas las llamadas a las API.

[Amazon API Gateway](https://aws.amazon.com/api-gateway/?pg=wianapi&cta=amzapigtwy) es un servicio completamente administrado que facilita a los desarrolladores la creación, la publicación, el mantenimiento, la supervisión y la protección de las API a cualquier escala. Gestiona todas las tareas implicadas en la aceptación y el procesamiento de miles de llamadas a la API simultáneas, entre ellas, la administración del tráfico, la compatibilidad con CORS, el control de autorizaciones y acceso, la limitación controlada, la supervisión y la administración de versiones de la API.

## ¿Qué es GraphQL?

GraphQL es un lenguaje de consulta desarrollado específicamente para las API. Prioriza dar a los clientes exactamente los datos que solicitan y nada más. Está diseñado para que las API sean rápidas, flexibles y fáciles de desarrollar. Como alternativa a REST, GraphQL brinda a los desarrolladores de frontend la capacidad de consultar varias bases de datos, microservicios y las API con un solo punto de conexión de GraphQL. Las organizaciones eligen crear API con GraphQL porque les ayuda a desarrollar aplicaciones más rápidamente. [Obtenga más información sobre GraphQL aquí](https://aws.amazon.com/graphql/).

AWS AppSync es un servicio completamente administrado que facilita el desarrollo de API GraphQL al encargarse del trabajo pesado de conectarse de manera segura a orígenes de datos tales como AWS DynamoDB, AWS Lambda, etc. AWS AppSync puede enviar actualizaciones de datos en tiempo real a través de Websockets a millones de clientes. En el caso de las aplicaciones móviles y web, AppSync también proporciona acceso a los datos locales cuando los dispositivos se desconectan. Una vez implementada, AWS AppSync en automático escala y reduce verticalmente el motor de ejecución de las API de GraphQL para cumplir con los volúmenes de solicitudes de las API.
