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

2. Con la base de datos anterior:
    * Crear un endpoint que te devuelva todos los restaurante pero solo el nombre
    * Crear un endpoint que borre un restaurante
    * Crear un endpoint que te devuelva el detalle de un restaurante
    * Crear un endpoint que busque por nombre
