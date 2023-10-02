# HATEOAS

**HATEOAS**, que en español significa "hipermedia como motor del estado de la aplicación," es un componente de la arquitectura de aplicaciones REST que la diferencia de otras arquitecturas.

Con HATEOAS, un cliente interactúa con una aplicación de red cuyos servidores de aplicación proporcionan información dinámicamente a través de hipermedia. Un cliente REST necesita poco o ningún conocimiento previo sobre cómo interactuar con una aplicación o servidor más allá de un conocimiento genérico de los hipermedia.

Por contraposición, clientes y servidores en el estándar CORBA interactúan a través de una interfaz fija compartida por medio de documentación o un lenguaje de descripción de interfaz (IDL).

Las restricciones impuestas por HATEOAS desacoplan el cliente del servidor. Esto permite a la funcionalidad del servidor evolucionar independientemente.

**Ejemplo**

Un cliente REST ingresa a una aplicación REST a través de una URL fija simple. Todas las acciones futuras que el cliente pueda realizar se descubren dentro de las representaciones de recursos devueltas por el servidor. Los tipos de medios utilizados para estas representaciones y las relaciones de enlace que pueden contener están estandarizados. El cliente realiza la transición a través de los estados de la aplicación seleccionando entre los enlaces dentro de una representación o manipulando la representación de otras formas que ofrece su tipo de medio. De esta manera, la interacción RESTful es impulsada por hipermedia, en lugar de información fuera de banda.

Por ejemplo, esta solicitud GET obtiene un recurso de cuenta, solicitando detalles en una representación JSON:

```
GET /accounts/12345 HTTP/1.1
Host: bank.example.com
Accept: application/vnd.acme.account+json
...
```

La respuesta es:

```
HTTP/1.1 200 OK
Content-Type: application/vnd.acme.account+json
Content-Length: ...

{
    "account": {
        "account_number": 12345,
        "balance": {
            "currency": "usd",
            "value": 100.00
        },
        "links": {
            "deposit": "/accounts/12345/deposit",
            "withdraw": "/accounts/12345/withdraw",
            "transfer": "/accounts/12345/transfer",
            "close": "/accounts/12345/close"
        }
    }
}
```

La respuesta contiene estos posibles enlaces de seguimiento: realizar un depósito, retiro o transferencia, o cerrar la cuenta. Cuando la información de la cuenta se recupera más tarde, la cuenta está sobregirada:

```
HTTP/1.1 200 OK
Content-Type: application/vnd.acme.account+json
Content-Length: ...

{
    "account": {
        "account_number": 12345,
        "balance": {
            "currency": "usd",
            "value": -25.00
        },
        "links": {
            "deposit": "/accounts/12345/deposit"
        }
    }
}
```

Ahora solo hay un enlace disponible: depositar más dinero. En su estado actual, los otros enlaces no están disponibles. De ahí el término "Motor de estado de aplicación," ya que las acciones que son posibles varían a medida que varía el estado del recurso.

Un cliente no necesita comprender todos los tipos de medios y mecanismos de comunicación que ofrece el servidor. La capacidad de comprender nuevos tipos de medios se puede adquirir en tiempo de ejecución a través del "código bajo demanda" que el servidor proporciona al cliente.

**Orígenes**

La restricción HATEOAS es una parte esencial de la característica de "interfaz uniforme" de REST, como se define en la tesis doctoral de Roy Fielding. Fielding describe con más detalle el concepto en su blog. El propósito de parte del rigor de esta y otras restricciones REST, explica Fielding, es "el diseño de software en la escala de décadas: cada detalle está destinado a promover la longevidad del software y la evolución independiente". Muchas de las limitaciones se oponen directamente a la eficiencia a corto plazo. Desafortunadamente, las personas son bastante buenos en el diseño corto plazo, y por lo general horrible en el diseño a largo plazo".
