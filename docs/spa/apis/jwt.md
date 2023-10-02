# **JWT**

**JSON Web Token** (**JWT**, pronunciado [/dʒɒt/](https://en.wikipedia.org/wiki/Help:IPA/English), igual que la palabra "jot") es un estándar de Internet propuesto para crear datos con firma opcional y/o cifrado opcional cuyo contenido sostiene JSON que afirma un número de reclamaciones. Los tokens son firmados ya sea usando un secreto privado o una clave pública/privada.

Por ejemplo, un servidor podría generar un token que tiene la reclamación "inició sesión como administrador" y proporcionárselo a un cliente. El cliente podría luego usar ese token para demostrar que ha iniciado sesión como administrador. Los tokens pueden ser firmados por la clave privada de una de las partes (generalmente la del servidor) de manera que cualquier otra parte pueda posteriormente verificar si el token es legítimo. Si la otra parte, por medios adecuados y confiables, está en posesión de la clave pública correspondiente, también podrá verificar la legitimidad del token. Los tokens están diseñados para ser compactos, seguros para URL y especialmente utilizables en un contexto de inicio de sesión único (SSO) en un navegador web. Las reclamaciones JWT pueden utilizarse típicamente para pasar la identidad de usuarios autenticados entre un proveedor de identidad y un proveedor de servicios, o cualquier otro tipo de reclamaciones requeridas por procesos comerciales.

JWT se basa en otros estándares basados en JSON: JSON Web Signature y JSON Web Encryption.

## Estructura

**Encabezado** Identifica qué algoritmo se utiliza para generar la firma. `HS256` indica que este token está firmado usando HMAC-SHA256. Los algoritmos criptográficos típicos utilizados son HMAC con SHA-256 (HS256) y RSA con SHA-256 (RS256). JWA (Algoritmos Web JSON) RFC 7518 introduce muchos más tanto para autenticación como para cifrado.

```
{
  "alg": "HS256",
  "typ": "JWT"
}
```

**Cuerpo** Contiene un conjunto de reclamaciones. La especificación de JWT define siete Nombres de Reclamaciones Registradas, que son los campos estándar comúnmente incluidos en los tokens. Las reclamaciones personalizadas generalmente también se incluyen, según el propósito del token. Este ejemplo tiene la reclamación estándar "Fecha de Emisión" (iat) y una reclamación personalizada ("loggedInAs").

```
{
  "loggedInAs": "admin",
  "iat": 1422779638
}
```

**Firma** Valida de manera segura el token. La firma se calcula codificando el encabezado y el cuerpo usando Codificación Base64url y concatenando ambos con un separador de puntos. Luego, esta cadena se somete al algoritmo criptográfico especificado en el encabezado. Este ejemplo utiliza HMAC-SHA256 con un secreto compartido (también se definen algoritmos de clave pública). La Codificación Base64url es similar a base64, pero utiliza caracteres no alfanuméricos diferentes y omite el relleno.

```
HMAC_SHA256(
  secreto,
  codificaciónBase64url(encabezado) + '.' +
  codificaciónBase64url(cuerpo)
)
```

Las tres partes se codifican por separado usando Codificación Base64url y se concatenan con puntos para producir el JWT:

```
const token = codificaciónBase64url(encabezado) + '.' + codificaciónBase64url(cuerpo) + '.' + codificaciónBase64url(firma)
```

El token resultante puede pasarse fácilmente a HTML y HTTP.

## Uso

En la autenticación, cuando el usuario inicia sesión con éxito utilizando sus credenciales, se devolverá un JSON Web Token que debe guardarse localmente (generalmente en almacenamiento local o de sesión, pero también pueden usarse cookies), en lugar del enfoque tradicional de crear una sesión en el servidor y devolver una cookie. Para procesos no supervisados, el cliente también puede autenticarse directamente generando y firmando su propio JWT con un secreto precompartido y pasándolo a un servicio compatible con OAuth de la siguiente manera:

```
POST /oauth2/token
Content-type: application/x-www-form-urlencoded

grant_type=urn:ietf:params:oauth:grant-type:jwt-bearer&assertion=eyJhb...
```

Si el cliente pasa una afirmación JWT válida, el servidor generará un access_token válido para realizar llamadas a la aplicación y lo devolverá al cliente:

```
{
  "access_token": "eyJhb...",
  "token_type": "Bearer",
  "expires_in": 3600
}
```

Cuando el cliente desea acceder a una ruta o recurso protegido, el agente de usuario debe enviar el JWT, generalmente en la cabecera HTTP de Autorización utilizando el esquema "Bearer". El contenido de la cabecera podría verse de la siguiente manera:

```
Authorization: Bearer eyJhbGci...<snip>...yu5CSpyHI
```

Este es un mecanismo de autenticación sin estado ya que el estado del usuario nunca se guarda en la memoria del servidor. Las rutas protegidas del servidor verificarán si hay un JWT válido en la cabecera de Autorización, y si está presente, se permitirá al usuario acceder a los recursos protegidos. Dado que los JWT son autocontenidos, toda la información necesaria está allí, reduciendo la necesidad de consultar la base de datos varias veces.

## Campos Estándar

| Código | Nombre | Descripción |
| --- | --- | --- |
| Campos de reclamación estándar |  | Los borradores de Internet definen los siguientes campos estándar ("reclamaciones") que pueden usarse dentro de un conjunto de reclamaciones JWT. |
| iss | Emisor | Identifica el principal que emitió el JWT. |
| sub | Sujeto | Identifica al sujeto del JWT. |
| aud | Audiencia | Identifica a los destinatarios para los que está destinado el JWT. Cada principal destinado a procesar el JWT debe identificarse con un valor en la reclamación de audiencia. Si el principal que procesa la reclamación no se identifica con un valor en la reclamación de audiencia cuando esta reclamación está presente, entonces el JWT debe ser rechazado. |
| exp | Tiempo de Expiración | Identifica el momento de expiración en el cual el JWT no debe ser aceptado para su procesamiento. El valor debe ser una Fecha Numérica: ya sea un número entero o decimal, que represente segundos desde Unix Time. |
| nbf | No Antes | Identifica el momento en el que el JWT comenzará a ser aceptado para su procesamiento. El valor debe ser una Fecha Numérica. |
| iat | Emitido en | Identifica el momento en que se emitió el JWT. El valor debe ser una Fecha Numérica. |
| jti | ID JWT | Identificador único, sensible a mayúsculas y minúsculas, del token, incluso entre diferentes emisores. |
| Campos de encabezado comúnmente utilizados |  | Los siguientes campos se utilizan comúnmente en el encabezado de un JWT |
| typ | Tipo de Token | Si está presente, debe establecerse en un tipo de medios registrado. |
| cty | Tipo de Contenido | Si se emplea el cifrado o firma anidados, se recomienda establecer esto en JWT; de lo contrario, omita este campo. |
| alg | Algoritmo de Código de Autenticación de Mensajes | El emisor puede establecer libremente un algoritmo para verificar la firma en el token. Sin embargo, algunos algoritmos admitidos son inseguros. |
| kid | ID de Clave | Una pista que indica qué clave utilizó el cliente para generar la firma del token. El servidor coincidirá este valor con una clave en el archivo para verificar que la firma es válida y el token es auténtico. |
| x5c | Cadena de Certificado x.509 | Una cadena de certificado en formato RFC4945 que corresponde a la clave privada utilizada para generar la firma del token. El servidor utilizará esta información para verificar que la firma es válida y el token es auténtico. |
| x5u | URL de Cadena de Certificado x.509 | Una URL desde la cual el servidor puede recuperar una cadena de certificado que corresponde a la clave privada utilizada para generar la firma del token. El servidor recuperará y utilizará esta información para verificar que la firma es auténtica. |
| crit | Crítico | Una lista de encabezados que deben ser entendidos por el servidor para aceptar el token como válido |

## Implementaciones

Existen implementaciones de JWT para muchos lenguajes y marcos, incluyendo, pero no limitado a:

- .NET (C# VB.Net, etc.)
- C
- Clojure
- Common Lisp
- Dart
- Elixir
- Erlang
- Go
- Haskell
- Java
- JavaScript
- Lua
- Node.js
- OCaml
- Perl
- PHP
- PL/SQL
- PowerShell
- Python
- Racket
- Raku
- Ruby
- Rust
- Scala
- Swift

## Vulnerabilidades

Los tokens JSON web pueden contener el estado de una sesión. Pero si los requisitos del proyecto permiten la invalidación de sesiones antes de la expiración del JWT, los servicios ya no pueden confiar en las afirmaciones del token por sí solos. Para validar que la sesión almacenada en el token no está revocada, las afirmaciones del token deben ser verificadas contra un almacén de datos. Esto hace que los tokens dejen de ser sin estado, socavando la principal ventaja de los JWT.

El consultor de seguridad Tim McLean informó de vulnerabilidades en algunas bibliotecas JWT que usaban el campo "alg" para validar incorrectamente los tokens, más comúnmente al aceptar un token "alg=none". Aunque estas vulnerabilidades fueron corregidas, McLean sugirió degradar por completo el campo "alg" para evitar confusiones de implementación similares. Aún así, se siguen encontrando nuevas vulnerabilidades "alg=none" en la naturaleza, con cuatro CVE presentados en el período 2018-2021 que tienen esta causa.

Con un diseño adecuado, los desarrolladores pueden abordar las vulnerabilidades del algoritmo tomando precauciones:

1. Nunca permitir que solo el encabezado JWT dirija la verificación.
2. Conocer los algoritmos (evitar depender solo del campo "alg").
3. Usar un tamaño de clave adecuado.
