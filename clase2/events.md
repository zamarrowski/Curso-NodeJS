# Events

![events](https://github.com/Fictizia/Curso-Node.js-para-desarrolladores-Front-end_ed8/raw/master/assets/event-loop-simple.png)

- Patrón Observador
- Similar al navegador

- **Suscribiendonos a eventos**
	- Sin eventos

	```javascript
	const http = require('http');
	
	const server = http.createServer((request, response) => {
		response.writeHead(200, {'Content-Type': 'text/plain'});
		response.end('¡Hola people!');
	}).listen(8080);
	```

	- Con eventos

	```javascript
	const http = require('http');
	
	const server = http.createServer().listen(8080);
	
	server.on('request', (request, response) => {
		response.writeHead(200, {'Content-Type': 'text/plain'});
		response.end('¡Hola people!');
	});
	```

- **Ejemplo sencillo: Creando nuestros eventos**

  ```javascript
  const events = require('events');
  const EventEmitter = events.EventEmitter;
  
  const ee = new EventEmitter(); 
  ee.on('current-date', (date) => { 
     console.log(date); 
  }); 
  setInterval(() => { 
     ee.emit('current-date', Date.now()); 
  }, 500);
  ```

- **Ejemplo: Juguemos al Ping-Pong**

  ```javascript
  const { EventEmitter } = require('events');
  const pingPong = new EventEmitter();
  
  let pingNumero = 1;
  
  console.log('Bienvenido al juego de Ping/Pong!');
  console.log('Empezamos en 5 segundos....');
  
  setTimeout(() => {
    console.log('Primer Ping... que desencadenará el juego');
    pingPong.emit('ping', pingNumero);
    pingNumero++;
  }, 5000);
  
  pingPong.on('ping', (numero) => {
    console.log('Llegó el Ping('+numero+'). Emitimos Pong');
    setTimeout(() => pingPong.emit('pong'), 1000);
  });
  
  pingPong.on('pong', () => {
    console.log('Llegó el Pong. Emitimos Ping');
    setTimeout(() => {
      pingPong.emit('ping', pingNumero);
      pingNumero++;
    }, 1000);
  });
  ```

### Repasar los conceptos clave

**Loop**

![loop](https://github.com/Fictizia/Curso-Node.js-para-desarrolladores-Front-end_ed8/raw/master/assets/nodejs-loop-simple.png)

- [The JavaScript Event Loop: Explained](http://blog.carbonfive.com/2013/10/27/the-javascript-event-loop-explained/)

![loop](../assets/nodejs-loop-complex.png)

- [Entendiendo el Event Loop](https://medium.com/the-node-js-collection/what-you-should-know-to-really-understand-the-node-js-event-loop-and-its-metrics-c4907b19da4c)

**Arquitecura diferente**

![](https://github.com/Fictizia/Curso-Node.js-para-desarrolladores-Front-end_ed8/raw/master/assets/event-loop-arch.png)


**Single Thread**
![](https://github.com/Fictizia/Curso-Node.js-para-desarrolladores-Front-end_ed8/raw/master/assets/single-thread.png)


**Multi Thread**
![](../assets/multi-thread.png)
