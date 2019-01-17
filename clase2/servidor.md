# Como crear un servidor de Nodejs

Tenemos que usar el módulo nativo [HTTP](https://nodejs.org/api/http.html) y en solo 6 líneas tenemos un servidor HTTP funcionando:

```
const http = require('http');

http.createServer((req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/plain' });
  res.end('Hola mundo');
}).listen(9000, 'localhost');
```

- **Rediccionamiento:**

  ```javascript
  const http = require('http');
  
  http.createServer((req, res) => {
    res.writeHead(301, {
      'Location': 'http://www.google.es/'
    });
    res.end();
  }).listen(8080, 'localhost');
  ```

- **Ping (petición http):**

  ```javascript
  const http = require('http');
  
  // Ping
  function ping(host) {
    http.get(host, (response) => {
        console.log(`La respuesta de ${host} es ${response.statusCode}`)
    }).on('error', (e) => {
        console.log('Tenemos un error!! -', e.message);
    });
  }
  ping('http://www.google.com');
  ```

- **LLamada a una API para obtener un JSON**

  ```javascript
  function getJSON(endpoint) {
    return new Promise((resolve, reject) => {
        http.get(endpoint, (response) => {
            let data = '';
            
            response.on('data', (chunk) => {
                data += chunk;
            }).on('end', () => {
                try {
                    data = JSON.parse(data);
                    resolve(data);
                } catch(error) {
                    reject(error);
                }
            });
        }).on('error', reject);
    });
  }
  
  getJSON('http://ghibliapi.herokuapp.com/films/').then(console.log, console.error);