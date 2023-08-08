# Python

Autor(es): Guido van Rossum

Desarrollador(es): Python Software Foundation

Licencia: Python Software Foundation Licence

Extentensiones: .py, .pyi, .pyc, .pyd, .pyw, .pyz .pyo

[Python Website](https://www.python.org/)

**Python** es un lenguaje de programación de alto nivel y propósito general. Su filosofía de diseño enfatiza la legibilidad del código mediante el uso de la indentación significativa.

Python es un lenguaje de tipo dinámico y con recolección de basura. Admite múltiples paradigmas de programación, incluyendo programación estructurada (particularmente programación procedural), orientada a objetos y programación funcional. A menudo se describe como un lenguaje "con baterías incluidas" debido a su completa biblioteca estándar.

[Guido van Rossum](https://es.wikipedia.org/wiki/Guido_van_Rossum) comenzó a trabajar en Python a fines de la década de 1980 como sucesor del lenguaje de programación [ABC](https://es.wikipedia.org/wiki/ABC_(lenguaje_de_programaci%C3%B3n)) y lo lanzó por primera vez en 1991 como Python 0.9.0. Python 2.0 se lanzó en 2000. Python 3.0, lanzado en 2008, fue una revisión importante que no fue completamente compatible con versiones anteriores. Python 2.7.18, lanzado en 2020, fue la última versión de Python 2.

Python consistentemente se ubica como uno de los lenguajes de programación más populares.

## **Historia**

Python fue concebido a fines de la década de 1980 por [Guido van Rossum](https://es.wikipedia.org/wiki/Guido_van_Rossum) en [Centrum Wiskunde & Informatica](https://es.wikipedia.org/wiki/Centrum_Wiskunde_%26_Informatica) (CWI) en los Países Bajos como sucesor del lenguaje de programación ABC, que fue inspirado por SETL y era capaz de manejo de excepciones y de interactuar con el sistema operativo [Amoeba](https://es.wikipedia.org/wiki/Amoeba_(sistema_operativo)). La implementación comenzó en diciembre de 1989. Van Rossum asumió la responsabilidad exclusiva del proyecto, como el desarrollador principal, hasta el 12 de julio de 2018, cuando anunció su "vacación permanente" de sus responsabilidades como "dictador benevolente de por vida" de Python, título otorgado por la comunidad de Python para reflejar su compromiso a largo plazo como el principal tomador de decisiones del proyecto. En enero de 2019, los desarrolladores principales activos de Python eligieron un Consejo Directivo de cinco miembros para liderar el proyecto.

Python 2.0 se lanzó el 16 de octubre de 2000, con muchas características nuevas importantes como comprensiones de listas, recolección de basura que detecta ciclos, conteo de referencias y soporte Unicode. Python 3.0, lanzado el 3 de diciembre de 2008, con muchas de sus características principales retroportadas a Python 2.6.x y 2.7.x. Las versiones de Python 3 incluyen la utilidad `2to3`, que automatiza la traducción del código de Python 2 a Python 3.

El fin de vida de Python 2.7 se estableció inicialmente para 2015, luego se pospuso a 2020 debido a la preocupación de que una gran cantidad de código existente no se pudiera adaptar fácilmente a Python 3. No se lanzarán más parches de seguridad ni otras mejoras para él. Actualmente, solo se admiten las versiones 3.7 y posteriores. En 2021, se aceleraron las versiones 3.9.2 y 3.8.8 de Python debido a problemas de seguridad en todas las versiones de Python (incluida la 2.7) que llevaron a una posible ejecución de código remoto y envenenamiento de caché web.

En 2022, se aceleraron las versiones 3.10.4 y 3.9.12 de Python, y 3.8.13 y 3.7.13 debido a muchos problemas de seguridad. Cuando se lanzó Python 3.9.13 en mayo de 2022, se anunció que la serie 3.9 (uniéndose a las series antiguas 3.8 y 3.7) solo recibiría correcciones de seguridad en el futuro. El 7 de septiembre de 2022, se realizaron cuatro nuevos lanzamientos debido a un posible ataque de denegación de servicio: 3.10.7, 3.9.14, 3.8.14 y 3.7.14.

A partir de noviembre de 2022, Python 3.11 es la versión estable. Cambios destacados desde 3.10 incluyen un mayor rendimiento en la ejecución del programa y una mejora en la informacion de errores.

## Filosofía de diseño y características

Python es un lenguaje de programación multi-paradigma. El soporte está completamente presente para la programación orientada a objetos y la programación estructurada, y muchas de sus características respaldan la programación funcional y la programación orientada a aspectos (incluyendo la metaprogramación y metaobjetos). Muchos otros paradigmas son admitidos mediante extensiones, incluyendo el diseño por contrato y la programación lógica.

Python utiliza el tipado dinámico y una combinación de contabilización de referencias y un recolector de basura que detecta ciclos para la gestión de memoria. Utiliza resolución de nombres dinámica (enlace tardío), que vincula nombres de métodos y variables durante la ejecución del programa.

Su diseño ofrece cierto soporte para la programación funcional en la tradición de Lisp. Tiene funciones `filter`, `map` y `reduce`; expresiones de comprensión de listas, diccionarios, conjuntos y expresiones de generadores. La biblioteca estándar tiene dos módulos (`itertools` y `functools`) que implementan herramientas funcionales tomadas de Haskell y Standard ML.

Su filosofía central se resume en el documento *El Zen de Python* (*PEP 20*), que incluye afirmaciones tales como:

- Lo hermoso es mejor que lo feo.
- Lo explícito es mejor que lo implícito.
- Lo simple es mejor que lo complejo.
- Lo complejo es mejor que lo complicado.
- La legibilidad cuenta.

En lugar de incorporar todas sus funcionalidades en su núcleo, Python fue diseñado para ser altamente extensible mediante módulos. Esta modularidad compacta lo ha hecho particularmente popular como un medio para agregar interfaces programables a aplicaciones existentes. La visión de Van Rossum de un lenguaje central pequeño con una gran biblioteca estándar e intérprete fácilmente extensible surgió de sus frustraciones con ABC, que defendía el enfoque opuesto.

Python se esfuerza por una sintaxis y gramática más simples y menos abarrotadas, al tiempo que brinda a los desarrolladores una elección en su metodología de codificación. En contraste con el lema de "hay más de una manera de hacerlo" de Perl, Python abraza la filosofía de "debería haber una, y preferiblemente solo una, manera obvia de hacerlo". Alex Martelli, miembro de la Python Software Foundation y autor de libros de Python, escribió: "Describir algo como 'inteligente' no se considera un cumplido en la cultura de Python".

Los desarrolladores de Python se esfuerzan por evitar la optimización prematura y rechazan parches para partes no críticas de la implementación de referencia de CPython que ofrecerían aumentos marginales de velocidad a costa de la claridad. Cuando la velocidad es importante, un programador de Python puede mover funciones críticas en tiempo a módulos de extensión escritos en lenguajes como C; o usar PyPy, un compilador de tiempo justo. También está disponible Cython, que traduce un script de Python a C y realiza llamadas directas a la API de nivel C en el intérprete de Python.

Los desarrolladores de Python apuntan a que sea divertido de usar. Esto se refleja en su nombre, un tributo al grupo de comedia británico Monty Python, y en enfoques ocasionalmente lúdicos en tutoriales y materiales de referencia, como el uso de los términos "spam" y "eggs" (una referencia a un sketch de Monty Python) en ejemplos, en lugar de los términos frecuentemente utilizados "foo" y "bar". Un neologismo común en la comunidad de Python es "pythonic", que tiene una amplia gama de significados relacionados con el estilo de programación. El código "pythonic" puede usar bien los enfoques propios de Python, ser natural o mostrar fluidez en el lenguaje, o conformarse con la filosofía minimalista de Python y su énfasis en la legibilidad. El código que es difícil de entender o parece una transcripción aproximada de otro lenguaje de programación se llama "unpythonic".

## Ejemplos de programación

Programa "Hola mundo":

```python
print('¡Hola, mundo!')

```

Programa para calcular el factorial de un número entero positivo:

```python
n = int(input('Escribe un número, y se imprimirá su factorial: '))

si n < 0:
    raise ValueError('Debes ingresar un entero no negativo')

factorial = 1
para i en rango(2, n + 1):
    factorial *= i

print(factorial)

```

## Bibliotecas

La extensa biblioteca estándar de Python proporciona herramientas adecuadas para muchas tareas y comúnmente se cita como una de sus mayores fortalezas. Para aplicaciones orientadas a Internet, se admiten muchos formatos y protocolos estándar como MIME y HTTP. Incluye módulos para crear interfaces de usuario gráficas, conectarse a bases de datos relacionales, generar números pseudoaleatorios, aritmética con decimales de precisión arbitraria, manipular expresiones regulares y realizar pruebas unitarias.

Algunas partes de la biblioteca estándar están cubiertas por especificaciones, por ejemplo, la implementación de la Interfaz de Puerta de Enlace del Servidor Web (WSGI) `wsgiref` sigue PEP 333, pero la mayoría está especificada por su código, documentación interna y suites de pruebas. Sin embargo, como la mayor parte de la biblioteca estándar es código Python multiplataforma, solo unos pocos módulos necesitan ser modificados o reescritos para implementaciones variantes.

Hasta el 14 de noviembre de 2022, el Índice de Paquetes de Python (PyPI), el repositorio oficial de software de Python de terceros, contiene más de 415,000 paquetes con una amplia gama de funcionalidades, incluyendo:

- Automatización
- Análisis de datos
- Bases de datos
- Documentación
- Interfaces de usuario gráficas
- Procesamiento de imágenes
- Aprendizaje automático
- Aplicaciones móviles
- Multimedia
- Redes informáticas
- Computación científica
- Administración de sistemas
- Marcos de pruebas
- Procesamiento de texto
- Marcos web
- Extracción de datos web

## Entornos de desarrollo

*Ver también: Comparación de entornos de desarrollo integrados § Python*

La mayoría de las implementaciones de Python (incluido CPython) incluyen un bucle de lectura-evaluación-impresión (REPL), lo que les permite funcionar como un intérprete de línea de comandos donde los usuarios ingresan declaraciones secuencialmente y reciben resultados de inmediato.

Python también viene con un Entorno de Desarrollo Integrado (IDE) llamado IDLE, que es más orientado a principiantes.

Otros shells, como IDLE e IPython, añaden habilidades adicionales como una mejor autocompletación, retención del estado de sesión y resaltado de sintaxis.

Además de los entornos de desarrollo integrados de escritorio estándar, hay IDE basados en navegadores web, como SageMath, para desarrollar programas relacionados con la ciencia y las matemáticas; PythonAnywhere, un entorno y entorno de desarrollo basado en navegador; y Canopy IDE, un IDE comercial que enfatiza la computación científica.

## Implementaciones

### Implementación de referencia

[CPython](https://en.wikipedia.org/wiki/CPython) es la implementación de referencia de Python. Está escrita en C, cumpliendo con el estándar [C89](https://en.wikipedia.org/wiki/C89_(C_version)) (Python 3.11 usa [C11](https://en.wikipedia.org/wiki/C11_(C_standard_revision)) con algunas características selectas de [C99](https://en.wikipedia.org/wiki/C99)). CPython incluye sus propias extensiones en C, pero las extensiones de terceros no se limitan a versiones antiguas de C; por ejemplo, pueden implementarse con [C11](https://en.wikipedia.org/wiki/C11_(C_standard_revision)) o C++.[[125]](https://en.wikipedia.org/wiki/Python_(programming_language)#cite_note-125)[[126]](https://en.wikipedia.org/wiki/Python_(programming_language)#cite_note-AutoNT-66-126) Compila programas de Python en un [código intermedio](https://en.wikipedia.org/wiki/Bytecode) que luego es ejecutado por su [máquina virtual](https://en.wikipedia.org/wiki/Virtual_machine). CPython se distribuye con una amplia biblioteca estándar escrita en una combinación de C y Python nativo, y está disponible para muchas plataformas, incluyendo Windows (a partir de Python 3.9, el instalador de Python falla deliberadamente en instalar en [Windows 7](https://en.wikipedia.org/wiki/Windows_7) y 8; Windows XP fue compatible hasta Python 3.5) y la mayoría de los sistemas modernos tipo Unix, incluyendo macOS (y las Mac con [Apple M1](https://en.wikipedia.org/wiki/Apple_M1), desde Python 3.9.1, con instalador experimental) y soporte no oficial para, por ejemplo, [VMS](https://en.wikipedia.org/wiki/OpenVMS). La portabilidad de la plataforma fue una de sus prioridades iniciales.[[132]](https://en.wikipedia.org/wiki/Python_(programming_language)#cite_note-AutoNT-69-132) (Durante el desarrollo de Python 1 y 2, incluso [OS/2](https://en.wikipedia.org/wiki/OS/2) y [Solaris](https://en.wikipedia.org/wiki/Solaris_(operating_system)) fueron compatibles,[[133]](https://en.wikipedia.org/wiki/Python_(programming_language)#cite_note-133) pero desde entonces se ha eliminado el soporte para muchas plataformas).

### Otras implementaciones

- [PyPy](https://en.wikipedia.org/wiki/PyPy) es un intérprete rápido y compatible con Python 2.7 y 3.8. Su compilador de "just-in-time" a menudo proporciona una mejora significativa de velocidad sobre CPython, pero algunas bibliotecas escritas en C no pueden usarse con él.
- [Stackless Python](https://en.wikipedia.org/wiki/Stackless_Python) es un importante fork de CPython que implementa "microthreads"; no utiliza la pila de llamadas de la misma manera, lo que permite programas masivamente concurrentes. PyPy también tiene una versión sin pila de llamadas.
- [MicroPython](https://en.wikipedia.org/wiki/MicroPython) y [CircuitPython](https://en.wikipedia.org/wiki/CircuitPython) son variantes de Python 3 optimizadas para microcontroladores, incluido Lego Mindstorms EV3.
- Pyston es una variante del tiempo de ejecución de Python que utiliza compilación "just-in-time" para acelerar la ejecución de programas de Python.
- Cinder es un fork orientado al rendimiento de CPython 3.8 que contiene varias optimizaciones, incluido el almacenamiento en caché de código en línea, la evaluación anticipada de las corutinas, un "JIT" de método a la vez y un compilador experimental de bytecode.

### Implementaciones no soportadas

Se han desarrollado otros compiladores de Python "just-in-time", pero ahora no tienen soporte:

- Google comenzó un proyecto llamado [Unladen Swallow](https://en.wikipedia.org/wiki/Unladen_Swallow) en 2009, con el objetivo de acelerar el intérprete de Python cinco veces usando LLVM y mejorar su capacidad de multiproceso para escalar a miles de núcleos, mientras que las implementaciones normales sufren del "bloqueo global del intérprete".
- [Psyco](https://en.wikipedia.org/wiki/Psyco) es un compilador "just-in-time" de especialización discontinuado que se integra con CPython y transforma el bytecode en código de máquina en tiempo de ejecución. El código emitido está especializado para ciertos tipos de datos y es más rápido que el código estándar de Python. Psyco no es compatible con Python 2.7 o versiones posteriores.
- [PyS60](https://en.wikipedia.org/wiki/PyS60) fue un intérprete de Python 2 para teléfonos móviles [Series 60](https://en.wikipedia.org/wiki/Series_60) lanzado por Nokia en 2005. Implementó muchos de los módulos de la biblioteca estándar y algunos módulos adicionales para integrarse con el sistema operativo Symbian. El Nokia [N900](https://en.wikipedia.org/wiki/N900) también es compatible con Python con bibliotecas de widgets [GTK](https://en.wikipedia.org/wiki/GTK), lo que permite escribir y ejecutar programas en el dispositivo objetivo.

### Compiladores cruzados a otros lenguajes

Existen varios compiladores a lenguajes de objetos de alto nivel, con Python sin restricciones, un subconjunto restringido de Python o un lenguaje similar a Python como lenguaje fuente:

- Brython, Transcrypt y [Pyjs](https://en.wikipedia.org/wiki/Pyjs) (última versión en 2012) compilan Python a JavaScript.
- [Cython](https://en.wikipedia.org/wiki/Cython) compila (un superset de) Python a C (el código resultante también es utilizable con Python y también, por ejemplo, con C++).
- [Nuitka](https://en.wikipedia.org/wiki/Nuitka) compila Python en C.
- [Numba](https://en.wikipedia.org/wiki/Numba) utiliza LLVM para compilar un subconjunto de Python a código de máquina.
- Pythran compila un subconjunto de Python 3 a C++ ([C++11](https://en.wikipedia.org/wiki/C%2B%2B11)).
- [RPython](https://en.wikipedia.org/wiki/RPython) puede compilar a C y se utiliza para construir el intérprete de PyPy en Python.
- El transpilador Python → 11l → C++ compila un subconjunto de Python 3 a C++ ([C++17]([https://en.wikipedia.org/wiki/C%2B%2](https://en.wikipedia.org/wiki/C%2B%252)

B17)).

Especializados:

- [MyHDL](https://en.wikipedia.org/wiki/MyHDL) es un lenguaje de descripción de hardware (HDL) basado en Python, que convierte el código de MyHDL a código Verilog o VHDL.
- Proyectos más antiguos (o que no deben usarse con Python 3.x y la última sintaxis):
    - Google's Grumpy (última versión en 2017) transpila Python 2 a Go.
    - [IronPython](https://en.wikipedia.org/wiki/IronPython) permite ejecutar programas de Python 2.7 (y una versión alfa, lanzada en 2021, también está disponible para "Python 3.4, aunque pueden incluirse características y comportamientos de versiones posteriores") en el tiempo de ejecución de Common Language Runtime de .NET.
    - [Jython](https://en.wikipedia.org/wiki/Jython) compila Python 2.7 a bytecode de Java, permitiendo el uso de las bibliotecas de Java desde un programa de Python.
    - [Pyrex](https://en.wikipedia.org/wiki/Pyrex_(programming_language)) (última versión en 2010) y [Shed Skin](https://en.wikipedia.org/wiki/Shed_Skin) (última versión en 2013) compilan a C y C++, respectivamente.

### **Rendimiento**

Se presentó una comparación de rendimiento de varias implementaciones de Python en una carga de trabajo no numérica (combinatoria) en EuroSciPy '13. El rendimiento de Python en comparación con otros lenguajes de programación también se evalúa en el *Computer Language Benchmarks Game* (Juego de Bancos de Pruebas de Lenguajes de Computación).

## Desarrollo

El desarrollo de Python se lleva a cabo en gran medida a través del proceso de *Propuesta de Mejora de Python* (PEP), el mecanismo principal para proponer nuevas características importantes, recopilar opiniones de la comunidad sobre problemas y documentar decisiones de diseño de Python. El estilo de codificación de Python está cubierto en el PEP 8. Los PEP pendientes son revisados y comentados por la comunidad de Python y el consejo directivo.

La mejora del lenguaje se corresponde con el desarrollo de la implementación de referencia CPython. La lista de correo python-dev es el foro principal para el desarrollo del lenguaje. Los problemas específicos se discutieron originalmente en el sistema de seguimiento de errores Roundup alojado por la fundación. En 2022, todos los problemas y discusiones se migraron a GitHub. El desarrollo originalmente se realizaba en un repositorio de código fuente autohospedado que utilizaba Mercurial, hasta que Python se trasladó a GitHub en enero de 2017.

Las versiones públicas de CPython se dividen en tres tipos, diferenciados por qué parte del número de versión se incrementa:

- Versiones no compatibles hacia atrás, donde se espera que el código se rompa y deba ser portado manualmente. La primera parte del número de versión se incrementa. Estas versiones se lanzan con poca frecuencia; la versión 3.0 se lanzó 8 años después de la 2.0. Según Guido van Rossum, es muy improbable que ocurra una versión 4.0.
- Lanzamientos mayores o de "características" son en gran medida compatibles con la versión anterior, pero introducen nuevas características. La segunda parte del número de versión se incrementa. A partir de Python 3.9, se espera que estos lanzamientos ocurran anualmente. Cada versión principal recibe correcciones de errores durante varios años después de su lanzamiento.
- Lanzamientos de corrección de errores, que no introducen nuevas características, ocurren aproximadamente cada 3 meses y se realizan cuando se han corregido suficientes errores desde el último lanzamiento. Las vulnerabilidades de seguridad también se corrigen en estos lanzamientos. La tercera y última parte del número de versión se incrementa.

También se lanzan muchas versiones alfa, beta y candidatos a versión preliminares y para pruebas antes de las versiones finales. Aunque hay un cronograma aproximado para cada lanzamiento, a menudo se retrasan si el código no está listo. El equipo de desarrollo de Python monitorea el estado del código ejecutando el extenso conjunto de pruebas unitarias durante el desarrollo.

La principal conferencia académica sobre Python es PyCon. También existen programas especiales de tutoría de Python, como Pyladies. Python 3.10 deprecó `wstr` (para eliminarse en Python 3.12; lo que significa que las extensiones de Python[[170]] necesitarán modificarse para entonces), y se agregó coincidencia de patrones al lenguaje.

## Generadores de documentación de API

Herramientas que pueden generar documentación para la API de Python incluyen pydoc (disponible como parte de la biblioteca estándar), Sphinx, Pdoc y sus bifurcaciones, Doxygen y Graphviz, entre otros.

## Denominación

El nombre de Python se deriva del grupo de comedia británico [Monty Python](https://es.wikipedia.org/wiki/Monty_Python), al cual el creador de Python, Guido van Rossum, disfrutaba mientras desarrollaba el lenguaje. Las referencias a Monty Python aparecen con frecuencia en el código y la cultura de Python; por ejemplo, las variables metasintácticas utilizadas a menudo en la literatura de Python son *spam* y *eggs* en lugar de las tradicionales *foo* y *bar*. La documentación oficial de Python también contiene varias referencias a rutinas de Monty Python. Los usuarios de Python a veces son llamados "Pythonistas".

El prefijo *Py-* se utiliza para indicar que algo está relacionado con Python. Ejemplos del uso de este prefijo en nombres de aplicaciones o bibliotecas de Python incluyen [Pygame](https://es.wikipedia.org/wiki/Pygame), una biblioteca para enlazar SDL con Python (comúnmente utilizada para crear juegos); [PyQt](https://es.wikipedia.org/wiki/PyQt) y [PyGTK](https://es.wikipedia.org/wiki/PyGTK), que enlazan Qt y GTK con Python respectivamente; y [PyPy](https://es.wikipedia.org/wiki/PyPy), una implementación de Python escrita originalmente en Python.

## Popularidad

Desde 2003, Python ha estado consistentemente entre los diez lenguajes de programación más populares en el Índice de la Comunidad de Programación TIOBE, donde en diciembre de 2022 era el lenguaje más popular (por delante de C, C++ y [Java](https://es.wikipedia.org/wiki/Java_(lenguaje_de_programaci%C3%B3n))). Fue seleccionado como Lenguaje de Programación del Año (por "el mayor aumento en las calificaciones en un año") en 2007, 2010, 2018 y 2020 (el único lenguaje en haberlo hecho cuatro veces hasta 2020).

Un estudio empírico encontró que los lenguajes de script, como Python, son más productivos que los lenguajes convencionales, como C y Java, para problemas de programación que involucran manipulación de cadenas y búsqueda en un diccionario, y determinó que el consumo de memoria a menudo era "mejor que Java y no mucho peor que C o C++".

Grandes organizaciones que utilizan Python incluyen [Wikipedia](https://es.wikipedia.org/wiki/Wikipedia), [Google](https://es.wikipedia.org/wiki/Google), [Yahoo!]([https://es.wikipedia.org/wiki/Yahoo!)](https://es.wikipedia.org/wiki/Yahoo!)), [CERN](https://es.wikipedia.org/wiki/CERN), [NASA](https://es.wikipedia.org/wiki/NASA), [Facebook](https://es.wikipedia.org/wiki/Facebook), [Amazon](https://es.wikipedia.org/wiki/Amazon_(empresa)), [Instagram](https://es.wikipedia.org/wiki/Instagram), [Spotify](https://es.wikipedia.org/wiki/Spotify) y algunas entidades más pequeñas como [ILM](https://es.wikipedia.org/wiki/Industrial_Light_%26_Magic) y [ITA](https://es.wikipedia.org/wiki/ITA_Software). El sitio de redes de noticias sociales [Reddit](https://es.wikipedia.org/wiki/Reddit) fue mayormente escrito en Python.

## Usos

Python puede servir como un lenguaje de script para aplicaciones web, por ejemplo, a través de [mod_wsgi](https://es.wikipedia.org/wiki/Mod_wsgi) para el servidor web [Apache](https://es.wikipedia.org/wiki/Apache_http_server). Con la Interfaz de Pasarela del Servidor Web, ha evolucionado una API estándar para facilitar estas aplicaciones. Marcos de desarrollo web como [Django](https://es.wikipedia.org/wiki/Django_(framework)), [Pylons](https://es.wikipedia.org/wiki/Pylons_(web_framework)), [Pyramid](https://es.wikipedia.org/wiki/Pyramid_(web_framework)), [TurboGears](https://es.wikipedia.org/wiki/TurboGears), [web2py](https://es.wikipedia.org/wiki/Web2py), [Tornado](https://es.wikipedia.org/wiki/Tornado_(web_server)), [Flask](https://es.wikipedia.org/wiki/Flask_(web_framework)), Bottle y [Zope](https://es.wikipedia.org/wiki/Zope) brindan soporte a los desarrolladores en el diseño y mantenimiento de aplicaciones complejas. Pyjs e [IronPython](https://es.wikipedia.org/wiki/IronPython) se pueden usar para desarrollar el lado cliente de aplicaciones basadas en Ajax. [SQLAlchemy](https://es.wikipedia.org/wiki/SQLAlchemy) se puede usar como un mapeador de datos a una base de datos relacional. [Twisted](https://es.wikipedia.org/wiki/Twisted_(software)) es un marco para programar comunicaciones entre computadoras, y es utilizado (por ejemplo) por [Dropbox](https://es.wikipedia.org/wiki/Dropbox_(servicio)).

Bibliotecas como [NumPy](https://es.wikipedia.org/wiki/NumPy), [SciPy](https://es.wikipedia.org/wiki/SciPy) y [Matplotlib](https://es.wikipedia.org/wiki/Matplotlib) permiten el uso efectivo de Python en la computación científica, con bibliotecas especializadas como [Biopython](https://es.wikipedia.org/wiki/Biopython) y [Astropy](https://es.wikipedia.org/wiki/Astropy) que proporcionan funcionalidades específicas para diferentes dominios. [SageMath](https://es.wikipedia.org/wiki/SageMath) es un sistema de álgebra computacional con una interfaz de cuaderno programable en Python; su biblioteca abarca muchos aspectos de las matemáticas, incluyendo álgebra, combinatoria, matemáticas numéricas, teoría de números y cálculo. [OpenCV](https://es.wikipedia.org/wiki/OpenCV) tiene enlaces con Python y ofrece un conjunto de funciones para visión por computadora y procesamiento de imágenes.

Python se usa comúnmente en proyectos de inteligencia artificial y aprendizaje automático con la ayuda de bibliotecas como [TensorFlow](https://es.wikipedia.org/wiki/TensorFlow), [Keras](https://es.wikipedia.org/wiki/Keras), [PyTorch](https://es.wikipedia.org/wiki/PyTorch) y [scikit-learn](https://es.wikipedia.org/wiki/Scikit-learn). Como lenguaje de script con una arquitectura modular, sintaxis sencilla y herramientas de procesamiento de texto ricas, Python a menudo se utiliza en el procesamiento del lenguaje natural.

Python también se puede utilizar para crear interfaces gráficas de usuario (GUI) utilizando bibliotecas como [Tkinter](https://es.wikipedia.org/wiki/Tkinter).

Python también se utiliza para crear juegos, con bibliotecas como [Pygame](https://es.wikipedia.org/wiki/Py

game) que permiten crear juegos en 2D.

Python se ha incorporado con éxito en muchos productos de software como lenguaje de script, incluido en software de método de elementos finitos como [Abaqus](https://es.wikipedia.org/wiki/Abaqus), modeladores paramétricos 3D como [FreeCAD](https://es.wikipedia.org/wiki/FreeCAD), paquetes de animación 3D como [3ds Max](https://es.wikipedia.org/wiki/3ds_Max), [Blender](https://es.wikipedia.org/wiki/Blender_(software)), [Cinema 4D](https://es.wikipedia.org/wiki/Cinema_4D), [Lightwave](https://es.wikipedia.org/wiki/LightWave_3D), [Houdini](https://es.wikipedia.org/wiki/Houdini_(software)), [Maya](https://es.wikipedia.org/wiki/Maya_(software)), [modo](https://es.wikipedia.org/wiki/Modo_(software)), [MotionBuilder](https://es.wikipedia.org/wiki/MotionBuilder), [Softimage](https://es.wikipedia.org/wiki/Autodesk_Softimage), el compositor de efectos visuales [Nuke](https://es.wikipedia.org/wiki/Nuke_(software)), programas de imágenes 2D como [GIMP](https://es.wikipedia.org/wiki/GIMP), [Inkscape](https://es.wikipedia.org/wiki/Inkscape), [Scribus](https://es.wikipedia.org/wiki/Scribus) y [Paint Shop Pro](https://es.wikipedia.org/wiki/Paint_Shop_Pro), y programas de notación musical como [scorewriter](https://es.wikipedia.org/wiki/Scorewriter) y [capella](https://es.wikipedia.org/wiki/Capella_(notation_program)). El depurador [GNU Debugger](https://es.wikipedia.org/wiki/GNU_Debugger) utiliza Python como un "pretty printer" para mostrar estructuras complejas como los contenedores de C++. Esri promociona Python como la mejor opción para escribir scripts en [ArcGIS](https://es.wikipedia.org/wiki/ArcGIS). También se ha utilizado en varios videojuegos y ha sido adoptado como uno de los tres lenguajes de programación disponibles en [Google App Engine](https://es.wikipedia.org/wiki/Google_App_Engine), junto con [Java](https://es.wikipedia.org/wiki/Java_(lenguaje_de_programaci%C3%B3n)) y [Go](https://es.wikipedia.org/wiki/Go_(lenguaje_de_programaci%C3%B3n)).

La mayoría de los componentes del software [Sugar](https://es.wikipedia.org/wiki/Sugar_(software)) para la laptop [One Laptop per Child](https://es.wikipedia.org/wiki/One_Laptop_per_Child) XO, desarrollados en [Sugar Labs](https://es.wikipedia.org/wiki/Sugar_Labs) desde 2008, están escritos en Python. El proyecto de la [computadora de placa única Raspberry Pi](https://es.wikipedia.org/wiki/Raspberry_Pi) ha adoptado Python como su principal lenguaje de programación para usuarios.

[LibreOffice](https://es.wikipedia.org/wiki/LibreOffice) incluye Python y tiene la intención de reemplazar Java con Python. Su Proveedor de Scripting en Python es una característica central desde la versión 4.0 lanzada el 7 de febrero de 2013.

## Lenguajes influenciados por Python

El diseño y la filosofía de Python han influido en muchos otros lenguajes de programación:

- [Boo](https://es.wikipedia.org/wiki/Boo_(lenguaje_de_programaci%C3%B3n)) utiliza la indentación, una sintaxis similar y un modelo de objetos similar.
- [Cobra](https://es.wikipedia.org/wiki/Cobra_(lenguaje_de_programaci%C3%B3n)) utiliza la indentación y una sintaxis similar, y su documento de *Agradecimientos* lista a Python como el primer lenguaje que lo influenció.
- [CoffeeScript](https://es.wikipedia.org/wiki/CoffeeScript), un lenguaje de programación que se compila a JavaScript, tiene una sintaxis inspirada en Python.
- [ECMAScript](https://es.wikipedia.org/wiki/ECMAScript)/[JavaScript](https://es.wikipedia.org/wiki/JavaScript) tomó prestados los iteradores y generadores de Python.
- [GDScript](https://es.wikipedia.org/wiki/GDScript), un lenguaje de script muy similar a Python, integrado en el motor de juegos [Godot](https://es.wikipedia.org/wiki/Godot_(motor_de_videojuego)).
- [Go](https://es.wikipedia.org/wiki/Go_(lenguaje_de_programaci%C3%B3n)) está diseñado para la "rapidez de trabajo en un lenguaje dinámico como Python" y comparte la misma sintaxis para rebanar arreglos.
- [Groovy](https://es.wikipedia.org/wiki/Groovy_(lenguaje_de_programaci%C3%B3n)) fue motivado por el deseo de llevar la filosofía de diseño de Python a [Java](https://es.wikipedia.org/wiki/Java_(lenguaje_de_programaci%C3%B3n)).
- [Julia](https://es.wikipedia.org/wiki/Julia_(lenguaje_de_programaci%C3%B3n)) fue diseñado para ser "tan utilizable para la programación general como Python".
- [Mojo](https://es.wikipedia.org/wiki/Mojo_(lenguaje_de_programaci%C3%B3n)) es actualmente una superconjunto no estricto (aspira a ser estricto) de Python (por ejemplo, todavía le faltan clases y agrega estructuras, y es hasta 35,000 veces más rápido para algún código [mandelbrot], ya que es [embarazosamente paralelo](https://es.wikipedia.org/wiki/Procesamiento_embarrado), donde la escritura estática ayuda (y se implementa con [MLIR](https://es.wikipedia.org/wiki/Intermediate_representation#Languages)), y por ejemplo 4000 veces más rápido para la multiplicación de matrices. Aún no es de código abierto, pero ese es el plan.
- [Nim](https://es.wikipedia.org/wiki/Nim_(lenguaje_de_programaci%C3%B3n)) utiliza la indentación y una sintaxis similar.
- El creador de [Ruby](https://es.wikipedia.org/wiki/Ruby_(lenguaje_de_programaci%C3%B3n)), [Yukihiro Matsumoto](https://es.wikipedia.org/wiki/Yukihiro_Matsumoto), ha dicho: "Quería un lenguaje de script más poderoso que Perl y más orientado a objetos que Python. Por eso decidí diseñar mi propio lenguaje".
- [Swift](https://es.wikipedia.org/wiki/Swift_(lenguaje_de_programaci%C3%B3n)), un lenguaje de programación desarrollado por Apple, tiene cierta sintaxis inspirada en Python.

Las prácticas de desarrollo de Python también han sido imitadas por otros lenguajes. Por ejemplo, la práctica de requerir un documento que describa la justificación y los problemas en torno a un cambio en el lenguaje (en Python, un PEP) también se utiliza en [Tcl](https://es.wikipedia.org/wiki/Tcl), [Erlang](https://es.wikipedia.org/wiki/Erlang_(lenguaje_de_programaci%C3%B3n)) y Swift.
