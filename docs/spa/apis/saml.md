# **Security Assertion Markup Language (SAML)**

**SAML** significa Language Lenguaje de Marcado de Declaraciones de Seguridad. Es un estándar basado en XML para el intercambio de datos de autenticación y autorización entre partes, especialmente entre un proveedor de identidad (IdP) y un proveedor de servicios (SP). En un sistema basado en SAML, un usuario solicita acceso a un recurso protegido. El proveedor de servicios solicita al proveedor de identidad autenticar al usuario y afirmar si se le otorga acceso al recurso.

### **Beneficios de SAML**

Algunas ventajas de utilizar SAML incluyen:

- Inicio de sesión único (SSO): Los usuarios pueden iniciar sesión una vez en el IdP y acceder a múltiples proveedores de servicios sin necesidad de autenticarse nuevamente.
- Mejora de la seguridad: Las contraseñas y las credenciales de usuario no necesitan almacenarse ni administrarse por parte del proveedor de servicios, lo que reduce los posibles vectores de ataque.
- Mayor eficiencia: Como los usuarios ya no necesitan mantener múltiples conjuntos de credenciales, la gestión del acceso se vuelve más fácil tanto para el usuario como para los administradores del sistema.
- Interoperabilidad: SAML permite que una amplia gama de aplicaciones funcionen juntas, independientemente de la tecnología o plataforma subyacente.

### **Componentes de SAML**

Tres componentes principales están involucrados en la arquitectura de SAML:

1. **Proveedor de Identidad (IdP)**: La entidad que administra las identidades de los usuarios y los autentica proporcionando tokens de seguridad, también llamados declaraciones.
2. **Proveedor de Servicios (SP)**: La entidad que proporciona un servicio (como una aplicación web o una API) y depende del proveedor de identidad para autenticar a los usuarios y otorgar o denegar acceso a los recursos.
3. **Usuario/Titular**: El usuario final que busca acceder al servicio proporcionado por el proveedor de servicios.

### **Flujo de Trabajo de SAML**

El proceso de autenticación de SAML consta de los siguientes pasos:

1. El usuario solicita acceso a un recurso protegido al proveedor de servicios.
2. Si el usuario aún no está autenticado, el proveedor de servicios genera y envía una solicitud de autenticación de SAML al proveedor de identidad.
3. El proveedor de identidad autentica al usuario (usando, por ejemplo, un nombre de usuario y contraseña, autenticación multifactor u otro método).
4. El proveedor de identidad construye una respuesta de SAML, que incluye detalles sobre el usuario y afirma si el usuario está autorizado para acceder al recurso solicitado.
5. La respuesta de SAML se envía de regreso al proveedor de servicios, generalmente a través del navegador web del usuario o el cliente de API.
6. El proveedor de servicios procesa la respuesta de SAML, extrae la información necesaria y otorga o deniega el acceso al usuario según la afirmación del proveedor de identidad.

Con SAML, puede simplificar la autenticación y autorización de usuarios en diversas aplicaciones y sistemas, lo que proporciona una mejor experiencia de usuario y mejora la seguridad general de su backend.
