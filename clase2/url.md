# URL

![url_parts](https://github.com/Fictizia/Curso-Node.js-para-desarrolladores-Front-end_ed8/raw/master/assets/url.png)

- **Leyendo urls:**

  ```javascript
  const url = require('url');
  const demoURL = 'http://localhost:3000/ruta?parametro=dato#detalle';
  const parsedUrl = url.parse(demoURL, true);
  
  console.log('Host: ' + parsedUrl.hostname);
  console.log('Puerto: ' + parsedUrl.port);
  console.log('Ruta: ' + parsedUrl.pathname);
  console.log('Parámetros: ' + parsedUrl.query);
  console.log('Hash: ' + parsedUrl.hash);
  ```
  
  ```javascript
  const { URL } = require('url');
  
  const demoURL = new URL("http://localhost:3000/ruta?parametro=dato#detalle");
  
  console.log('Host: ' + demoURLhostname);
  console.log('Puerto: ' + demoURL.port);
  console.log('Ruta: ' + demoURL.pathname);
  console.log('Parámetros: ' + demoURL.query);
  console.log('Hash: ' + demoURL.hash);
  ```

- **Trabajando con rutas:**

  ```javascript
  const http = require('http');
  const url = require('url');
  
  http.createServer(function (req, res) {
    const pathname = url.parse(req.url).pathname;
  
    if (pathname === '/') {
      res.writeHead(200, {
        'Content-Type': 'text/plain'
      });
      res.end('Index!');
    } else if (pathname === '/otro') {
      res.writeHead(200, {
        'Content-Type': 'text/plain; charset=utf-8'
      });
      res.end('sencillamente otra página');
    } else if (pathname === '/alindex') {
      res.writeHead(301, {
        'Location': '/'
      });
      res.end();    
      
    } else {
      res.writeHead(404, {
        'Content-Type': 'text/plain'
      });
      res.end('Querido... 404!');
    }
  }).listen(8080, 'localhost');
  ```

- **Ping recurrente (consola):**

  ```javascript
  const http = require('http');
  const url = "google.es";
  const tiempo = 3500;
  
  setInterval(function() {
    http.get({ host: url }, function(res) {
      if (res.statusCode === 200 ) {  
        console.log(`Sin errores en ${url}`);
      } else {
        console.log(`Respuesta Http ${res.statusCode} en ${url}`);
      }    
    }).on('error', function(e) {
      console.log(`Con errores -> La respuesta de ${url} es ${e.message}`);
    });
  }, tiempo);
  ```
