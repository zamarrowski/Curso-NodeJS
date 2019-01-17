# AJAX

> Asynchronous JavaScript And XML, es una técnica de desarrollo web para crear aplicaciones interactivas.

![Ajax comparación](https://github.com/Fictizia/Curso-Node.js-para-desarrolladores-Front-end_ed8/raw/master/assets/ajax.jpg)

**Con Jquery**

```javascript
function peticionJqueryAjax (url) {
  $.ajax({
    dataType: "json",
    url,
  }).done((data, textStatus, jqXHR) => {
    console.log('La solicitud se ha completado correctamente.');
    console.log( data );
  }).fail((jqXHR, textStatus, errorThrown) => {
    console.log(`La solicitud a fallado: ${textStatus}`);
  });
}
  
peticionAjax('https://api.github.com/users/josex2r')
```

**Vanilla JS** (`XMLHttpRequest`)

- *readyState*:
  - 0 es *uninitialized*
  - 1 es *loading*
  - 2 es *loaded*
  - 3 es *interactive*
  - 4 es *complete*

```javascript
function peticionAjax(url) {
  const xmlHttp = new XMLHttpRequest();

  xmlHttp.onreadystatechange = function() {

    if (xmlHttp.readyState === 4 && xmlHttp.status === 200) {
      console.info(JSON.parse(xmlHttp.responseText));
    } else if (xmlHttp.readyState === 4 && xmlHttp.status === 404) {
      console.error('ERROR! 404');
      console.info(JSON.parse(xmlHttp.responseText));
    }
  };
  xmlHttp.open('GET', url, true);
  xmlHttp.send();
}

peticionAjax('https://api.github.com/users/josex2r')
```

**Vanilla JS** (`fetch`)

```javascript
function peticionAjax(url) {
  fetch(url)
    .then((response) => response.json())
    .then((json) => {
      console.log(json);
    }, () => {
      console.error('ERROR!!!');
    });
}

peticionAjax('https://api.github.com/users/josex2r')
```

### JSON

- `JSON.parse()`: Analiza la cadena y retorna los valores

- `JSON.stringify()`: Analiza los valores y retorna una cadena 

### JSONP

> JSONP o JSON con padding es una técnica de comunicación utilizada en los programas JavaScript para realizar llamadas asíncronas a dominios diferentes.

El objeto JSON se devuelve envuelto en la llamada de una función. De esta forma, una función ya definida en el entorno de JavaScript podría manipular los datos JSON.

```javascript
jsonCallback({
  api_key: '224Wrf2asfSDfcea23reSDfqW',
  status: 'good',
  name: 'wikipedia',
  date: '27-09-1995'
});
```

Por convención, el nombre de la función de retorno se especifica mediante un parámetro de la consulta, normalmente, utilizando jsonp o callback como nombre del campo en la solicitud al servidor.

```html
<script type="text/javascript" src="http://servidor.ejemplo.com/datos.json?callback=parseJSON"></script>
```

Soporte en cliente (librerías):

- Jquery:

  ```javascript
  // Using YQL and JSONP
  $.ajax({
    url: 'http://query.yahooapis.com/v1/public/yql',
    // The name of the callback parameter, as specified by the YQL service
    jsonp: 'callback',
    // Tell jQuery we're expecting JSONP
    dataType: 'jsonp',
    // Tell YQL what we want and that we want JSON
    data: {
      q: 'select title,abstract,url from search.news where query="cat"',
      format: 'json'
    },
    // Work with the response
    success(response) {
      console.log(response); // server response
    }
  });
  ```
- [jsonp.js de Przemek Sobstel](https://github.com/sobstel/jsonp.js/blob/master/jsonp.js)
- [J50Npi.js de Roberto Decurnex](https://github.com/robertodecurnex/J50Npi/blob/master/J50Npi.js)
