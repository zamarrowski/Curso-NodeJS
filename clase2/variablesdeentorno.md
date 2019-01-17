# Variables del Entorno

- Conocer todas las variables disponibles en el entorno
  - Windows: 

  ```
  SET
  ```

  - UNIX: 

  ```
  env
  ```

- Guardar nuevas variables en el entorno
  - Windows: 

  ```
  SET ALGO='mi secreto'
  ```

  - UNIX: 

  ```
  export ALGO='mi secreto'
  ```
  
- Recuperar las variables con Node.js

  ```javascript
  const datoRecuperado = process.env.ALGO;
  console.log(process.env.ALGO);
  ```

- Creando variables del entorno limitadas a Node.js y temporales (SOLO UNIX)
  - Arrancando...   

  ```
  NODE_ENV=production node app.js
  ```

  - Usando datos...

  ```javascript
  if(process.env.NODE_ENV === "production"){
    console.log("Entramos en modo producción");
  } else if (process.env.NODE_ENV === "development"){
    console.log("Entramos en modo desarrollo");
  } else {
    console.log("Entramos en modo desconocido. ¡Revisa las variables del entorno!");
  }
  ```  
  
- **Alternativas**
  - [dotenv - librería para Nodejs](https://github.com/motdotla/dotenv)
