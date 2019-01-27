# Herramientas

**Paquetes de interes global**

- node-inspector 
  - Instalación global.
  - Utilizar `debugger;` para lanzar las herrameintas de depuración del navegador.
  ```
  node-debug server.js
  ```
- nodemon
  - [Documentación](https://github.com/remy/nodemon#nodemon)
  - Relanza la aplicación por cada cambio que relaizemos
  ```
  npm install -g nodemon
  ```  
  ```
  nodemon server.js
  ```
- forever
  - Relanza la aplicación cuando deja de funcionar
  - Opciones adiccionales
  - Muy popular
  - [Docuemntación](https://github.com/foreverjs/forever)
  ```
    forever start/stop server.js
  ```
- pm2
  - Pensada para producción
  - Muchas opciones de configuración
  - Monitorización activa de muchos detalles clave de la aplicación
  - [Documentación](http://pm2.keymetrics.io/)
  ```
    pm2 start/stop server.js
  ```

**Otros**
- [formidable](https://www.npmjs.com/package/formidable)
- [fs-extra](https://www.npmjs.com/package/fs-extra)
- [mongose](http://mongoosejs.com/)
  - Driver para trabajr con MongoDB
- [node-mysql](https://github.com/felixge/node-mysql)
  - Facilita el trabajo con MySQL
- [Nodemailer](https://github.com/nodemailer/nodemailer)
  - Gestiona facilemnte el envio de e-mails
- [node-validator](https://github.com/chriso/validator.js)
  - Validación y sanitización de cadenas, especialmente pensado para formularios. 

**[Muchos Más (lista)](https://github.com/sindresorhus/awesome-nodejs/)**
