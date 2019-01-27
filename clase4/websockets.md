# Websockets

> WebSocket es una tecnología que proporciona un canal de comunicación bidireccional y full-duplex sobre un único socket TCP. Está diseñada para ser implementada en navegadores y servidores web, pero puede utilizarse por cualquier aplicación cliente/servidor.

![WS_Sockets](https://github.com/Fictizia/Curso-Node.js-para-desarrolladores-Front-end_ed8/blob/master/assets/websocket.png)
- Protocolo de comunicación que se negocia sobre HTTP
- Full-duplex
- Única conexión permanente (siempre conectado)
- Stream de mensajes
- Contenido en tiempo real
- Orientado a "eventos" (mensajes)
- Baja latencia

**Entendiendo los eventos**

![Sockets](https://github.com/Fictizia/Curso-Node.js-para-desarrolladores-Front-end_ed8/raw/master/assets/websockets-guides.png)


**Negociación del protocolo WebSocket**

> Para establecer una conexión WebSocket, el cliente manda una petición de negociación WebSocket, y el servidor manda una respuesta de negociación WebSocket, como se puede ver en el siguiente ejemplo:
> [WebSockets en Wikiwand](https://www.wikiwand.com/es/WebSocket)

- Cliente:

  ```
  GET /demo HTTP/1.1
  Host: example.com
  Connection: Upgrade
  Sec-WebSocket-Key2: 12998 5 Y3 1 .P00
  Sec-WebSocket-Protocol: sample
  Upgrade: WebSocket
  Sec-WebSocket-Key1: 4 @1 46546xW%0l 1 5
  Origin: http://example.com

  ^n:ds[4U
  ```

- Servidor:
  
  ```
  HTTP/1.1 101 WebSocket Protocol Handshake
  Upgrade: WebSocket
  Connection: Upgrade
  Sec-WebSocket-Origin: http://example.com
  Sec-WebSocket-Location: ws://example.com/demo
  Sec-WebSocket-Protocol: sample

  8jKS'y:G*Co,Wxa-
  ```

![handshake](https://github.com/Fictizia/Curso-Node.js-para-desarrolladores-Front-end_ed8/raw/master/assets/websocket-handshake.gif)

> Los 8 bytes con valores numéricos que acompañan a los campos Sec-WebSocket-Key1 y Sec-WebSocket-Key2 son tokens aleatorios que el servidor utilizará para construir un token de 16 bytes al final de la negociación para confirmar que ha leído correctamente la petición de negociación del cliente.

### WS: Nativo

- [Soporte](http://caniuse.com/#search=websocket)
- [Documentación en MDN](https://developer.mozilla.org/en-US/docs/Web/API/WebSocket)

**Abrir la conexión**

```javascript
var myWebSocket = new WebSocket("ws://www.websockets.org");
```

**Gestión de Eventos**

- Siempre dispondremos del parámetro event.

  ```javascript
  myWebSocket.onopen = function() { console.log("Connection open ..."); };
  myWebSocket.onmessage = function(evt) { console.log( "Received Message: ", evt.data); };
  myWebSocket.onclose = function() { console.log("Connection closed."); };      
  ```

**Envio de mensajes**

```javascript
myWebSocket.send("Hello WebSockets!");
```

**Cerrar la conexión**

```javascript
myWebSocket.close();
```

### Socket.io

![Sockets](https://github.com/Fictizia/Curso-Node.js-para-desarrolladores-Front-end_ed8/raw/master/assets/socketio.png)

Caracrerísticas:
- Fácil
- Soporte a navegadores obsoletos (Fallback)
- Popular
- Extraordinariamente simple

#### Client side

**Abrir la conexión**

```html
<script src="/socket.io/socket.io.js"></script>
<script>
  const socket = io();
</script>
```

**Gestión de Eventos**

```javascript
socket.on('my-event', (data) => { 
  console.log('Received Message:', data); 
});
```

- **Eventos reservados**:
  - `connect/connection`

    ```javascript
    socket.on('connect', (socket) => {
      // ...
    });
    ```

  - `disconnect`

    ```javascript
    socket.on('disconnect', (socket) => {
      // ...
    });
    ```

  - `error`

    ```javascript
    socket.on('error', (error) => {
      // ...
    });
    ```

  - [Más en la documentación](https://socket.io/docs/client-api/)

**Envio de mensajes**

```javascript
socket.emit('my-event', data);
```

**Cerrar la conexión**

```javascript
socket.disconnect();
socket.close();
// Si quieres reabrir. -> socket.connect();
```

#### Server Side

**Con HTTP directamente:**

```javascript
const server = require('http').createServer();
const io = require('socket.io')(server);

io.on('connection', (socket) =>{
  socket.on('event', (data) =>{
      // ...
  });
  socket.on('disconnect', (socket) =>{
      // ...
  });
});

server.listen(8080);
```

**Con Express:**
```javascript
const app = require('express')();
const server = require('http').createServer(app);
const io = require('socket.io')(server);

io.on('connection', () => {
    // ...
});

server.listen(8080);
```

**Eventos reservados**:
- `connect/connection`

  ```javascript
  io.on('connect', (socket) => {
    // ...
  });
    
  socket.on('connection', (socket) => {
    // ...
  });
  ```

- `disconnect`

  ```javascript
  io.on('connection', (socket) => {
    socket.on('disconnect', (reason) => {
      // ...
    });
  });
  ```

- `error`

  ```javascript
  io.on('connection', (socket) => {
    socket.on('error', (error) => {
      // ...
    });
  });
  ```
  
  - [Más en la documentación](https://socket.io/docs/server-api/)

**Cheatsheet `emit`**

```javascript
// sending to sender-client only
socket.emit('message', "this is a test");

// sending to all clients, include sender
io.emit('message', "this is a test");

// sending to all clients except sender
socket.broadcast.emit('message', "this is a test");

// sending to all clients in 'game' room(channel) except sender
socket.broadcast.to('game').emit('message', 'nice game');

// sending to all clients in 'game' room(channel), include sender
io.in('game').emit('message', 'cool game');

// sending to sender client, only if they are in 'game' room(channel)
socket.to('game').emit('message', 'enjoy the game');

// sending to all clients in namespace 'myNamespace', include sender
io.of('myNamespace').emit('message', 'gg');

// sending to individual socketid
socket.broadcast.to(socketid).emit('message', 'for your eyes only');
```

**Compartiendo sesión entre `express` y `socket.io`**

```javascript
const sessionMiddleware = session({
    store: new RedisStore({}), // XXX redis server config
    secret: "keyboard cat",
});

// express
app.use(sessionMiddleware);

// socket.io
io.use((socket, next) => {
    sessionMiddleware(socket.request, socket.request.res, next);
});
```

**Recursos**
- [Socket.io en Github](https://github.com/socketio/socket.io)
- [Socket.io - Express 3/4](http://socket.io/docs/#using-with-express-3/4)

### Nativo vs. Librerías

- [Differences between socket.io and websockets en Stackoverflow](http://stackoverflow.com/a/38558531)
- [WebSocket and Socket.IO by DWD](https://davidwalsh.name/websocket)
- [An Introduction to WebSockets by Matt West](http://blog.teamtreehouse.com/an-introduction-to-websockets)
