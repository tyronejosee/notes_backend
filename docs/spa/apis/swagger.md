# Swagger

- **Desarrollador(es)**: Tony Tam, SmartBear Software
- **Lanzamiento**: 2011
- **Tipo**: Software para APIs Restful
- **Licencia**: Apache 2.0
- **Página**: [https://swagger.io/](https://swagger.io/)
- **Documentación**: [https://swagger.io/docs/](https://swagger.io/docs/)
- **Repositorio**: [https://github.com/OAI/OpenAPI-Specification](https://github.com/OAI/OpenAPI-Specification)

Swagger es un conjunto de herramientas de software de código abierto para diseñar, construir, documentar, y utilizar servicios web RESTful. Fue desarrollado por SmartBear Software e incluye documentación automatizada, generación de código, y generación de casos de prueba.

## Historia

El proyecto Swagger API fue creado en 2011 por Tony Tam, 2​ cofundador técnico del sitio de diccionarios Wordnik. Durante el desarrollo de los productos de Wordnik, la necesidad de automatizar la documentación API y la generación de SDK cliente se convirtió en una fuente importante de frustración. Tam diseñó una representación JSON simple de la API, basándose en la flexibilidad del estilo de arquitectura REST y utilizando muchas características de las herramientas creadas para el protocolo SOAP. El concepto de interfaz de usuario fue propuesto por Ayush Gupta, quien sugirió que una interfaz de usuario interactiva beneficiaría a los usuarios finales que desearan "probar" y desarrollar con la API.3​ Ramesh Pidikiti dirigió la implementación del generador de código inicial y el diseñador/desarrollador Zeke Sikilianos aportó el nombre Swagger. El proyecto de la API Swagger se hizo de código abierto en septiembre de 2011. Poco después del lanzamiento, se agregaron varios componentes nuevos al proyecto, incluido un validador independiente, soporte para Node.js y Ruby on Rails.

En los primeros años de Swagger, la tracción modesta provino de pequeñas empresas y desarrolladores independientes. Las API RESTful generalmente no tenían un mecanismo de descripción legible por máquina, y Swagger proporcionó una forma simple y visible de hacerlo. Tam fue invitado a una reunión con algunos de los líderes de opinión de la industria de las API, incluidos John Musser (ProgrammableWeb), Marsh Gardiner (Apigee, ahora un producto de Google), Marco Palladino (Kong) y Kin Lane para discutir un esfuerzo de estandarización en torno a las descripciones de API. Si bien la reunión no arrojó un plan concreto para hacerlo, puso a Swagger en el mapa como una innovación crítica en el espacio API.

Con la ayuda del uso de la licencia de código abierto Apache 2.0, varios productos y servicios en línea comenzaron a incluir Swagger en sus ofertas, que se aceleraron rápidamente después de la adopción por parte de Apigee, Intuit, Microsoft, IBM y otros que comenzaron a respaldar públicamente el proyecto Swagger.

Poco después de la creación de Swagger, se introdujeron estructuras alternativas para describir las API RESTful, siendo la más popular API Blueprint en abril de 2013 y RAML en septiembre de 2013. Si bien estos productos de la competencia tenían un respaldo financiero más sólido que Swagger, inicialmente se enfocaron en diferentes casos de uso de Swagger y, a mediados de 2014, el interés de Swagger estaba creciendo más rápidamente que la combinación de los otros dos.

En noviembre de 2015, SmartBear Software, la compañía que mantenía Swagger, anunció que estaba ayudando a crear una nueva organización, bajo el patrocinio de la Fundación Linux, llamada OpenAPI Initiative. Varias empresas, incluidas Google, IBM y Microsoft, son miembros fundadores. 4​

El 1 de enero de 2016, la especificación Swagger pasó a llamarse Especificación OpenAPI y se trasladó a un nuevo repositorio de software en Github. 5​ Si bien la especificación en sí no se modificó, este cambio de nombre significó la división entre el formato de descripción de la API y las herramientas de código abierto.

En julio de 2017, las herramientas Swagger se descargaron más de 100.000 veces al día, según los repositorios de alojamiento Sonatype y npm.

## Usos Prácticos

### Desarrollar APIs

Al crear APIs, las herramientas Swagger se pueden usar para generar automáticamente un documento de API abierta basado en el código mismo. Esto incrusta la descripción de la API en el código fuente de un proyecto y se denomina informalmente desarrollo de API de código primero o ascendente.

Alternativamente, utilizando **Swagger Codegen**, los desarrolladores pueden desacoplar el código fuente del documento Open API y generar código de cliente y servidor directamente desde el diseño. Esto hace posible diferir el aspecto de codificación.

### Interactuar con las API

Con el proyecto Swagger Codegen, los usuarios finales generan SDK de cliente directamente desde el documento de OpenAPI, lo que reduce la necesidad de código de cliente generado por humanos. En agosto de 2017, el proyecto Swagger Codegen admitía más de 50 idiomas y formatos diferentes para la generación de SDK del cliente.

### Documentar APIs

Cuando se describe en un documento de OpenAPI, las herramientas de código abierto de Swagger pueden usarse para interactuar directamente con la API a través de la interfaz de usuario de Swagger. Este proyecto permite conexiones directamente a API en vivo a través de una interfaz de usuario interactiva basada en HTML. Las solicitudes se pueden realizar directamente desde la interfaz de usuario y las opciones exploradas por el usuario de la interfaz.
