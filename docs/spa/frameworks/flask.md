# Flask

- **Desarrollador(es)**: Armin Ronacher
- **Lanzamiento**: 2010
- **Licencia**: BSD
- **Escrito en**: Python
- **Página**: [https://palletsprojects.com/p/flask/](https://palletsprojects.com/p/flask/)
- **Documentación**: [https://flask.palletsprojects.com/en/](https://flask.palletsprojects.com/en/)
- **Repositorio**: [https://github.com/pallets/flask](https://github.com/pallets/flask)

**Flask** es un microframework web escrito en Python. Se clasifica como un microframework porque no requiere herramientas o bibliotecas particulares. No tiene una capa de abstracción de base de datos, validación de formularios ni ningún otro componente en el que las bibliotecas de terceros preexistentes proporcionen funciones comunes. Sin embargo, Flask admite extensiones que pueden agregar características de la aplicación como si estuvieran implementadas en Flask mismo. Existen extensiones para mapeadores objeto-relacional, validación de formularios, manejo de cargas, varias tecnologías de autenticación abierta y varias herramientas relacionadas con marcos comunes.

Las aplicaciones que utilizan el framework Flask incluyen Pinterest y LinkedIn.

## Historia

Flask fue creado por Armin Ronacher de Pocoo, un grupo internacional de entusiastas de Python formado en 2004. Según Ronacher, la idea originalmente fue una broma del Día de los Inocentes lo suficientemente popular como para convertirla en una aplicación seria. El nombre es un juego con el marco anterior llamado Bottle.

Cuando Ronacher y Georg Brandl crearon un sistema de tablón de anuncios escrito en Python en 2004, se desarrollaron los proyectos de Pocoo, Werkzeug y Jinja.

En abril de 2016, el equipo de Pocoo se disolvió y el desarrollo de Flask y las bibliotecas relacionadas pasó al recién formado proyecto Pallets. Desde 2018, los datos y objetos relacionados con Flask pueden ser renderizados con Bootstrap.

Flask se ha vuelto popular entre los entusiastas de Python. Hasta octubre de 2020, tenía la segunda mayor cantidad de estrellas en GitHub entre los marcos de desarrollo web de Python, solo ligeramente detrás de Django, y fue votado como el marco web más popular en la Encuesta de Desarrolladores de Python en los años 2018 a 2022.

## Componentes

El microframework Flask forma parte de los *Proyectos Pallets* (anteriormente *Pocoo*), y se basa en varios de ellos, todos bajo una licencia BSD.

### Werkzeug

Werkzeug (del alemán "herramienta") es una biblioteca de utilidades para el lenguaje de programación Python, destinada a aplicaciones de la Interfaz de Pasarela del Servidor Web (WSGI). Werkzeug puede instanciar objetos para solicitudes, respuestas y funciones de utilidad. Se puede utilizar como base para un marco de software personalizado y es compatible con Python 2.7 y 3.5 en adelante.

### Jinja

Jinja, también creado por Ronacher, es un motor de plantillas para el lenguaje de programación Python. Al igual que el marco web Django, maneja plantillas en un entorno seguro.

### MarkupSafe

MarkupSafe es una biblioteca de manipulación de cadenas de caracteres para el lenguaje de programación Python. El tipo MarkupSafe homónimo extiende el tipo de cadena de Python y marca su contenido como "seguro"; combinar MarkupSafe con cadenas regulares escapa automáticamente las cadenas no marcadas, evitando la doble escapada de las cadenas ya marcadas.

### ItsDangerous

ItsDangerous es una biblioteca segura de serialización de datos para el lenguaje de programación Python. Se utiliza para almacenar la sesión de una aplicación Flask en una cookie sin permitir que los usuarios manipulen el contenido de la sesión.

## Características

- Servidor de desarrollo y depurador
- Soporte integrado para pruebas unitarias
- Enrutamiento de solicitudes RESTful
- Utiliza la plantilla Jinja
- Soporte para cookies seguras (sesiones en el lado del cliente)
- 100% compatible con WSGI 1.0
- Basado en Unicode
- Documentación completa
- Compatibilidad con Google App Engine
- Extensiones disponibles para ampliar la funcionalidad

## Ejemplo

El siguiente código muestra una aplicación web simple que muestra "Hello World!" cuando se visita:

```python
from flask import Flask
app = Flask(__name__)

@app.route("/")
def hello() -> str:
    return "Hello World"

if __name__ == "__main__":
    app.run()
```
