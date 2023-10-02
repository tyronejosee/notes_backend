# Especificación OpenAPI

| Especificación OpenAPI |  |
| --- | --- |
| Año de inicio | 2010 |
| Primera publicación | 10 de agosto de 2011 |
| Última versión | 3.1.015 de febrero de 2021 |
| Sitio web | http://openapis.org/http://openapis.org/ |

La **Especificación OpenAPI**, anteriormente conocida como **Especificación Swagger**, es una especificación para un lenguaje de definición de interfaz legible por máquina para describir, producir, consumir y visualizar servicios web. Anteriormente parte del marco de trabajo Swagger, se convirtió en un proyecto separado en 2016, supervisado por la Iniciativa OpenAPI, un proyecto de colaboración de código abierto de la Fundación Linux.

Al tomar como entrada Swagger y algunas otras herramientas, se pueden generar código, documentación y casos de prueba a partir de archivos compatibles con la Especificación OpenAPI.

## Historia

El desarrollo de Swagger comenzó a principios de 2010 por Tony Tam, quien trabajaba en la empresa de diccionarios en línea Wordnik.

En marzo de 2015, SmartBear Software adquirió la especificación de API de código abierto Swagger de Reverb Technologies, la empresa matriz de Wordnik.

En noviembre de 2015, SmartBear anunció la creación de una nueva organización llamada la Iniciativa OpenAPI bajo el patrocinio de la Fundación Linux. Otras empresas fundadoras incluyeron 3scale, Apigee, Capital One, Google, IBM, Intuit, Microsoft, PayPal y Restlet. SmartBear donó la especificación Swagger al nuevo grupo. También se consideraron RAML y API Blueprint por parte del grupo.

El 1 de enero de 2016, la especificación Swagger cambió su nombre a Especificación OpenAPI (OAS) y se trasladó a un nuevo repositorio de GitHub.

En septiembre de 2016, la conferencia API World otorgó un premio de infraestructura API a SmartBear por su trabajo continuo en Swagger.

En julio de 2017, la Iniciativa OpenAPI lanzó la versión 3.0.0 de su especificación. MuleSoft, el principal contribuyente al lenguaje alternativo de modelado de API RESTful (RAML), se unió a la OAS y liberó su herramienta de marco de modelado de API como código abierto, lo que permite generar documentos OAS a partir de la entrada de RAML.

En febrero de 2021, la Iniciativa OpenAPI lanzó la versión 3.1.0 de la especificación. Los cambios principales en la Especificación OpenAPI 3.1.0 incluyen la alineación de vocabularios de esquema JSON, nuevos elementos de nivel superior para describir webhooks que se registran y gestionan fuera de banda, el soporte para identificar licencias de API utilizando el identificador SPDX estándar, la posibilidad de incluir descripciones junto con el uso de referencias de esquema y un cambio para que el objeto PathItems sea opcional para simplificar la creación de bibliotecas reutilizables de componentes.

## Fechas de lanzamiento

| Versión | Fecha | Notas |
| --- | --- | --- |
| 3.1.0 | 15 de febrero de 2021 | Lanzamiento de la Especificación OpenAPI 3.1.0 |
| 3.0.3 | 20 de febrero de 2020 | Lanzamiento de la Especificación OpenAPI 3.0.3 |
| 3.0.2 | 8 de octubre de 2018 | Lanzamiento de la Especificación OpenAPI 3.0.2 |
| 3.0.1 | 6 de diciembre de 2017 | Lanzamiento de la Especificación OpenAPI 3.0.1 |
| 3.0.0 | 26 de julio de 2017 | Lanzamiento de la Especificación OpenAPI 3.0.0 |
| 2.0 | 8 de septiembre de 2014 | Lanzamiento de Swagger 2.0 |
| 1.2 | 14 de marzo de 2014 | Lanzamiento inicial del documento formal |
| 1.1 | 22 de agosto de 2012 | Lanzamiento de Swagger 1.1 |
| 1.0 | 10 de agosto de 2011 | Primer lanzamiento de la Especificación Swagger |

## Uso

Las aplicaciones implementadas en base a archivos de interfaz OpenAPI pueden generar automáticamente documentación de métodos, parámetros y modelos de datos. Esto ayuda a mantener la documentación, las bibliotecas de cliente y el código fuente sincronizados.

Cuando se utiliza un documento OpenAPI para generar fragmentos de código fuente para servidores, el proceso se llama generación de estructuras.

## Relaciones con prácticas de ingeniería de software

El paradigma de acordar primero un contrato de API y luego programar la lógica empresarial, en contraste con codificar el programa primero y luego escribir una descripción retrospectiva de su comportamiento como contrato, se llama desarrollo orientado por contrato. Dado que la interfaz se determina antes de que se escriba cualquier código, los desarrolladores posteriores pueden simular el comportamiento del servidor y comenzar las pruebas de inmediato. En este sentido, el desarrollo orientado por contrato también es una práctica de pruebas de desplazamiento a la izquierda.

## Características

La Especificación OpenAPI es independiente del lenguaje. Con la especificación de recursos declarativos de OpenAPI, los clientes pueden comprender y consumir servicios sin conocimiento de la implementación del servidor ni acceso al código del servidor.

## Herramientas que funcionan con OpenAPI

La Iniciativa OpenAPI mantiene una lista de implementaciones para la versión 3.0 de la especificación. SmartBear todavía marca sus herramientas OpenAPI con el nombre Swagger. El marco Swagger UI permite a los desarrolladores y no desarrolladores interactuar con la API en una interfaz de usuario de sandbox que brinda información sobre cómo responde la API a los parámetros y opciones. Swagger puede manejar tanto JSON como XML.

Swagger Codegen contiene un motor impulsado por plantillas para generar documentación, clientes de API y fragmentos de servidor en diferentes lenguajes mediante el análisis de la definición de OpenAPI. En julio de 2018, William Cheng, el principal contribuyente a Swagger Codegen, y más de 40 otros colaboradores a Swagger Codegen bifurcaron el código en un proyecto llamado OpenAPI Generator bajo la organización OpenAPI Tools.

## Conferencia anual

La Iniciativa OpenAPI patrocina una Conferencia Anual de Especificaciones de API (ASC). El evento tiene sus orígenes en la Conferencia de Estrategia y Práctica de API (APIStrat) que se celebró durante muchos años y se convirtió en parte de la Iniciativa OpenAPI en 2016.
