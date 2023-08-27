# Cross-Site Request Forgery (CSRF)

El CSRF (Cross-site request forgery o falsificación de petición en sitios cruzados) es un tipo de exploit malicioso de un sitio web en el que comandos no autorizados son transmitidos por un usuario en el cual el sitio web confía. Esta vulnerabilidad es conocida también por otros nombres como XSRF, enlace hostil, ataque de un clic, secuestro de sesión y ataque automático.

## Introducción

Un ataque CSRF fuerza al navegador web validado de una víctima a enviar una petición a una aplicación web vulnerable, la cual entonces realiza la acción elegida a través de la víctima. Al contrario que en los ataques XSS, los cuales explotan la confianza que un usuario tiene en un sitio en particular, el cross-site request forgery explota la confianza que un sitio tiene en un usuario en particular.

## Escenario

Las vulnerabilidades CSRF se conocen desde finales de 1990 y fueron nombradas como CSRF o XSRF por Peter Watkins en 2001. CSRF no se puede trazar porque es llevada a cabo por la dirección IP de un usuario legítimo. Esto puede llevar a confusión en investigaciones forenses, donde será necesaria la intervención de expertos en seguridad informática para determinar casos particulares de ataques CSRF. Los exploits de este tipo de ataque apenas se conocen públicamente; en el año 2007 hay unos pocos ejemplos bien documentados.

**Ejemplo**:

Un ejemplo muy clásico se da cuando un sitio web, llamémoslo "example1.com", posee un sistema de administración de usuarios. En dicho sistema, cuando un administrador se conecta y ejecuta el siguiente REQUEST GET, elimina al usuario de ID: "63": `http://example1.com/usuarios/eliminar/63`

Una forma de ejecutar la vulnerabilidad CSRF, se daría si otro sitio web, llamemos "example2.com", en su sitio web añade el siguiente código HTML: `<img src="http://example1.com/usuarios/eliminar/63">`

Cuando el usuario administrador (conectado en example1.com) navegue por este sitio atacante, su navegador web intentará buscar una imagen en la URL y al realizarse el REQUEST GET hacia esa URL eliminará al usuario 63.
