# Express


![Express_logo](https://github.com/Fictizia/Curso-Node.js-para-desarrolladores-Front-end_ed8/blob/master/assets/express.png)

**Influencias / usos**
- Otros frameworks similares:
  - Zend (PHP)
  - Django (Python)
  - Sinatra (Ruby)

- Uso:
  - API JSON
  - Single Page Applications
  - App tiempo real

**Pros**
- Rutas
- Parámetros
- Formularios y subida de ficheros
- Cookies
- Sesiones
- Templates
- Middlewares

**Contras**
- Base de datos / ORM
- Autenticación de usuarios
- Seguridad
- Migraciones
- Deployment
- Organización del código

**Migraciones**
- [De Express 3.x a Express 4.x](http://expressjs.com/es/guide/migrating-4.html)
  - [Documentación de la 3.x (desuso)](http://expressjs.com/es/3x/api.html)
  - [Cambios](http://expressjs.com/es/guide/migrating-4.html)
  - [Nuevas funcionaldiades](https://github.com/expressjs/express/wiki/New-features-in-4.x?_ga=1.226364894.554285759.1461232316)
- [De Express 4.x a Express 5.x (hoy es Alpha)](http://expressjs.com/es/guide/migrating-5.html)
  - [Cambios Previstos](https://github.com/expressjs/express/pull/2237?_ga=1.29731835.554285759.1461232316)


**Instalación**

- Instalación local:

  ```
  npm install express
  ```

- Instalación global:

  ```
  npm install -g express
  ```

- Instalación versiones anteriores:

  ```
  npm install -g express@3.x
  ```

**Hello World!**

  ```javascript
  const express= require('express');
  const app = express();
  
  app.get('/', (req, res) => res.send('Hello World!'));
  
  app.listen(8080, () => console.log('Example app listening on port 8080'));
```

- Métodos HTTP: delimitando a un único método

  ```javascript
  app.get('/', (req, res, next) => {
    res.send('Solo get como método me vale...');
  });
  ```

- Métodos HTTP: Otra forma de delimitar a un método 

  ```javascript
  app['m-search']('/', (req, res, next) => {
    res.send('Solo m-search como método me vale...');
  });
  ```

- Métodos HTTP: permitiendo todos los métodos

  ```javascript
  app.all('/', (req, res, next) => {
    res.send('Cualquier método me vale...');
  });
  ```

- Rutas: Raiz `http://localhost:8080/`

  ```javascript
  app.get('/', (req, res, next) => {
    res.send('Esto es la Raiz');
  });
  ```
- Rutas: Básicas http://localhost:8080/hola

  ```javascript
  app.get('/hola', (req, res, next) => {
    res.send('Esto es /hola');
  });
  ```

- Rutas: Capturando Parámetros `http://localhost:8080/hola/Eduardo`, `http://localhost:8080/hola/Oscar`, ...

  ```javascript
  app.get('/hello/:nombre', (req, res) => {
      res.send('Hola ' + req.nombre + '!');
  });
  ```
- Rutas: Capturando varios parámetros `http://localhost:8080/desde/Madrid/a/Malga`, `http://localhost:8080/desde/Madrid/a/NYC`

  ```javascript
    app.get('/desde/:origen/a/:destino', (req, res, next) => {
      res.send('Quieres ir de ' + req.params.origen + ' a ' + req.params.destino);
    });
  ```
- Rutas: Capturando varios parámetros y alguno determiando `http://localhost:8080/mensaje/1/editar`, `http://localhost:8080/mensaje/500/borrar`, ...

  ```javascript
    app.get('/mensaje/:id/:accion(editar|borrar)', (req,res,next) => {
      res.send('Quieres ' + req.params.accion + ' el mensaje numero ' + req.params.id);
    });
  ```

- Rutas: Parámetros opcionales `http://localhost:8080/user/1/editar`, `http://localhost:8080/user/500/borrar`, ...

  ```javascript
  app.get('/user/:id/:comando?', (req, res, next) => {
    if(req.params.comando){
      res.send("Tenemos algo! Quieres " + req.params.comando);
    } else {
      res.send("Nada de nada...");
    }
  });
  ```
  
- Rutas: Más parámetros opcionales http://localhost:8080/user/1.pdf, http://localhost:8080/user/500.zip, etc...

  ```javascript
  app.get('/user/:id.:formato?', (req, res, next) => {
    if(req.params.formato){
      res.send("["+req.params.formato+"] Extensión requerida... ");
    } else {
      res.send("Sin Extensión requerida");
    }
  });
  ```

- Rutas: Tipo fichero `http://localhost:8080/hola.text`

  ```javascript
  app.get('/hola.text', (req, res) => {
    res.send('Hola');
  });
  ```

- Rutas: Patrones de serie (?) *http://localhost:8080/acd o http://localhost:8080/abcd*

  ```javascript
  app.get('/ab?cd', (req, res) => {
    res.send('ab?cd');
  });
  ```

- Rutas: Patrones de serie (+) *http://localhost:8080/abcd, http://localhost:8080/abbbbbcd, etc...*

  ```javascript
  app.get('/ab+cd', (req, res) => {
    res.send('ab+cd');
  });
  ```

- Rutas: Patrones de serie (*) *http://localhost:8080/abcd, http://localhost:8080/abAALGOOOcd, etc...*

  ```javascript
  app.get('/ab*cd', (req, res) => {
    res.send('ab*cd');
  });
  ```

- Rutas: Patrones de serie (()) *http://localhost:8080/abe o http://localhost:8080/abcd*
  
  ```javascript
  app.get('/a(bc)d', (req, res) => {
    res.send('a(bc)d');
  });
  ```

- Rutas: Expresiones regulares *http://localhost:8080/mcfly, http://localhost:8080/dragonfly, etc...*

  ```javascript
  app.get(/.*fly$/, (req, res) => {
    res.send('/.*fly$/');
  });
  ```

- Rutas: Molularidad con app.route()

  ```javascript
  app.route('/pelicula')
    .get((req, res) => {
      res.send('todas las peliculas...');
    })
    .post((req, res) => {
      res.send('Añadir una pelicula...');
    })
  ```

- Manejadores: Función individual

  ```javascript
  app.get('/example/a', (req, res) => {
    res.send('Hola desde A!');
  });
  ```

- Manejadores: Dos funciones individuales

  ```javascript
  app.get('/example/b', (req, res) => {
    console.log('La respuesta se enviará a la siguiente función...');
    next();
  }, (req, res) => {
    res.send('Hola desde B!');
  });
  ```

- Manejadores: Matrices

  ```javascript
  const cb0 = (req, res, next) => {
    console.log('CB0');
    next();
  };
  
  const cb1 = (req, res, next) => {
    console.log('CB1');
    next();
  };
  
  const cb2 = (req, res) => {
    res.send('Hola desde C!');
  };
  
  app.get('/example/c', [cb0, cb1, cb2]);
  ```

- Manejadores: Matrices y funciones individuales

  ```javascript
  const cb0 = (req, res, next) => {
    console.log('CB0');
    next();
  };
  
  const cb1 = (req, res, next) => {
    console.log('CB1');
    next();
  };
  
  app.get('/example/d', [cb0, cb1], (req, res, next) => {
    console.log('La respuesta se enviará a la siguiente función...');
    next();
  }, (req, res) => {
    res.send('Hola desde D!');
  });
  ```

- Manejadores: Objeto petición
  - `req.ip` *Almacena la IP desde donde se realizó la peticioón*
  - `req.is` *Que tipo de datos nos llegan desde la petición. Booleano*

    ```javascript
    req.is('json');
    req.is('application/*');
    req.is('application/json');
    ```
  - `req.params` *Contenido de la ruta (http://localhost:8080/usuarios/:id)*
  - `req.query` *Contenido de la consulta de la URL (http://localhost:8080/peliculas?categoria=Ficcion&director=George+Lucas)*
    - simples (http://localhost:8080/peliculas?categoria=Ficcion&director=George+Lucas):
    ```javascript
    app.get('/peliculas', function(req,res,next){
      console.log(req.query.director) // George Lucas
      console.log(req.query.categoria) // Ficcion
    });
    ```
    - Agrupados (http://localhost:8080/peliculas?categoria[tipo]=Corto&director=Yo+Mismo):
    ```javascript
    app.get('/peliculas', function(req,res,next){
      console.log(req.query.director) // Yo Mismo
      console.log(req.query.categoria.tipo) // Corto
    });
    ```
  - `req.body` *Contenido dentro de la propia petición*

- Manejadores: Métodos de respuesta
  - [res.download()](http://expressjs.com/es/4x/api.html#res.download) *Solicita un archivo para descargarlo.*
  - [res.end()](http://expressjs.com/es/4x/api.html#res.end) *Finaliza el proceso de respuesta.*
  - [res.json()](http://expressjs.com/es/4x/api.html#res.json) *Envía una respuesta JSON.*
  - [res.jsonp()](http://expressjs.com/es/4x/api.html#res.jsonp) *Envía una respuesta JSON con soporte JSONP.*
    - Valores por defecto ajustables en app.set()
      - *?callback=* valor por defecto en la petición
      - `res.jsonp({date: newDate()});`
  - [res.redirect()](http://expressjs.com/es/4x/api.html#res.redirect) *Redirecciona una solicitud.*
  - [res.render()](http://expressjs.com/es/4x/api.html#res.render) *Renderiza una plantilla a la que le pasa además datos (opcional)*
  - [res.send()](http://expressjs.com/es/4x/api.html#res.send) *Envía una respuesta de varios tipos.*
    - Muy flexible
      - Código y contenido `res.send(404,'Oops...');`
      - Enviar un JSON `res.send({mensaje: "secreto"});`
      - Solo código (autocompleta el mensaje) `res.send(200);` 


  - [res.sendFile()](http://expressjs.com/es/4x/api.html#res.sendFile) *Envía un archivo para ser visualizado.*
  - [res.sendStatus()](http://expressjs.com/es/4x/api.html#res.sendStatus) *Envía un archivo para ser descargado.*


**Mecánica: app.use()**
- Usando Middleware: app.use(middleware)
  - Declaración directa 

    ```javascript
    app.use((req, res, next) => {
        console.log("Petición en "+req.url+" con el método" + req.method);
        next(); 
    });
    ```

  - Enlazando

    ```javascript
    const express = require('express');
    const app = express();
    
    function chivato (req, res, next) {
        console.log(`Nueva petición en ${req.url} con el método ${req.method}`);
        next(); 
    };
    
    app.use(chivato);

    app.get('/', (req, res) => {
      res.send('Hola a todos!');
    });
    
    app.listen(3000);    
    ```

**Middleware: La clave**

![Mw_schema](../assets/middleware.jpg)

Una función que recibe 3 o 4 parámetros: req, res, next

- Tipos:
  - Middleware de nivel de aplicación
  - Middleware de nivel de direccionador
  - Middleware de manejo de errores
  - Middleware incorporado
  - Middleware de terceros

- Concatenación:
  - Al terminar su tarea, tiene que invocar a next()


**Middleware de nivel de aplicación**
- Global *Afecta a cualquier Ruta*

  ```javascript
  const app = express();
  
  app.use((req, res, next) => {
    console.log('Time:', Date.now());
    next();
  });
  ```

- Punto de Montaje *Afecta solo a una vía de acceso, en este caso /user/:id*

  ```javascript
  const app = express();
  
  app.get('/user/:id', (req, res, next) => {
    console.log('ID:', req.params.id);
    next();
  }, (req, res, next) => {
    res.send('User Info');
  });
  ```

**Middleware de nivel de direccionador**
- Global *Afecta a cualquier Ruta*

  ```javascript
  const app = express();
  const router = express.Router();
  
  router.use((req, res, next) => {
    console.log('Time:', Date.now());
    next();
  });
  ```

- Punto de Montaje *Afecta solo a una vía de acceso, en este caso /user/:id*

  ```javascript
  const app = express();
  const router = express.Router();
  
  router.get('/user/:id', (req, res, next) => {
    console.log('ID:', req.params.id);
    next();
  }, (req, res, next) => {
    res.send('User Info');
  });
  ```

**Middleware de manejo de errores**
- Argumento adiccional

  ```javascript
  const bodyParser = require('body-parser');
  const methodOverride = require('method-override');
  
  app.use(gestionErrorServer);
  
  function gestionErrorServer(err, req, res, next) {
    if (req.xhr) {
      res.status(500).send({ error: 'Something failed!' });
    } else {
      res.status(500);
      res.render('error', { error: err });
    }
  }
  
  //...
  ```

**Middleware incorporado**
- Desde la versión 4.x Express no depende de [Connect](https://github.com/senchalabs/connect)
- Solamente queda incorporado [express.static](https://github.com/expressjs/serve-static)
  - Incluyendo archivos estáticos

    ```javascript
    app.use(express.static('public'));
    ```

  - Configurando la carpeta pública

    ```javascript
    const options = {
      dotfiles: 'ignore',
      etag: false,
      extensions: ['htm', 'html'],
      index: false,
      maxAge: '1d',
      redirect: false,
      setHeaders(res, path, stat) {
        res.set('x-timestamp', Date.now());
      }
    }
    
    app.use(express.static('public', options));
    ```

  - Usando múltiples directorios estáticos

    ```javascript
    app.use(express.static('public'));
    app.use(express.static('uploads'));
    app.use(express.static('files'));
    ```


- Middleware oficial (No incorporado):
  - [serve-favicon](https://github.com/expressjs/serve-favicon)
    - Sirve el favicon
  - [Morgan](https://github.com/expressjs/morgan)
    - Logger para peticiones HTTP
  - [body-parser](https://github.com/expressjs/body-parser)
    - Decodifica:
      - application/json
      - application/x-www-form-urlencoded
      - multipart/form-data
    - Crea el objeto req.body con los parámetros
    - Crea el objeto req.files con los ficheros que se han subido desde un formulario
  - [basic-auth-connect](https://github.com/expressjs/basic-auth-connect)
    - Protección básica de las rutas usando usuario y contraseña
  - [csurf](https://github.com/expressjs/csurf)
    - Crea *req.session._csrf* 
    - Protección contra Cross-site request forgery
    - Usando tokens
  - [cors](https://github.com/expressjs/cors)
    - Gestión de Cross Origin Resource Sharing (CORS)
  - [compression](https://github.com/expressjs/compression)
    - [gzip](https://www.wikiwand.com/es/Gzip)
  - [express-session](https://github.com/expressjs/session)
    - Simple gestor de sesiones 
  - [multer](https://github.com/expressjs/multer)
    - *Node.js middleware for handling `multipart/form-data`.*
  - [cookie-session](https://github.com/expressjs/cookie-session)
    - *Simple cookie-based session middleware*
  - [cookie-parser](https://github.com/expressjs/cookie-parser)
    - *cookie parsing middleware*
    - Crea req.cookies
  - [cookie-session](https://github.com/expressjs/cookie-session)
    - Inicializa y parsea los datos de sesión del usuario
    - Utilizando cookies como almacenamiento
    - Algunas opciones avanzadas
  - [serve-static](https://github.com/expressjs/serve-static)
    - *Serve static files*
    - ¡Muy útil! Se pone cerca del final
    - Cachea los ficheros
    - La variable global __dirname contiene el directorio donde reside el script en ejecución
  - [vhost](https://github.com/expressjs/vhost)
    - Virtual Domain Hosting
  - [restful-router](https://github.com/expressjs/restful-router)
    - *Simple RESTful url router.*
  - [connect-markdown](https://github.com/expressjs/connect-markdown)
    - *Auto convert markdown to html for connect.*

**Middleware: Más Middleware, más funcionalidad**
- [La lista de Raynos](https://github.com/Raynos/http-framework)

- Habilitando CORS

  ```javascript
  app.use(function(req, res, next) {
    res.header("Access-Control-Allow-Origin", "*");
    res.header('Access-Control-Allow-Methods', 'GET,PUT,POST,DELETE');
    res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
    next();
  });
  ```

- Baneando Navegadores (IE8 y anteriores)

  ```javascript
  // ban.js
  const banned = [ 'MSIE', 'Trident/6.0'];
  
  module.exports = () => (req, res, next) =>{
    if (req.headers['user-agent'] !== undefined && req.headers['user-agent'].indexOf(banned) > -1) {
      res.end('Navegador no compatible');
    } else { 
      next(); 
    }
  };
  ```

- Mapeado de parámetros en rutas.
  - Cuidado con app.param()
    - Funcionamiento (orden de busqueda):
      - req.params
      - req.body
      - req.query

    ```javascript
    app.param('id_usuario', (req, res, next, id) =>{
      // Llamamos a una función que valida....
      validadorUsuario(id, (err, usuario) => {
        if (err) { 
          next(err);
        } else if (user) { 
          // Actualizamos con los nuevos datos
          req.params.usuario = usuario; 
          // damos paso a la siguiente función
          next();
        } else {
          next(new Error('Error al cargar el usuario'));
        } 
      });
    });
    ```

-  Redireccionando al usuario en caso de no estar logados

  ```javascript
  module.exports = (req, res, next) => {
    if (req.params.usuario.logged){
      next();
    } else {
      res.redirect('/login');
    }
  };
  ```

- Gestion de errores tipo 4xx y tipo 5xx

  ```javascript
  // Error 404
  app.use((req, res) => {
    res.status(400);
    res.render('404', { title: '404 - No encontrado' });
  });
  
  // Error 500 (solo en caso de desarrollo)
  app.use('development', (error, req, res, next) => {
    res.status(500);
    res.render('500', {
      title: 'Jefe, ¡Tenemos un 500!',
      error: error
    });
  });
  
  
  // Error 500 (solo en caso producción)
  app.use('production', (error, req, res, next) => {
    res.status(500);
    res.render('500', {
      title: 'Oops… ¡Algo salió mal!'
    });
    // Mandamos un email con los datos al equipo.
  });
  ```

**[Ejemplos con Express](https://github.com/expressjs/express/tree/master/examples)**


**Express en resumen**

- GET Básico

  ```javascript
  app.get('/hola', (req, res) => {
      res.send('hemos abierto una nueva ruta!');
  });
  ```

- POST Básico
  - app.js 

    ```javascript
    app.post('/', (req, res) => {
      res.send(req.body);
    });
    ```

- Parámetros en las rutas
  - app.js 

    ```javascript
    app.get('/hola/:usuario', (req, res) => {
        res.send(`Hola ${req.params.usuario}. Hemos abierto una nueva ruta personalizada!`);
    });
    ```
