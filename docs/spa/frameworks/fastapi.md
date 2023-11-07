# FastAPI

- **Desarrollador(es)**: Sebastián Ramírez
- **Lanzamiento**: 2018
- **Licencia**: MIT
- **Escrito en**: Python
- **Página**: [https://fastapi.tiangolo.com/](https://fastapi.tiangolo.com/)
- **Repositorio**: [https://github.com/tiangolo/fastapi](https://github.com/tiangolo/fastapi)

**FastAPI** es un moderno marco de trabajo web para construir APIs REST en Python. Fue lanzado por primera vez en 2018 y desde entonces ha ganado rápidamente popularidad entre los desarrolladores debido a su facilidad de uso, velocidad y robustez.

FastAPI se basa en Pydantic y utiliza sugerencias de tipo para validar, serializar y deserializar datos. También genera automáticamente documentación OpenAPI para las APIs construidas con él.

FastAPI es totalmente compatible con la programación asincrónica y puede ejecutarse en servidores como Gunicorn y ASGI, como Uvicorn e Hypercorn, lo que lo convierte en una buena elección para entornos de producción. Para mejorar la amigabilidad del desarrollador, se consideró el soporte del editor desde los primeros días del proyecto.

## Componentes

### Pydantic

Pydantic es una biblioteca de validación de datos para Python. Dado que la lógica de validación de tipos está escrita en el lenguaje de programación Rust, Pydantic está entre las bibliotecas de validación de datos más rápidas para Python. Al escribir código en un entorno de desarrollo integrado (IDE), Pydantic proporciona sugerencias de tipos para la validación de esquemas y la serialización a través de anotaciones de tipos.

### Starlette

Starlette es un marco/herramienta ASGI ligero con el objetivo de admitir la funcionalidad asíncrona en Python. Starlette ha demostrado un gran rendimiento en pruebas independientes, lo cual es heredado por FastAPI.

### Uvicorn

Uvicorn es un servidor de aplicaciones web de nivel bajo y mínimo para marcos asíncronos, siguiendo la especificación ASGI.

## Características

- Alto rendimiento
- Sugerencias de tipos
- Validación de datos
- Documentación automática basada en estándares de OpenAPI
- Inyección de dependencias

## Adopción y uso en el mundo real

FastAPI fue el tercer marco web más querido en la Encuesta de Desarrolladores de Stack Overflow 2021.

Grandes empresas como Uber y Netflix lo utilizan para desarrollar algunas de sus aplicaciones.

## Ejemplo

El siguiente código muestra una aplicación web simple que muestra "[Hello World]!" cuando se visita:

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return "Hello World!"

```
