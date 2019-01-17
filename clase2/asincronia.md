# Asincronía:

> El modelo de programación de Node.js es monohilo, asíncrono y dirigido por eventos. 
1. No puede haber código bloqueante o todo el servidor quedará bloqueado y esto incluye no responder a nuevas peticiones entrantes.
2. La asincronicidad implica que no sabemos cuándo ni en que orden se va a ejecutar el código, generalmente esto no es importante pero en ocasiones sí lo es y habrá que tenerlo en cuenta.
3. En caso de error inesperado debemos capturarlo y controlar el posible estado en que haya podido quedar la ejecución del código.
> Nicolas Nombela en [nnombela](http://nnombela.com/blog/2012/03/21/asincronicidad-en-node-dot-js/)

- **Síncrono - código bloqueante:**

  ```javascript
  const http = require('http');
  let numeroPeticion = 1
    
  function writeResponse(response) {
    response.writeHead(200, {'Content-Type': 'text/plain'});
    response.write('Hola Mundo!, numero de peticion ', numeroPeticion);
    response.end();
    console.log('Se termino... ', numeroPeticion);
  }
    
  function sleepSynch(seconds, response) {
    const startTime = new Date().getTime();
    while (new Date().getTime() < startTime + Math.floor((Math.random() * 1000) + 500) * seconds) {
      // Nada pasa....
    }
    writeResponse(response);
  }
    
  http.createServer(function(request, response) {
    console.log('Empezo...', numeroPeticion);
    sleepSynch(10, response);
    numeroPeticion++;
  }).listen(8080);
  ```

- **Asíncrono - timeOut()**

  ```javascript
  const http = require('http');

  function writeResponse(response, i) {
    response.writeHead(200, {'Content-Type': 'text/plain'});
    response.write('Hola Mundo!');
    response.end();
    console.log(`Se termino ${i}...`);
  }

  function sleepAsynch(seconds, i, response) {
    setTimeout(function() {
      writeResponse(response, i);
    }, 3000);
  }

  let index = 1;

  http.createServer((request, response) => {
    const i = index++;
    console.log(`Empezo ${i}...`);
    sleepAsynch(10, i, response);
  }).listen(8080);
  ```
