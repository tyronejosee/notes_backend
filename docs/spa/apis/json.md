# JSON

**JSON** (acrónimo de **JavaScript Object Notation**, 'notación de objeto de JavaScript') es un formato de texto sencillo para el intercambio de datos. Se trata de un subconjunto de la notación literal de objetos de JavaScript, aunque, debido a su amplia adopción como alternativa a XML, se considera un formato independiente del lenguaje.

Una de las supuestas ventajas de JSON sobre XML como formato de intercambio de datos es que resulta mucho más sencillo escribir un analizador sintáctico (parser) para él. En JavaScript, un texto JSON se puede analizar fácilmente usando la función `eval()`, algo que (debido a la ubicuidad de JavaScript en casi cualquier navegador web) ha sido fundamental para que haya sido aceptado por parte de la comunidad de desarrolladores AJAX.

En la práctica, los argumentos a favor de la facilidad de desarrollo de analizadores o de sus rendimientos son poco relevantes, debido a las cuestiones de seguridad que plantea el uso de `eval()` y el auge del procesamiento nativo de XML incorporado en los navegadores modernos. Por esa razón, JSON se emplea habitualmente en entornos donde el tamaño del flujo de datos entre cliente y servidor es de vital importancia (de aquí su uso por Yahoo!, Google, Mozilla, etc, que atienden a millones de usuarios) cuando la fuente de datos es explícitamente de fiar y donde no es importante el hecho de no disponer de procesamiento XSLT para manipular los datos en el cliente.

Si bien se tiende a considerar JSON como una alternativa a XML, lo cierto es que no es infrecuente el uso de JSON y XML en la misma aplicación; así, una aplicación de cliente que integra datos de Google Maps con datos meteorológicos en SOAP (Simple Object Access Protocol) necesita hacer uso de ambos formatos.

En diciembre de 2005, Yahoo! comenzó a dar soporte opcional de JSON en algunos de sus servicios web.

## Nombre y pronunciación

En inglés, JSON se pronuncia de forma acrónima, como el nombre de la letra J (jay, /yéi/) seguido de la sílaba «son». El resultado habitual, con la primera sílaba tónica (/yéison/), se pronuncia igual que el nombre Jason, aunque Douglas Crockford, desarrollador del formato JSON, marca como tónica la segunda sílaba, como /yeisón/.

En español, hay que tener en cuenta que JSON es una sigla y que en ocasiones no hay una sola forma de pronunciarlas. Atendiendo a la norma ortográfica, lo normal sería pronunciarla como /jotasón/. Algunos lo pronuncian como /jasón/, pero se alejaría más de la pronunciación de la sigla introduciendo una letra más que no existe en la sigla (JASON) y por tanto sería una pronunciación incorrecta.

## Sintaxis

Los tipos de datos disponibles con JSON son:

- Números: Se permiten números negativos y opcionalmente pueden contener parte fraccional separada por puntos. Ejemplo: 123.456
- Cadenas: Representan secuencias de cero o más caracteres. Se ponen entre doble comilla y se permiten cadenas de escape. Ejemplo: `"Hola"`
- Booleanos: Representan valores booleanos y pueden tener dos valores: `true` y `false`
- null: Representan el valor nulo.
- Array: Representa una lista ordenada de cero o más valores los cuales pueden ser de cualquier tipo. Los valores se separan por comas y el vector se mete entre corchetes. Ejemplo `["juan","pedro","jacinto"]`
- Objetos: Son colecciones no ordenadas de pares de la forma `<nombre>:<valor>` separados por comas y puestos entre llaves. El nombre tiene que ser una cadena entre comillas dobles. El valor puede ser de cualquier tipo.

## Modelos de procesamiento

Al ser JSON un formato muy extendido para el intercambio de datos, se han desarrollado API para distintos lenguajes que permiten analizar sintácticamente, generar, transformar y procesar este tipo de dato.

Los modelos de programación más utilizados para tratar con JSON en los distintos lenguajes son:

- Modelo de objeto: El JSON completo es almacenado en memoria en un formato de árbol. Este árbol es navegado, analizado y modificado con las API apropiadas. Como lo carga todo en memoria y luego lo procesa este modelo consume muchos recursos. Sin embargo es muy flexible para manipular el contenido. Este modelo es permitido por ejemplo en Java por la JSR 353 y por la biblioteca Jackson.
- Modelo de flujo: Los datos son leídos o escritos en bloques. Por ejemplo, cada vez que se lee un bloque, el analizador genera eventos apropiados para indicar el tipo de bloque de que se trata. El cliente puede procesar el contenido escuchando los eventos apropiados. Además es el cliente el que decide como se va leyendo el JSON permitiendo parar o saltar contenidos en mitad del proceso. El proceso de escritura tiene propiedades análogas.
- Convirtiendo los objetos JSON en objetos del lenguaje. En Java esto es realizado por ejemplo por las bibliotecas Jackson y Gson.

## Uso de JSON

En teoría, es trivial analizar JSON en JavaScript usando la función `JSON.parse()` incorporada en el lenguaje. Por ejemplo:

`miObjeto = JSON.parse(json_datos);`

En la práctica, las consideraciones de seguridad por lo general recomiendan no usar `eval()` sobre datos crudos y debería usarse un analizador JavaScript distinto para garantizar la seguridad. El analizador proporcionado por JSON.org usa `eval()` en su función de análisis, protegiéndola con una expresión regular de forma que la función sólo ve expresiones seguras.

Un ejemplo de acceso a datos JSON usando XMLHttpRequest es:

```javascript
var http_request = new XMLHttpRequest();
var url = "http://example.net/jsondata.php";
http_request.onreadystatechange = handle_json;
http_request.open("GET", url, true);
http_request.send(null);

function handle_json() {
  if (http_request.readyState == 4) {
    if (http_request.status == 200) {
      var json_data = http_request.responseText; 
      var the_object = eval("(" + json_data + ")");
    } else {
      alert("Ocurrió un problema con la URL.");
    }
    http_request = null;
  }
}
```

Obsérvese que el uso de XMLHttpRequest en este ejemplo no es compatible con todos los navegadores, ya que existen variaciones sintácticas para Internet Explorer, Opera, Safari, y navegadores basados en Mozilla.

También es

 posible usar elementos `<iframe>` ocultos para solicitar los datos de manera asíncrona, o usar peticiones `<form target="url_to_cgi_script" />`. Estos métodos eran los más habituales antes del advenimiento del uso generalizado de XMLHttpRequest.

Hay una biblioteca para el framework .NET que exporta clases .NET con la sintaxis de JSON para la comunicación entre cliente y servidor, en ambos sentidos.

## Ejemplo de JSON

A continuación se muestra un ejemplo simple de definición de barra de menús usando JSON y XML.

JSON:

```json
{
    "menu": {
        "id": "file",
        "value": "File",
        "popup": {
            "menuitems": [
                {
                    "value": "New", "onclick": "CreateNewDoc()"
                },{
                    "value": "Open", "onclick": "OpenDoc()"
                },{
                    "value": "Close", "onclick": "CloseDoc()"
                }
            ]
        }
    }
}
```

Es una posible representación JSON del siguiente XML:

```xml
<menu id="file" value="File">
    <popup>
        <menuitem value="New" onclick="CreateNewDoc()" />
        <menuitem value="Open" onclick="OpenDoc()" />
        <menuitem value="Close" onclick="CloseDoc()" />
    </popup>
</menu>
```

## Comparación con XML y otros lenguajes de marcado

Hay muchos analizadores JSON en el lado del servidor, existiendo al menos un analizador para la mayoría de los entornos. En algunos lenguajes, como Java o PHP, hay diferentes implementaciones donde escoger. En JavaScript, el análisis es posible de manera nativa con la función `JSON.parse()`. Ambos formatos carecen de un mecanismo para representar grandes objetos binarios.

Con independencia de la comparación con XML, JSON puede ser muy compacto y eficiente si se usa de manera efectiva. Por ejemplo, la aplicación DHTML de búsqueda en "BarracudaDrive" recibe los listados de directorio como JSON desde el servidor. Esta aplicación de búsqueda está permanentemente consultando al servidor por nuevos directorios, y es notablemente rápida, incluso sobre una conexión lenta.

Los entornos en el servidor normalmente requieren que se incorpore una función u objeto analizador de JSON. Algunos programadores, especialmente los familiarizados con el lenguaje C, encuentran JSON más natural que XML, pero otros desarrolladores encuentran su escueta notación algo confusa, especialmente cuando se trata de datos fuertemente jerarquizados o anidados muy profundamente.

Hay más comparaciones entre JSON y XML en JSON.org.

YAML es un superconjunto de JSON que trata de superar algunas de las limitaciones de este. Aunque es significativamente más complejo, aún puede considerarse como ligero. El lenguaje de programación Ruby utiliza YAML como el formato de serialización por defecto, por lo que es posible manejar JSON con bastante sencillez.
