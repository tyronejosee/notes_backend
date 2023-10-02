# Autenticación

La **autenticación** o **autentificación** es el acto o proceso de confirmar que algo (o alguien) es quien dice ser. A la parte que se identifica se le llama **probador**. A la parte que verifica la identidad se la llama **verificador**. Es habitual que el probador sea un usuario que quiere acceder a ciertos recursos y el verificador sea un sistema que protege el acceso a dichos recursos y tiene que verificar que el que accede sea un usuario que tiene permisos para acceder a esos recursos. Para poder tener autenticación es necesaria, como condición previa, la existencia de identidades biunívocamente identificadas de tal forma que se permita hacer la tarea

## Etapas

La autenticación o autentificación (palabra preferida por la RAE) o mejor dicho acreditación, en términos de seguridad de redes de datos, se puede considerar uno de los tres pasos fundamentales (AAA). Cada uno de ellos es, de forma ordenada:

- Autenticación. En la seguridad de ordenador, la autenticación es el proceso de intento de verificar la identidad digital del remitente de una comunicación como una petición para conectarse. El remitente autenticado puede ser una persona que usa un ordenador, un ordenador por sí mismo o un programa del ordenador. En un web de confianza, "autenticación" es un modo de asegurar que los usuarios son quien ellos dicen que son; que el usuario que intenta realizar funciones en un sistema está autorizado para hacerlo.
- Autorización. Proceso por el cual la red de datos autoriza al usuario identificado a acceder a determinados recursos de la misma.
- Auditoría, mediante la cual la red o sistemas asociados registran todos y cada uno de los accesos a los recursos que realiza el usuario autorizados o no.

A menudo, el problema de la autorización es idéntico al de la autenticación; muchos protocolos de seguridad extensamente adoptados estándar, regulaciones obligatorias, y hasta estatutos se basan en esta suposición. Sin embargo, el uso más exacto describe la autenticación como el proceso de verificar la identidad de una persona, mientras que la autorización es el proceso de verificación de que una persona conocida tiene la autoridad para realizar cierta operación. La autenticación, por lo tanto, debe preceder la autorización.

Para distinguir la autenticación de la autorización de término estrechamente relacionada, existen unas notaciones de taquigrafía, que son: A1 para la autenticación y A2 para la autorización, que se usan con cierta frecuencia. También existen los términos AuthN y AuthZ, que se usan en algunas comunidades.

## Tipos de autenticación

### **Autenticación de identidad**

Garantiza que los participantes en una comunicación son los que dicen ser. Es decir, es un proceso de demostración de identidad de una parte ante las demás, de una manera fehaciente.

### **Autenticación del origen de los datos**

Garantiza la autenticidad del origen de los datos, es decir, que provengan de donde deben provenir.

Los métodos de autenticación usados dependen de los que se utilizan para la verificación, y estos se dividen en cinco categorías:

- Sistemas basados en algo conocido. Ejemplo, una contraseña/password (Unix) o frase de contraseña/passphrase (PGP).
- Sistemas basados en algo poseído. Ejemplo, una tarjeta de identidad, una tarjeta inteligente (smartcard), un dispositivo usb tipo epass token, una tarjeta de coordenadas, una smartcard o un dongle criptográfico.
- Sistemas basados en una característica física del usuario o un acto involuntario del mismo. Por ejemplo, verificación de voz, verificación de escritura, verificación de huellas, verificación de patrones oculares.
- Sistemas basados en el comportamiento. Por ejemplo, la forma de teclear, de caminar, etcétera.
- Sistemas basados en la ubicación. Por ejemplo, el lugar, la dirección IP donde se realiza la acción, la hora específica, etcétera.

También puede ser

**Directa**

En el proceso de autenticación solo intervienen las partes interesadas o que se van a autenticar.

**Indirecta**

En el proceso interviene una tercera parte confiable que actúa como autoridad o juez, que avala la identidad de las partes involucradas.

**Unilateral**

Solo una parte se autentica ante la otra. La otra parte no se autentica ante la primera.

**Mutua**

Ambas partes deben autenticarse entre sí.

## Características de autenticación

Cualquier sistema de identificación ha de poseer unas determinadas características para ser viable:

- Ha de ser fiable con una probabilidad muy elevada (podemos hablar de tasas de fallo de en los sistemas menos seguros)....
- Económicamente factible para la organización (si su precio es superior al valor de lo que se intenta proteger, tenemos un sistema incorrecto).
- Soportar con éxito cierto tipo de ataques.
- Ser aceptable para los usuarios, que serán al fin y al cabo quienes lo utilicen.
- Respuesta inmediata, directa, inteligente, sencilla, ante cada situación.

## Mecanismo de autenticación

Artículo principal: Protocolo de identificación

Para autenticar, es necesario establecer un protocolo de comunicación entre las partes, de forma que la parte verificadora suele verificar que la parte que se identifica (habitualmente un usuario) efectivamente es quien dice que es. En general, el proceso de autenticación consta de los siguientes pasos:

1. El probador solicita acceso a un sistema.
2. El verificador solicita al usuario que se autentique.
3. El probador aporta las credenciales que le identifican y permiten verificar la autenticidad de la identificación.
4. El verificador valida según sus reglas si las credenciales aportadas son suficientes para dar acceso al usuario o no.

## Control de acceso

Un ejemplo familiar es el control de acceso. Un sistema informático supuesto para ser utilizado solamente por aquellos autorizados, debe procurar detectar y excluir el desautorizado. El acceso a él por lo tanto es controlado generalmente insistiendo en un procedimiento de la autentificación para establecer con un cierto grado establecido de confianza la identidad del usuario, por lo tanto concediendo esos privilegios como puede ser autor

ización, el acceso. Cada intento se sigue típicamente del almacenamiento de información relacionada en una auditoría, de tal modo que los encargados de sistema pueden determinar quién ha accedido a sus recursos y qué operaciones han realizado. 

## Autenticación multifactor

La autenticación multifactor (MFA) es un método de autenticación que requiere que un usuario proporcione dos o más formas de verificación de identidad antes de permitir el acceso a una aplicación, sistema o recurso. Los factores de autenticación se dividen generalmente en tres categorías:

1. **Algo que el usuario sabe**: Esto podría ser una contraseña, un PIN o una respuesta a una pregunta de seguridad.
2. **Algo que el usuario tiene**: Esto podría ser un teléfono móvil, una tarjeta de identificación o una tarjeta inteligente.
3. **Algo que el usuario es**: Esto se refiere a características biométricas como huellas dactilares, reconocimiento facial o escaneo de retina.

La autenticación multifactor proporciona un nivel adicional de seguridad porque incluso si un atacante conoce la contraseña de un usuario, todavía necesitaría acceso a otro factor de autenticación para obtener acceso.

## Conclusión

La autenticación es un componente crítico de la seguridad de la información y se utiliza para garantizar que los usuarios o sistemas sean quienes afirman ser antes de permitirles el acceso a recursos o sistemas. Hay varios tipos y mecanismos de autenticación disponibles, y la elección depende de los requisitos de seguridad y la conveniencia de un sistema en particular. La autenticación multifactor se ha vuelto cada vez más importante para mejorar la seguridad al requerir múltiples formas de verificación de identidad.
