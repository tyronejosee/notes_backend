# OpenID

![OpenID Logo](assets/../../../../assets/images/openid.svg)

**OpenID** es un estándar de identificación digital descentralizado, con el que un usuario puede identificarse en una página web a través de una URL (o un XRI en la versión actual) y puede ser verificado por cualquier servidor que soporte el protocolo.

En los sitios que soporten OpenID, los usuarios no tienen que crearse una nueva cuenta de usuario para obtener acceso. En su lugar, solo necesitan disponer de un identificador creado en un servidor que verifique OpenID, llamado proveedor de identidad o IdP.

El proveedor de identidad puede confirmar la identificación OpenID del usuario a un sitio que soporte este sistema.

A diferencia de otras arquitecturas Single Sign-On, OpenId no especifica el mecanismo de autenticación. Por lo tanto, la seguridad de una conexión OpenId depende de la confianza que tenga el cliente OpenID en el proveedor de identidad. Si no existe confianza en el proveedor, la autenticación no será adecuada para servicios bancarios o transacciones de comercio electrónico, sin embargo el proveedor de identidad puede usar autenticación fuerte pudiendo ser usada para dichos fines.

OpenID está ganando fuerza debido al anuncio de algunos sitios grandes, como Technorati de la adopción de este sistema. El software MediaWiki cuenta con una extensión para permitir acceso por OpenID, pero de momento no se usa en los servidores de Wikipedia.

### Desarrollo

El sistema OpenID fue desarrollado originalmente por Brad Fitzpatrick de LiveJournal, aunque David Recordon de VeriSign, Josh Hoyt de JanRain y Dick Hardt de Sxip son ahora coautores. Las futuras especificaciones de OpenID serán desarrolladas en una meritocracia basadas en la lista de distribución. Para apoyar la implantación de OpenID, un grupo de empresas anunció en agosto de 2006 un programa de contribuciones de desarrollo, ofreciendo 5000$ a los primeros diez proyectos de software libre que implemente total compatibilidad con OpenID.

A partir de la versión 1.1, OpenID utiliza el protocolo de búsqueda de servicios Yadis. En diciembre de 2007 vio la luz la versión 2.0 de la Autenticación OpenID.

### Terminología

Un glosario básico de los términos usados con OpenID:

- **Usuario final**: la persona que quiere acceder con su identidad a un sitio.
- **Identificador**: la URL o XRI elegida por el usuario final como su identificador OpenID.
- **Proveedor de identidad**: Un proveedor de servicios que ofrece registro de URL o XRI OpenID y proveen autenticación OpenID.
- **Parte confidente**: el sitio que quiere verificar la identidad del usuario final.

### Cómo funciona OpenID

Un sitio web, como `example.com`, que desea ofrecer acceso a sus visitantes a través de OpenID, instala un formulario de identificación en alguna de sus páginas. A diferencia de los típicos formularios de identificación que preguntan al usuario por su nombre y contraseña, en este caso solamente existe un campo para el identificador OpenID. El sitio web puede optar por mostrar un pequeño logo OpenID junto al campo. Este formulario estará conectado a una implementación de la biblioteca cliente OpenID.

Si, por ejemplo, Alicia quiere acceder a `example.com` usando el identificador OpenID `alicia.proveedor-openid.org` que ella previamente ha registrado en el proveedor de identidad `proveedor-openid.org`, simplemente va a `example.com` y teclea `alicia.proveedor-openid.org` en la caja de identificación de OpenID. A partir de la versión 2.0 de la autenticación OpenID (y en algunas de las implementaciones de OpenID 1.1) Alicia también puede identificarse tecleando un i-nombre como `=example.alicia` o `=example.comunidad*alicia`.

Si el identificador es una URL, la primera cosa que debe realizar la parte (`example.com`) es transformarla a una forma canónica, del tipo `http://web.archive.org/web/http://alicia.proveedor-openid.org/`. Con OpenID 1.0, la parte confidente solicita entonces la página web situada en dicha URL y, vía una etiqueta HTML de enlace, descubre que el servidor del proveedor es, suponiéndose, `http://proveedor-openid.org/openid-auth.php`. También descubre si debe o no usar una identidad delegada (ver más abajo). A partir de OpenID 1.1, el cliente realiza el descubrimiento de estos datos solicitando el 'documento XRDS (también llamado 'documento Yadis') con el tipo de contenido `application/xrds+xml`, que puede estar disponible en dicha URL y que siempre estará disponible a través de una XRI.

Hay dos modos mediante los cuales la parte confidente puede comunicarse con el proveedor de identidad:

- `checkid_immediate`, el cual está orientado a la identificación automática y en el que toda comunicación entre los dos servidores se realiza como una tarea de fondo, sin que el usuario sea consciente de ello;
- `checkid_setup`, en el que el usuario se comunica directamente con el servidor proveedor usando el mismo navegador web que emplea para acceder al sitio de la parte confidente.

La segunda opción es más popular en la Web; también puede suceder que un `checkid_immediate` termine convirtiéndose en un `checkid_setup` si la operación no puede automatizarse.

En primer lugar, la parte confidente y el proveedor (opcionalmente) establecen un secreto compartido, que la parte confidente se encarga de almacenar. Si se emplea `checkid_setup`, la parte confidente redirige el navegador web del usuario hacia el proveedor. En el ejemplo, el navegador de Alicia sería redirigido a `proveedor-openid.org` de manera que Alicia pudiera autenticarse contra el proveedor.

El método de autenticación puede variar, pero normalmente un proveedor OpenID pide una contraseña (y entonces posiblemente almacena la sesión del usuario usando cookies, tal y como hacen muchos sitios con autenticación basada en contraseña). En caso de que Alicia no tenga una sesión activa en `proveedor-openid.org`, este le solicitará su contraseña. Una vez tenga la sesión abierta el servidor le preguntará acerca de la confianza que le ofrece `http://example.com/openid-retorno.php` (la página designada por `example.com` como destino al que el usuario debería volver tras completar la autenticación para recibir los detalles de su identidad). Si ella responde positivamente,

 la autenticación OpenID se considera exitosa y el navegador es redirigido a la página de retorno indicada con las credenciales otorgadas. Si Alicia decide no fiarse del sitio de la parte confidente, el navegador también será redirigido, pero se notificará del rechazo a la parte confidente, de manera que `example.com` como contrapartida se negará a autenticar a Alicia.

Sin embargo, el proceso de no ha terminado todavía porque en esta etapa, `example.com` no puede decidir si las credenciales recibidas realmente fueron recibidas desde `proveedor-openid.org`. Si ellos habían establecido previamente un secreto compartido, el consumidor puede validar el secreto compartido recibido con las credenciales que tuviese guardadas previamente. Cada consumidor es llamado con estado porque guarda el secreto compartido entre sesiones. En comparación, un consumidor sin estado o mudo deberá hacer una petición más a fondo (`check_authentication`) para asegurarse que los datos vinieron de verdad de `proveedor-openid.org`.

Después de que el identificador de Alicia haya sido verificado, ella será considerada registrada en `example.com` como `alicia.proveedor-openid.org`. El sitio puede entonces guardar la sesión o, si este es su primer registro, pedir a Alicia que introduzca información específica para `example.com` para terminar el registro.

### Fundación OpenID

La Fundación OpenID (en los Estados Unidos), así como su filial OpenID Europe, se crearon en 2007. Es una organización sin ánimo de lucro cuyo papel es la organización y el desarrollo del framework OpenID para la comunidad, así como administrar su propiedad intelectual.

### Identificadores OpenID

A partir de la versión 2.0 de la autenticación OpenID (y en algunas de las implementaciones de OpenID 1.1), hay dos tipos de identificadores: URLs y XRIs.

#### URLs

Hay dos formas de obtener una URL OpenId válida que pueda usarse para registrarse en todos los sitios que soporten OpenID.

1. Primero, usar una URL existente que tú controles (como tu blog o página personal), y si sabes editar HTML, podrás insertar las etiquetas (tags) OpenID apropiadas en el código siguiendo las instrucciones de las especificaciones de OpenID. Cabe comentar que usando un subdominio podrás hacer que tu OpenID sea más fácil de escribir, pero no es necesario.
2. Segundo, registrar tu identificador OpenID con un proveedor de identidades. Estos ofrecen la posibilidad de registrar URLs (habitualmente terceros niveles de dominio) configuradas automáticamente para utilizarse con servicios de autenticación OpenID.

#### XRIs

Los XRIs son un nuevo sistema de identificación en Internet, diseñado específicamente para identidades digitales de dominio cruzado. Los XRIs son de dos formas i-nombres e i-números que son habitualmente registrados simultáneamente como equivalentes. Los I-nombres son reasignables (parecidos a nombres de dominio), mientras que los i-números nunca son reasignados. Cuando un i-nombre XRI es usado como un identificador OpenID, este es resuelto inmediatamente por el i-número equivalente (el elemento CanonicalID de un documento XRDS). Este i-número es el identificador OpenID almacenado por la parte confidente. De esta manera el usuario y la parte confidente están protegidos contra los cambios de identidad que podrían suceder con una URL basada en un nombre DNS reasignable.

### Críticas

OpenID ha recibido numerosas críticas de base, relativas a problemas desde distintos ámbitos, pero en especial de seguridad y privacidad. La unificación de todas las identidades conlleva altos riesgos, unido a que el servidor de identidad conocerá todas las webs que se visiten cada día. Es más, si se comprometiera la seguridad del ordenador usuario o del servidor, toda la vida digital del usuario quedaría desprotegida.
