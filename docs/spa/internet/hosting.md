# Hosting

El término "servidor web" puede referirse al hardware, al software o a ambos trabajando juntos.

1. En el lado del hardware, un servidor web es una computadora que almacena software de servidor web y los archivos de componentes de un sitio web (por ejemplo, documentos HTML, imágenes, hojas de estilo CSS y archivos JavaScript). Un servidor web se conecta a Internet y admite el intercambio de datos físicos con otros dispositivos conectados a la web.
2. En el lado del software, un servidor web incluye varias partes que controlan cómo los usuarios web acceden a los archivos alojados. Como mínimo, esto es un "servidor HTTP". Un servidor HTTP es un software que comprende las URL (direcciones web) y el HTTP (el protocolo que utiliza tu navegador para ver páginas web). Un servidor HTTP se puede acceder a través de los nombres de dominio de los sitios web que almacena, y entrega el contenido de estos sitios web alojados al dispositivo del usuario final.

En el nivel más básico, cada vez que un navegador necesita un archivo alojado en un servidor web, el navegador solicita el archivo a través de HTTP. Cuando la solicitud llega al servidor web correcto (hardware), el servidor HTTP (software) acepta la solicitud, encuentra el documento solicitado y lo envía de vuelta al navegador, también a través de HTTP. (Si el servidor no encuentra el documento solicitado, devuelve una respuesta 404 en su lugar).

Para publicar un sitio web, necesitas un servidor web estático o dinámico.

Un **servidor web estático**, o conjunto, consta de una computadora (hardware) con un servidor HTTP (software). Lo llamamos "estático" porque el servidor envía sus archivos alojados tal como están a tu navegador.

Un **servidor web dinámico** consta de un servidor web estático más software adicional, comúnmente un "servidor de aplicaciones" y una "base de datos". Lo llamamos "dinámico" porque el servidor de aplicaciones actualiza los archivos alojados antes de enviar el contenido a tu navegador a través del servidor HTTP.

Por ejemplo, para producir las páginas web finales que ves en el navegador, el servidor de aplicaciones podría llenar una plantilla HTML con contenido de una base de datos. Sitios como MDN o Wikipedia tienen miles de páginas web. Típicamente, este tipo de sitios están compuestos por solo algunas plantillas HTML y una base de datos gigante, en lugar de miles de documentos HTML estáticos. Esta configuración facilita el mantenimiento y la entrega del contenido.

Para revisar: para obtener una página web, tu navegador envía una solicitud al servidor web, que busca el archivo solicitado en su propio espacio de almacenamiento. Al encontrar el archivo, el servidor lo lee, lo procesa según sea necesario y lo envía al navegador. Veamos esos pasos con más detalle.

### Almacenamiento de archivos

Primero, un servidor web debe almacenar los archivos del sitio web, es decir, todos los documentos HTML y sus activos relacionados, incluyendo imágenes, hojas de estilo CSS, archivos JavaScript, fuentes y videos.

Técnicamente, podrías alojar todos esos archivos en tu propia computadora, pero es mucho más conveniente almacenar los archivos en un servidor web dedicado porque:

- Un servidor web dedicado suele estar más disponible (encendido y funcionando).
- Excluyendo el tiempo de inactividad y los problemas del sistema, un servidor web dedicado siempre está conectado a Internet.
- Un servidor web dedicado puede tener la misma dirección IP todo el tiempo. Esto se conoce como una "dirección IP dedicada". (No todos los proveedores de servicios de Internet proporcionan una dirección IP fija para líneas de hogar).
- Un servidor web dedicado suele ser mantenido por un tercero.

Por todas estas razones, encontrar un buen proveedor de alojamiento es una parte clave de la construcción de tu sitio web. Examina los diversos servicios que ofrecen las empresas. Elige uno que se adapte a tus necesidades y presupuesto. (Los servicios van desde gratuitos hasta miles de dólares al mes). Puedes encontrar más detalles en este artículo.

Una vez que tengas el servicio de alojamiento web, debes subir tus archivos a tu servidor web.

### Comunicación a través de HTTP

En segundo lugar, un servidor web proporciona soporte para HTTP (Protocolo de transferencia de hipertexto). Como su nombre indica, HTTP especifica cómo transferir hipertexto (documentos web vinculados) entre dos computadoras.

Un protocolo es un conjunto de reglas para la comunicación entre dos computadoras. HTTP es un protocolo textual y sin estado.

Textual: Todas las órdenes son en texto plano y legibles por humanos.
Sin estado: Ni el servidor ni el cliente recuerdan comunicaciones anteriores. Por ejemplo, basándose únicamente en HTTP, un servidor no puede recordar una contraseña que escribiste ni tu progreso en una transacción incompleta. Necesitas un servidor de aplicaciones para tareas como esas. (Cubriremos ese tipo de tecnología en otros artículos).

HTTP establece reglas claras sobre cómo se comunican un cliente y un servidor. Cubriremos HTTP en un artículo técnico más adelante. Por ahora, simplemente ten en cuenta estas cosas:

- Normalmente, solo los clientes hacen solicitudes HTTP, y solo a servidores. Los servidores responden a la solicitud HTTP de un cliente. Un servidor también puede poblar datos en una caché del cliente, antes de que se solicite, mediante un mecanismo llamado "push del servidor".
- Al solicitar un archivo a través de HTTP, los clientes deben proporcionar la URL del archivo.
- El servidor web debe responder a cada solicitud HTTP, al menos con un mensaje de error.

En un servidor web, el servidor HTTP es responsable de procesar y responder a las solicitudes entrantes.

1. Al recibir una solicitud, un servidor HTTP verifica si la URL solicitada coincide con un archivo existente.
2. Si es así, el servidor web envía el contenido del archivo de vuelta al navegador. Si no, el servidor verificará si debe generar un archivo dinámicamente para la solicitud (ver Contenido estático vs. dinámico).
3. Si ninguna de estas opciones es posible, el servidor web devuelve un mensaje de error al navegador, comúnmente "404 No encontrado". El error 404 es tan común que algunos diseñadores web dedican tiempo y esfuerzo considerable a diseñar páginas de error 404.

### Contenido estático vs. dinámico

Hablando en términos generales, un servidor puede servir contenido estático o dinámico. Recuerda que el término "estático" significa "servido tal como está". Los sitios web estáticos son los más fáciles de configurar, por lo que sugerimos que tu primer sitio sea un sitio estático.

El término "dinámico" significa que el servidor procesa el contenido o incluso lo genera sobre la marcha desde una base de datos. Este enfoque proporciona más flexibilidad, pero la pila técnica es más compleja, lo que hace que construir un sitio web sea mucho más desafiante.

Es imposible sugerir un único servidor de aplicaciones listo para usar que sea la solución adecuada para todos los casos de uso posibles. Algunos servidores de aplicaciones están diseñados para alojar y gestionar blogs, wikis o soluciones de comercio electrónico, mientras que otros son más genéricos. Si estás construyendo un sitio web dinámico, tómate el tiempo para investigar tus requisitos y encontrar la tecnología que mejor se adapte a tus necesidades.

La mayoría de los desarrolladores de sitios web no necesitarán crear un servidor de aplicaciones desde cero, porque hay muchas soluciones listas para usar, muchas de las cuales son altamente configurables. Pero si necesitas crear tu propio servidor, probablemente querrás usar un marco de servidor, aprovechando su código y bibliotecas existentes, y extendiendo solo las partes que necesitas para cumplir con tu caso de uso. Solo un número relativamente pequeño de desarrolladores debería necesitar desarrollar un servidor completamente desde cero, por ejemplo, para cumplir con restricciones de recursos en un sistema integrado. Si deseas experimentar con la creación de un servidor, echa un vistazo a los recursos en la vía de aprendizaje de programación de sitios web del lado del servidor.
