# Ejercicios

1. Crear un servidor con express:
  - Crear un middleware que:
    - Si el usuario envia la cabecera Authorizartion: AbCdEf123456 devolveremos un mensaje de bienvenido.
    - Si el usuario no envia la cabecera Authorization mostraremos un mensaje de loguearse, por favor.
    - En caso de que mande la cabecera con otro contenido devolveremos un 401.

2. Crer un CRUD de usuarios que se guarda en memoria:
  - GET -> listado de usuarios (/users)
  - GET -> detalle de un usuario por id (/users/:id)
  - POST -> Crear usuario (/users)
  - PUT -> Edita un usuario por id (/users/:id)
  - DELETE -> Borra un usuario por id (/users/:id)

3. Crear un servidor y usar Pug para:
  - Si hacemos un GET a /users devolver una lista de usuarios con nombre, apellido y edad
  - Si hacemos un GET a /auth devolver un mensaje de logueado si mandar la cabecera Authorization AbCdEf123456
  - Si hacemos un GET a /auth devolver un mensaje de logueate si no mandar la cabecera Authorization AbCdEf123456
  - Si hacemos un POST a /template con un objeto como este:
    ```javascript
      let user = {
        name: 'Sergio',
        firstName: 'Zamarro',
        age: 26,
        dog: {
          name: 'India'
        }
      }
    ```
    Devolver un mensaje como este:
    > Me llamo Sergio Zamarro y tengo 26 años.
    > Tengo un perro genial llamado India

En caso de que no tenga perro mostrar un mensaje como este:

    > Me llamo Sergio Zamarro y tengo 26 años.
    > Ojalá tuviese perro

En caso de ser menor de edad devolver un mensaje como este:

    > Me llamo Sergio Zamarro y soy demasiado pequeño como para saber que es esto.
    > Ojalá tuviese perro


 