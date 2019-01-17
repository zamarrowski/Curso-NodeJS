# File System

- **Leer un archivo**

  ```javascript
  const fs = require('fs');
  
  fs.readFile('archivo.txt', 'utf8', (err, data) => {
    if (!err) {
      console.log(data);
    } else {
      throw err;
    }
  });
  ```

- **Escribir un archivo**

  ```javascript
  const fs = require('fs');

  const data = "y esto... se guardará en 'test.txt'";

  fs.writeFile('test.txt', data, (err) => {
    if (!err) {
      console.log('Datos guardados en el \'test.txt\'');
    } else {
      throw err;
    }
  });
  ```

- **Usando Promesas y Callbacks**

  ```javascript
  const fs = require('fs');
  
  // Con CallBacks!
  fs.readFile('./README.md', (error, content) => {
    console.log('Leyendo el archivo...');
    fs.writeFile('./length.txt', content.length, (error) => {
      if (error) {
        console.log('error! ', error);
      } else {
        console.log('Terminado... hemos almacenado una cadena que vale ', content.length);
      }
    });
  });

  // Con Promesas!
  function leerArchivo (file) {
    return new Promise((resolve, reject) => {
      fs.readFile(file, (error, contenido) => {
        console.log('Empezando la lectura de ', file);
        if (error) {
          console.log('Error en la lectura');
          return reject(error);
        }
        console.log('Lectura finalizada en ', file);
        resolve(contenido);
      });
    });
  }

  function escribirArchivo(file, content) {
    return new Promise((resolve, reject) => {
      fs.writeFile(file, content, (error) => {
        if(error) {
  				console.log('Error en la escritura de ', file);
  				return reject(error);
  			}
  			console.log('Escritura Termianda en ', file);
  			resolve();
  		});
  	});
  }

  //Opción1
  leerArchivo('./miArchivo.txt')
    .then((content) => {
        escribirArchivo('./longitud.txt', content);
    }, (error) => {
    	console.log('Promesas con errores: ');
    	console.log(error);
    });

  //Opción2
  Promise.all([
  	leerArchivo('./otros.txt'),
  	leerArchivo('./usuarios.txt'),
  	leerArchivo('./mas_cosas.txt')
	]).then((respuestas) => {
		console.log('Tenemos un total de '+respuestas.length+' respuesta/s.');
		console.log('El primero tiene '+respuestas[0].length+' caracteres');
		console.log('El segundo tiene '+respuestas[1].length+' caracteres');
		console.log('El tercero tiene '+respuestas[2].length+' caracteres');
	});

  //Opcion3
  Promise.race([
  	leerArchivo('./otros.txt'),
  	leerArchivo('./usuarios.txt'),
  	leerArchivo('./mas_cosas.txt')
	]).then((respuesta) => {
		console.log('El más rápido tiene solo '+respuesta.length+' caracteres.');
	});
  ```

- **Ejemplo utilizando la librería [Q](https://github.com/kriskowal/q)**

  ```javascript
  const fs = require('fs');
  const Q = require('q');
  const readFile = Q.denodeify(fs.readFile);
  
  // Con CallBacks!
  readFile('./README.md').then(content) => {
    console.log('El contenido es:', content);
  }, (error) => {
    console.log('error! ', error);
  });
  ```

- **[Más métodos para:](https://nodejs.org/api/fs.html)**
	- Síncronos
	- Escucha de cambios
	- Manipulación de carpetas
	- Comprobación de ficheros/directorios
	- etc...
