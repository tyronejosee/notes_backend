# Nginx

- **Desarrollador(es)**: Igor Sysoev
- **Lanzamiento**: 2004
- **Licencia**: BSD License
- **Escrito en**: C
- **Página**: [https://www.nginx.com/](https://www.nginx.com/)
- **Repositorio**: [https://hg.nginx.org/nginx](https://hg.nginx.org/nginx)

**Nginx** (pronunciado en inglés "ényin-ex", /ˈɛndʒɪn-ɛks/) es un servidor web/proxy inverso ligero de alto rendimiento y un proxy para protocolos de correo electrónico (IMAP/POP3).

Es software libre y de código abierto, licenciado bajo la Licencia BSD simplificada; también existe una versión comercial distribuida bajo el nombre de Nginx Plus. Es multiplataforma, por lo que corre en sistemas tipo Unix (GNU/Linux, BSD, Solaris, Mac OS X, etc.) y Windows.

El sistema es usado por una larga lista de sitios web conocidos, como: WordPress, Netflix, Hulu, GitHub, Ohloh, SourceForge, **Yapo.cl**, TorrentReactor y partes de Facebook (como el servidor de descarga de archivos zip pesados).

## Nombre

Su creador, Igor Sysoev, en su página personal desde 2009 escribe el nombre totalmente en minúsculas, mientras que el nombre de la empresa propietaria desde 2011 lo escribe totalmente en mayúsculas, lo cual se corresponde con el nombre que devuelve el encabezado HTTP en todas y cada una de las solicitudes de conexión con que inicia la visita de cada página web.

Para complicar más el asunto, el logotipo tiene caracteres tanto en mayúsculas como en minúsculas del alfabeto cirílico. No obstante, se ha logrado un consenso en denominar "nginx" al servidor web, "NGINX" a los productos y servicios derivados que maneja la empresa y "Nginx" para referirse a ambos en conjunto.

## Uso

Originalmente, Nginx fue desarrollado para satisfacer las necesidades de varios sitios web de Rambler que recibían unas 500 millones de peticiones al día en septiembre de 2008.

De acuerdo con el estudio de Netcraft, *Netcraft's Jul 2014 Web Server Survey*, nginx es el segundo servidor web más usado en dominios activos (14,35%) superando a Internet Information Server de Microsoft. Además, pasó la marca de ser usado en más de 100 millones de sitios. Para el 29 de mayo de 2018 en el informe actualizado para este mismo estudio, Nginx alcanzó los 359 millones de dominios servidos, a pesar de haber perdido 44 millones con respecto al mes anterior.

En febrero de 2017, la adopción de Nginx fue:

- Argentina: 24,94% del total de dominios.
- España: 11,51% del total de dominios.
- México: 13.10% del total de dominios.
- Chile: 20,44% del total de dominios.
- Colombia: 16,03% del total de dominios.

## Nginx vs Nginx Plus

Hay dos versiones de Nginx, OSS Nginx y Nginx Plus. Nginx Plus ofrece funcionalidades adicionales que no son incluidas en OSS Nginx, como por ejemplo Active Health Checks, persistencia de sesión basada en cookies, integración del servicio de descubrimiento DNS, Api de Purgación de Caché, AppDynamic, Datalog, plug-ins de Dynatrace y New Relic, almacén clave-valor, entre otras características.

## Comparación con Apache

Nginx fue inicialmente desarrollado con el fin explícito de superar el rendimiento ofrecido por el servidor web Apache. Sirviendo archivos estáticos, Nginx usa dramáticamente menos memoria que Apache, y puede manejar aproximadamente cuatro veces más solicitudes por segundo. Este aumento de rendimiento viene con un costo de disminuida flexibilidad, como por ejemplo la capacidad de anular las configuraciones de acceso del sistema por archivo (Apache logra esto con un archivo .htaccess, mientras que Nginx no tiene desarrollada tal funcionalidad). Anteriormente, incorporar módulos de terceros en Nginx requería recompilar la aplicación fuente con los módulos enlazados estáticamente. Esto fue parcialmente superado en la versión 1.9.11 de febrero de 2016, con la adición de carga dinámica de módulos. Sin embargo, los módulos aun deben ser compilados al mismo tiempo que Nginx, y no todos los módulos son compatibles con este sistema; algunos requieren el antiguo proceso de enlazado estático.

## Características Básicas del Servidor Web

- Servidor de archivos estáticos, índices y autoindexado.
- Proxy inverso con opciones de caché.
- Balanceo de carga.
- Tolerancia a fallos.
- Soporte de HTTP y HTTP2 sobre SSL.
- Soporte para FastCGI con opciones de caché.
- Servidores virtuales basados en nombre y/o en dirección IP.
- Streaming de archivos FLV y MP4.
- Soporte para autenticación.
- Compatible con IPv6.
- Soporte para protocolo SPDY.
- Compresión gzip.
- Habilitado para soportar más de 10,000 conexiones simultáneas.

## Características del Proxy de Correo

- Proxy SMTP, POP3 e IMAP.
- Soporta STARTTLS.
- Soporta SSL.
