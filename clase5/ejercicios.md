# Ejercicios

1. Descargar este archivo: [restaurants.json](https://www.w3resource.com/mongodb-exercises/retaurants.zip)
    * Copiar el archivo al contenedor:
    ```
    docker cp retaurants.json d71f1bb62f12:./
    ```
    * Entrar al contenedor como bash
    * Cargar json en el Mongo:
    ```
    mongoimport --db fictizia --collection restaurants --file retaurants.json
    ```
    * Comprobar que los registros se han añadido correctamente
    * Realizar una consulta en mongo que saque todos los registros
    * Sacar los restaurante de la calle "Morris Park Ave"
    * Write a MongoDB query to display all the documents in the collection restaurants. Go to the editor
    * Write a MongoDB query to display the fields restaurant_id, name, borough and cuisine for all the documents in the collection restaurant.
    * Write a MongoDB query to display the fields restaurant_id, name, borough and cuisine, but exclude the field _id for all the documents in the collection restaurant. Go to the editor
    * Write a MongoDB query to display the fields restaurant_id, name, borough and zip code, but exclude the field _id for all the documents in the collection restaurant. Go to the editor
    * Write a MongoDB query to display all the restaurant which is in the borough Bronx. Go to the editor

2. Con la base de datos anterior:
    * Crear un endpoint que te devuelva todos los restaurante pero solo el nombre
    * Crear un endpoint que borre un restaurante
    * Crear un endpoint que te devuelva el detalle de un restaurante
    * Crear un endpoint que busque por nombre
