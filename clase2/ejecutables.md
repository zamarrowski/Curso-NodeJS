# Creando ejecutables

- Solo para entornos UNIX

- Necesitamos *shebang*
  
  > Shebang es, en la jerga de Unix, el nombre que recibe el par de caracteres #! que se encuentran al inicio de los programas ejecutables interpretados.

  ```javascript
  #!/usr/bin/env node
  console.log('Soy un script!');
  ```

- Necesitamos hacer el script ejecutable

  ```
  chmod +x mi_escript_archivo.js
  ```

- Ejecutando el script

  ```
  ./mi_escript_archivo.js <parámetro>
  ```

- **Ejemplo: Hello world!**

  ```javascript
  #!/usr/bin/env node
  console.log('Hello World!');
  process.exit(1); // Por defecto la salida es '1'
  ```

**Arrancar Scripts al incio del sistema**
- Librerías:
  - [node-upstarter](https://github.com/carlos8f/node-upstarter) 

