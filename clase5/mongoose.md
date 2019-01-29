# Mongoose

![mongoose](https://cms-assets.tutsplus.com/uploads/users/34/posts/29527/preview_image/mongoose.jpg)

Mongoose es el conector más famoso para conectar NodeJS a MongoDB. Es un ODM que nos permite hacer consultas sobre nuestras colecciones de forma sencilla:

* Crear un modelo de una coleccion:

```javascript
  const Schema = mongoose.Schema
  const userSchema = new Schema({
    username: { type: String, required: true },
    password: { type: String, required: true },
    email: { type: String, required: true },
    birthdate: { type: Date, required: true },
    subscriptions: { type: [Schema.Types.ObjectId] },
  })

  let User = mongoose.model('User', userSchema)
```

* [Tipos de schemas](https://mongoosejs.com/docs/schematypes.html):
  * String
  * Number
  * Date
  * Buffer
  * Boolean
  * Mixed
  * ObjectId
  * Array
  * Decimal128
  * Map

* Conectar a MongoDB

```
mongodb://localhost:27017/fictizia
```

* Usar proemsas en vez de callbacks:
```javascript
mongoose.Promise = Promise
```

* Buscar un usuario
```javascript
UserModel.findOne({ $or: [ { username: userToCreate.username }, { email: userToCreate.email } ] }).then(user => {
  console.log(user)
}).catch(err => console.log(err))
```

* Crear un usuario

```javascript
let newUser = new UserModel(userToCreate)
newUser.save()
  .then(doc => console.log(doc))
  .catch(err => console.log(err))
```

* Borrar un usuario
```
Character.deleteOne({ name: 'Eddard Stark' })
```

* Modificar un usuario
```javascript
UserModel.find({ name: 'Sergio'})
  .then(user => {
    user.name = 'sergio2'
    user.save()
      .then(user => console.log(user))
      .catch(err => console.log(err))
  })
  .catch(err => console.log(err))
```
