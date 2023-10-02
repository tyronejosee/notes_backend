# gRPC

**gRPC** (**gRPC Llamadas a Procedimientos Remotos**) es un framework de alto rendimiento de código abierto y multiplataforma para llamadas a procedimientos remotos (RPC). Inicialmente, gRPC fue creado por **Google**, que utilizaba una infraestructura de RPC de propósito general llamada Stubby para conectar la gran cantidad de microservicios que se ejecutaban dentro y entre sus centros de datos desde aproximadamente 2001. En marzo de 2015, Google decidió construir la siguiente versión de Stubby y hacerla de código abierto. El resultado fue gRPC, que ahora es utilizado en muchas organizaciones además de Google para alimentar casos de uso que van desde microservicios hasta el "último tramo" de la computación (móvil, web e Internet de las cosas). Utiliza HTTP/2 para el transporte, Protocol Buffers como lenguaje de descripción de interfaz y proporciona características como autenticación, transmisión bidireccional, control de flujo, enlaces bloqueantes o no bloqueantes, y cancelación y tiempos de espera. Genera enlaces de cliente y servidor multiplataforma para muchos lenguajes. Los escenarios de uso más comunes incluyen la conexión de servicios en una arquitectura de estilo de microservicios o la conexión de clientes de dispositivos móviles a servicios backend.

El uso complejo de HTTP/2 por parte de gRPC hace que sea imposible implementar un cliente de gRPC en el navegador, en su lugar, requiere un proxy.

## Autenticación

gRPC admite el uso de Seguridad de la Capa de Transporte (TLS) y autenticación basada en tokens. La conexión a los servicios de Google debe utilizar TLS. Existen dos tipos de credenciales: credenciales de canal y credenciales de llamada. Para la autorización basada en tokens, gRPC proporciona Interceptor de Servidor y un Interceptor de Cliente.

## Codificación

gRPC utiliza Protocol Buffers para codificar datos. A diferencia de las API REST con JSON, tienen una especificación más estricta. Debido a tener una única especificación, gRPC elimina el debate y ahorra tiempo al desarrollador porque es consistente en todas las plataformas e implementaciones.

## Adopción

Varias organizaciones diferentes han adoptado gRPC, como Uber, Square, Netflix, IBM, CoreOS, Docker, CockroachDB, Cisco, Juniper Networks, Spotify, Zalando, Dropbox y Google como el desarrollador original.

El proyecto de código abierto u-bmc utiliza gRPC para reemplazar la Interfaz de Gestión de Plataforma Inteligente (IPMI). El 8 de enero de 2019, Dropbox anunció que la próxima versión de "Courier", su framework de RPC en el núcleo de su arquitectura orientada a servicios (SOA), se migraría para basarse en gRPC, principalmente porque se alineaba bien con sus frameworks de RPC personalizados existentes.

## Alternativas a gRPC

- Cap'n Proto
- Apache Thrift
- Apache Avro
- JSON-RPC
- XML-RPC
