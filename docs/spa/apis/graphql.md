# GraphQL

**GraphQL** es un lenguaje de consulta y manipulación de datos de código abierto para APIs y un motor de consulta.

GraphQL permite la obtención de datos de forma declarativa, donde un cliente puede especificar exactamente qué datos necesita de una API. En lugar de múltiples puntos finales que devuelven datos separados, un servidor GraphQL expone un solo punto de entrada y responde con precisión a los datos que el cliente solicitó. Debido a que un servidor GraphQL puede obtener datos de fuentes de datos separadas y presentar los datos en un gráfico unificado, no está vinculado a una base de datos o motor de almacenamiento específico.

## Historia

Facebook comenzó el desarrollo de GraphQL en 2012 y lo lanzó como código abierto en 2015. En 2018, GraphQL se trasladó a la recién establecida Fundación GraphQL, alojada por la Fundación Linux.

El 9 de febrero de 2018, el Lenguaje de Definición de Esquema de GraphQL (SDL) se convirtió en parte de la especificación.

Muchas API públicas populares adoptaron GraphQL como la forma predeterminada de acceder a ellas. Estas incluyen las API públicas de Facebook, Github, Yelp, Shopify y Google Directions API.

## Diseño

GraphQL admite la lectura, escritura (mutación) y suscripción a cambios en los datos (actualizaciones en tiempo real, comúnmente implementadas mediante WebSockets). Un servicio GraphQL se crea definiendo tipos con campos y proporcionando funciones para resolver los datos de cada campo. Los tipos y campos componen lo que se conoce como la definición del esquema. Las funciones que recuperan y mapean los datos se llaman resolutores.

Después de ser validada contra el esquema, una consulta GraphQL se ejecuta en el servidor. El servidor devuelve un resultado que refleja la forma de la consulta original, generalmente en formato JSON.

### Sistema de tipos

El tipo raíz de un esquema GraphQL, por defecto, contiene todos los campos que se pueden consultar. Otros tipos definen los objetos y campos que el servidor GraphQL puede devolver. Hay varios tipos base, llamados escalares, para representar cosas como cadenas, números e identificadores.

Los campos se definen como opcionales por defecto, y se puede usar un signo de exclamación al final para hacer que un campo sea obligatorio. Un campo puede definirse como una lista envolviendo el tipo del campo entre corchetes, por ejemplo, `autores: [String]`.

```json
type Query {
  currentUser: User
}

type User {
  id: ID!
  name: String!
}
```

### Consultas

Una consulta GraphQL define la forma exacta de los datos necesarios por el cliente.

```json
query CurrentUser {
  currentUser {
    name
    age
  }
}
```

Una vez validados y ejecutados por el servidor GraphQL, los datos se devuelven en la misma forma.

```json
{
  "currentUser": {
    "name": "Yash Bhavsar",
    "age": 23
  }
}
```

### Mutaciones

Una mutación GraphQL permite crear, actualizar o eliminar datos. Las mutaciones generalmente contienen variables, que permiten que los datos se pasen desde el cliente al servidor. La mutación también define la forma de los datos que se devolverán al cliente después de que se complete la operación.

```json
mutation CreateUser($name: String!, $age: Int!) {
  createUser(userName: $name, age: $age) {
    name
    age
  }
}
```

Las variables se pasan como un objeto con campos que coinciden con los nombres de las variables en la mutación.

```json
{
  "name": "Han Solo",
  "age": 42
}
```

Una vez que se completa la operación, el servidor GraphQL devolverá datos que coincidan con la forma definida por la mutación.

```json
{
  "data": {
    "createUser": {
      "name": "Han Solo",
      "age": 42
    }
  }
}
```

### Suscripciones

GraphQL también admite actualizaciones en vivo enviadas desde el servidor al cliente en una operación llamada suscripción. Nuevamente, el cliente define la forma de los datos que necesita cada vez que se realiza una actualización.

```json
subscription {
  newPerson {
    name
    age
  }
}
```

Cuando se realiza una mutación a través del servidor GraphQL que actualiza el campo asociado, los datos se envían a todos los clientes suscritos en el formato establecido mediante la suscripción.

```json
{
  "newPerson": {
    "name": "Jane",
    "age": 23
  }
}
```

### Comparación con otros lenguajes de consulta

GraphQL no proporciona un lenguaje de consulta de gráficos completo como SPARQL o incluso en dialectos de SQL que admiten el cierre transitivo. Por ejemplo, una interfaz GraphQL que informa sobre los padres de un individuo no puede devolver, en una sola consulta, el conjunto de todos sus ancestros.

## Pruebas

Las API de GraphQL se pueden probar manualmente o con herramientas automatizadas que emiten solicitudes de GraphQL y verifican la corrección de los resultados. También es posible generar pruebas automáticas de nuevas solicitudes mediante técnicas basadas en la búsqueda debido a un esquema tipado y capacidades de introspección.

Algunas de las herramientas de software utilizadas para probar implementaciones de GraphQL incluyen Postman, GraphiQL, Apollo Studio, GraphQL Editor y Step CI.
