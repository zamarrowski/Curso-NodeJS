# MongoDB

![mongo](https://cdn-images-1.medium.com/max/1600/1*Ce0gUe0LbnhL7ebnDGTp5w.png)

[MongoDB](https://www.mongodb.com/es) es una base de datos NoSQL orientado a documentos y es de código abierto.

## Características principales:

* Consultas adhoc
* Indexación
* Replicación
* Balanceo de cargar o sharding
* Almacenamiento de archivos
* Agreggation framework
* Javascript!

## Relaciones en MongoDB

Uno de los puntos más criticados y menos comprendidos es las relaciones en MongoDB. MongoDB está pensado para usarse en bases de datos donde no haya muchas relaciones entre entidades.

1. Relaciones One-to-One: 

Imaginaemos que tenemos *una colección* de personas donde cada persona tiene una dirección:
```javascript
{
   _id: "joe",
   name: "Joe Bookreader"
}

{
   patron_id: "joe",
   street: "123 Fake Street",
   city: "Faketon",
   state: "MA",
   zip: "12345"
}
```

 En un modelo normal sacaríamos la dirección a otra tabla. En MongoDB para poder evitar esa consulta se embebe el documento: 

 ```javascript
 {
   _id: "joe",
   name: "Joe Bookreader",
   address: {
              street: "123 Fake Street",
              city: "Faketon",
              state: "MA",
              zip: "12345"
            }
}
 ```

 De esta forma cuando obtengamos el usuario, obtendremos la dirección.

2. Relaciones One-to-Many:

Ahora imaginemos que una persona puede tener varias direcciones. En un modelo normalizado tendríamos las direcciones en otra tabla referenciando al usuario. Alo así:
```javascript
{
   _id: "joe",
   name: "Joe Bookreader"
}

{
   patron_id: "joe",
   street: "123 Fake Street",
   city: "Faketon",
   state: "MA",
   zip: "12345"
}

{
   patron_id: "joe",
   street: "1 Some Other Street",
   city: "Boston",
   state: "MA",
   zip: "12345"
}
```

Si nuestra aplicacion necesita las direcciones de un usuario de manera frecuente tendríamos que hacer varias queries para obtener sus direcciones y los datos del usuario. Si embebemos las direcciones del usuario podríamos tener esta información en una sola query:

```javascript
{
   _id: "joe",
   name: "Joe Bookreader",
   addresses: [
                {
                  street: "123 Fake Street",
                  city: "Faketon",
                  state: "MA",
                  zip: "12345"
                },
                {
                  street: "1 Some Other Street",
                  city: "Boston",
                  state: "MA",
                  zip: "12345"
                }
              ]
 }
```

3. One-to-Many with references

Ahora imaginemos otro caso. Tenemos una entidad libros y otra editoriales. Una editorial puede tener muchos libros publicados y un libro tener solo una editorial. Si embebemos la editorial dentro del documento libro tendremos que lidiar con la repeticion de esta información en todos los libros de esa editorial. Si algún dia cambia de nombre tendríamos que actualizar todos los libros:
```javascript
{
   title: "MongoDB: The Definitive Guide",
   author: [ "Kristina Chodorow", "Mike Dirolf" ],
   published_date: ISODate("2010-09-24"),
   pages: 216,
   language: "English",
   publisher: {
              name: "O'Reilly Media",
              founded: 1980,
              location: "CA"
            }
}

{
   title: "50 Tips and Tricks for MongoDB Developer",
   author: "Kristina Chodorow",
   published_date: ISODate("2011-05-06"),
   pages: 68,
   language: "English",
   publisher: {
              name: "O'Reilly Media",
              founded: 1980,
              location: "CA"
            }
}
```

Lo mejor en este caso sería separar la colección editorial de la colección libro y referenciar de una a otra.

Para saber en que colección tenemos que poner esa referencia tenemos que pensar en si ese número de referencias va a crecer.
En caso de poner la referencia a los libros en la colección de editorailes tendríamos algo así:
```javascript
{
   name: "O'Reilly Media",
   founded: 1980,
   location: "CA",
   books: [123456789, 234567890, ...]
}

{
    _id: 123456789,
    title: "MongoDB: The Definitive Guide",
    author: [ "Kristina Chodorow", "Mike Dirolf" ],
    published_date: ISODate("2010-09-24"),
    pages: 216,
    language: "English"
}

{
   _id: 234567890,
   title: "50 Tips and Tricks for MongoDB Developer",
   author: "Kristina Chodorow",
   published_date: ISODate("2011-05-06"),
   pages: 68,
   language: "English"
}
```

No sabemos cuanto puede crecer nuestro documento así que lo mejor sería referencia en cada libro a la editorial:
```javascript
{
   _id: "oreilly",
   name: "O'Reilly Media",
   founded: 1980,
   location: "CA"
}

{
   _id: 123456789,
   title: "MongoDB: The Definitive Guide",
   author: [ "Kristina Chodorow", "Mike Dirolf" ],
   published_date: ISODate("2010-09-24"),
   pages: 216,
   language: "English",
   publisher_id: "oreilly"
}

{
   _id: 234567890,
   title: "50 Tips and Tricks for MongoDB Developer",
   author: "Kristina Chodorow",
   published_date: ISODate("2011-05-06"),
   pages: 68,
   language: "English",
   publisher_id: "oreilly"
}
```

## MongoDB in Docker!

Para arrancarnos un Mongo en nuestro ordenador con Docker tan solo tenemos que hacer:

```
docker run -p 27017:27017 --name fictizia-mongodb -d mongo:3.4.19
```

Para entrar a la consola de Mongo ejecutamos:
```
docker exec -it fictizia-mongodb mongo
```

* Listar bases de datos:
`show dbs`

* Usar una base datos
`use databasename`

* Añadir un registro a una colección
```
use fictizia
db.users.insert({name: 'sergio', age: 26})
```

* Ver colecciones
`show collections`

* Buscar todos los registros:
`db.users.find()`

* Buscar todos los registros y que lo pinte bonito:
`db.users.find().pretty()`

* Buscar un solo registro
`db.users.findOne()`

* Buscar registros por un campo
`db.users.find({ name: 'sergio' })`

* Buscar un registro por id
`db.users.findOneAndUpdate({ _id: ObjectId("5c50a7474b76f8986ee35f6a") })`

* Buscar un registro por id y actualizarlo
`db.users.findOneAndUpdate({_id: ObjectId("5c50a7474b76f8986ee35f6a")}, { $set: { name: 'sergio2'} } )`

* Borrar un elemento
`db.users.remove({ name: 'sergio2'})`

* Borrar todos los elementos
`db.users.remove({})`

* Borrar una colección:
`db.users.drop()`