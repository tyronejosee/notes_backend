# Django Roadmap:

-------------------

## Part 1 (Development Basics):
- Python virtual environment (pipenv, virtualenv, pyenv)

- Effective Python Book

- VCS (Version Control System):
  Git and Github (commits, branches, merges, conflicts, stashing, pull requests)
  
- IDE/Text Editor:
 Pycharm Pro or VS Code (shortcuts, formatting, integrations, plugins)
  
- Networks Basics:
 IPs, Ports, HTTP/HTTPS, FTP, Webservers, NATs, SSH, ...etc
  
- Linux

- Using The Terminal/CMD/PowerShell

# Part 2 (Databases)
- RDB (PostgreSQL, MySQL/MariaDB, SQLite)
- NoSQL (MongoDB, Redis)
- ORM (Object-Relational Mapper)
  
## Part 3 (Software Engineering)
- Conventional Commits
- Trunk-based Development (https://www.atlassian.com/continuous-delivery/continuous-integration/trunk-based-development)
- Change Logs
- README
- Documentation
- Clean Code
- Design Principles (SOLID, KISS, YAGNI, ...etc)
- Design Patterns
- Testing (Unit, Integration, Functional)
- Pytest
- TDD (Test-Driven Development)
- BDD (Behavior-Driven Development)
- DDD (Domain-Driven Design)
- Issue Tracking (GitHub issues, JIRA, Redmine) Learn how to mention issue number in commit message
- Continues Integration ([GitHub Actions](https://github.com/features/actions), Jenkins, Travis-CI)
- pre-commit hooks (black, flake) 
- .env files and environmental variables 
- Logs, and Logging (For Example Sentry)


## Part 4 (Web)
- HTML, CSS, SASS, Javascript, Bootstrap and JQuery
- REST API
- Swagger
- ngrok
- GraphQL
- Browser dev tools (elements tab, console, network tab, performance) 


## Part 5 (Theory and Tools):
- Security (XSS, SQL Injection, CSRF, CORS, ...etc)
- Symmetric Encryption and Asymmetric Encryption
- SSH (Connecting, Generating Keys, Adding Hosts, ...etc)
- Authentication (session, basic, token and jwt token)
- Docker, docker-compose
- Postman
- Authentication vs Authorization


## Part 6 (Django)
- Good Resources:
  - Two-Scoops with Django
  - Code With Mosh - Ultimate Django Series
  - Documentation
- Django App Architecture and Organization
- Important Packages
  - django-split-settings (https://sobolevn.me/2017/04/managing-djangos-settings)
  - django-allauth (social auth)
  - django-rest-auth (for drf)
  - django-braces (mixins)
  - django-compressor (for static files)
  - django-countries (country fields)
  - django-crispy-forms (render forms)
  - django-db-mailer
  - django-el-pagination
  - django-extensions (shell_plus, jobs, ...etc)
  - drf-extra-fields (Base64Fields)
  - django-filters
  - django-fsm (state machine)
  - django-jet (admin styles and template)
  - django-modeltranslation
  - django-newsletter
  - django-phonenumber-field
  - django-push-notifications
  - django-solo
  - django-treebeard
  - PyJWT
  - django-redis
  - django-wkhtmltopdf
  - django-import-export
  - sentry-sdk
  - django-ckeditor
  - geopy (locating)
  - django-rest-knox (auth)
  - drf-spectacular (swagger)
  - easy-thumbnails
  - django-oscar
  - django-oscar-api
  - django-oscar-invoices
  - django-debug-toolbar
  - pytest-django
  - pytest-cov

- custom management commands 
- custom migrations 
- permissions 
- Django cookie-cutter
- Django Rest Framework
- Wagtail 
- Django cms

## Part 7 (Advanced Concepts & Devops & Production):
- Elastic Stack
- Caching with redis
- Asynchronous programming (celery, rabbit mq, django rq, Kafka) 
- Linux cron jobs
- AWS Basics (S3, EC2, Networks)
- Gunicorn
- Nginx
- Microservices
- Hosting (PAAS, SAAS, IAAS)
- System Design (a good book is System Design Interview - An Insider's Guide)


## Part 8 (Front-End Optional Miscellaneous)
- NPM
- Webpack  
- SPA (Vue and Nuxt.js/React and Next.js/Angular)
- PWA
- TypeScript
- ...etc




















---

## HTML

- Estructura básica de documentos HTML
- Etiquetas principales
- Semántica
- Atributos
- Estructura de la página (Layout)
- Entidades
- Formularios
- Multimedia
- Eventos

## CSS

- Introducción a CSS
- Sintaxis y selectores
- Modelo de caja
- Fuentes y tipografías
- Colores y backgrounds
- Visibilidad y posicionamiento
- Técnicas de layout (Flexbox, Grid)
- Transiciones y animaciones
- Diseño responsive
- Variables CSS
- Preprocesadores CSS (SASS, Less)

## JavaScript

- Estructura básica de JavaScript
- Estructuras de control
- Funciones
- Alcance (Scope) y clausura (Clousure)
- Arrays
- Objetos
- Manipulación del DOM
- Gestión de eventos
- Promesas y Async/Await
- AJAX y Fetch API

## React

- Introducción a React
- JSX y componentes
- Props y estados
- Ciclo de vida de los componentes
- Hooks
- Routing
- Integración API
- Formularios y validación
- Estilos
- Gestión de estado global
- Optimización de rendimiento

---

## Metadatos

- **Desarrollador(es)**: Apache Software Foundation
- **Lanzamiento**: 0000
- **Licencia**: Apache 2.0
- **Escrito en**: Java
- **Página**: [https://cassandra.apache.org/](https://cassandra.apache.org/)
- **Documentación**: [https://cassandra.apache.org/doc/](https://cassandra.apache.org/doc/)
- **Repositorio**: [https://github.com/apache/cassandra](https://github.com/apache/cassandra)

---

## Librerías de Python

os y os.path: El módulo os proporciona funciones para interactuar con el sistema operativo, incluyendo operaciones relacionadas con archivos y directorios. os.path se utiliza para trabajar con rutas de archivo y directorio de manera segura en diferentes sistemas operativos.

io: El módulo io proporciona herramientas para trabajar con flujos de entrada y salida, como leer y escribir datos desde y hacia archivos.

open: La función open() es una función incorporada que se utiliza para abrir archivos en diferentes modos (lectura, escritura, añadir, etc.). Retorna un objeto de archivo que se puede usar para interactuar con el archivo.

shutil: El módulo shutil permite realizar operaciones de más alto nivel en archivos y directorios, como copiar, mover y eliminar.

glob: El módulo glob se utiliza para buscar archivos que coincidan con ciertos patrones en un directorio.

json: Si trabajas con archivos JSON, el módulo json es esencial para leer y escribir datos en formato JSON.

csv: Para archivos CSV (valores separados por comas), el módulo csv es útil para leer y escribir datos en este formato.

pickle: El módulo pickle permite serializar objetos de Python en un formato binario, lo que es útil para guardar objetos complejos en archivos.

pathlib: A partir de Python 3.4, el módulo pathlib proporciona una interfaz más orientada a objetos y moderna para manipular rutas y archivos.

sqlite3: Si deseas trabajar con bases de datos SQLite, el módulo sqlite3 es una excelente opción para el manejo de bases de datos incorporadas en archivos.

requests: Si estás interesado en descargar archivos desde Internet, el módulo requests es perfecto para realizar solicitudes HTTP y descargar contenido.

zipfile: Si necesitas trabajar con archivos comprimidos en formato ZIP, el módulo zipfile te permitirá extraer y crear archivos ZIP.

tarfile: Similar al zipfile, pero para archivos comprimidos en formato TAR.

pathlib: Este módulo proporciona una interfaz más moderna y orientada a objetos para trabajar con rutas de archivos y directorios.