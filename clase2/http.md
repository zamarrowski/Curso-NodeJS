# HTTP

### Trabajando con APIs

> Una API representa la capacidad de comunicación entre componentes de software.

**CRUD**

![CRUD](https://github.com/Fictizia/Curso-Node.js-para-desarrolladores-Front-end_ed8/raw/master/assets/crud.png)

- **Create** (POST):
  - Respuesta 200 - OK
  - Respuesta 204 - Sin contenido
  - Respuesta 404 - No encontrado
  - Respuesta 409 - Conflicto, ya existe
- **Read** (GET):
  - Respuesta 200 - OK
  - Respuesta 404 - No encontrado
- **Update** (PUT):
  - Respuesta 200 - OK
  - Respuesta 204 - Sin contenido
  - Respuesta 404 - No encontrado
- **Delete** (DELETE):
  - Respuesta 200 - OK
  - Respuesta 404 - No encontrado


![HTTP Protocolo](https://github.com/Fictizia/Curso-Node.js-para-desarrolladores-Front-end_ed8/raw/master/assets/http.png)


**Códigos de respuesta HTTP**:

- 1xx Informativas
- 2xx Peticiones Correctas
- 3xx Redirecciones
- 4xx Errores Cliente
- 5xx Errores Servidor


[Lista de respuestas HTTP](https://es.wikipedia.org/wiki/Anexo:C%C3%B3digos_de_estado_HTTP)

[Especificación](https://tools.ietf.org/html/rfc2616#section-10)

**Ejemplos**:
- [API RTVE](https://github.com/UlisesGascon/RTVE-API)
- [API Github](https://developer.github.com/v3/)


### Multipurpose Internet Mail Extensions (MIME)

- **Más usadas:**
  - text/html
  - text/plain
  - text/css
  - image/gif
  - image/x-png
  - image/jpeg
  - application/pdf
  - application/zip
  - text/javascript
  - *[Lista Completa](http://sites.utoronto.ca/webdocs/HTMLdocs/Book/Book-3ed/appb/mimetype.html)*
