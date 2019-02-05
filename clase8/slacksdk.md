# Slack SDK

![slacklogo](https://i.pinimg.com/originals/2b/26/43/2b26437d72e949db88e62d251c736c45.gif)

Existe ya un SDK para NodeJS que nos permite interactuar con Slack: [Node Slack SDK](https://github.com/slackapi/node-slack-sdk)

Este SDK nos permite:

* Mandar mensajes
* Leer mensajes
* Reaccionar a comandos
* Reaccionar a eventos
* RTM

### Instalación

```
npm i --save @slack/client
```

### Creando un cliente

```javascript
const { WebClient } = require('@slack/client')
const web = new WebClient(token)
```

### Dejando un mensaje en el canal de Slack

```javascript
web.chat.postMessage({ channel: channel, text: message })
  .then(res => {})
  .catch(err => {})
```

### Lista la info de canales
```javascript
web.channels.list().then(res => console.log(res))
```

### Escuchando mensajes en tiempo real
```javascript
const { RTMClient } = require('@slack/client');
const rtm = new RTMClient(token);
rtm.start()

const conversationId = 'CFY3T8ATS';
rtm.on('message', res => console.log(res.text))
```

### Como crear un Slack y una aplicación

Nos vamos a [Slack](https://slack.com/intl/es-es/) y:

1. Pinchamos en *Primeros pasos*
2. Le damos a crear un nuevo espacio de trabajo
3. Metemos los datos que nos piden (email, nombre, etc...)

Una vez creado debemos crear nuestra app para ello:
1. Pinchamos en el menu desplegable de arriba a la izquierda (donde pone el nombre del espacio de trabajo)
2. Nos ponemos sobre *administracion* y clickamos en *Gestionar aplicaciones*
3. Pinchamos en *Crear app* y después en *Start building*
4. Rellenamos los datos de nuestra app y le damos a *Create app*
5. Añadimos un bot pinchando en *Bots*
6. Volvemos a *Basic information* y le damos a *Install your app to your workspace*
7. Para obtener el token de nuestro bot tan solo hay que ir a *OAuth & Permissions*
8. Debemos invitar al bot a nuestro canal

Ya estamos listos para escuchar mensajes y responder!