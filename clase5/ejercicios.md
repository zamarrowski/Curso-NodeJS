# Ejercicios

1. Descargar este archivo: [restaurants.json](https://www.w3resource.com/mongodb-exercises/retaurants.zip)
  1. Copiar el archivo al contenedor:
  ```
  docker cp retaurants.json d71f1bb62f12:./
  ```
  2. Entrar al contenedor como bash
  3. Cargar json en el Mongo:
  ```
  mongoimport --db fictizia --collection restaurants --file retaurants.json
  ```
  4. Comprobar que los registros se han añadido correctamente
  5. Realizar una consulta en mongo que saque todos los registros.
  6. Sacar los restaurante de la calle "Morris Park Ave"

2. Con la base de datos anterior:
  1. Crear un endpoint que te devuelva todos los restaurante pero solo el nombre
  2. Crear un endpoint que borre un restaurante
  3. Crear un endpoint que te devuelva el detalle de un restaurante
  4. Crear un endpoint que busque por nombre
