# Heroku

![Heroku_logo](https://github.com/Fictizia/Curso-Node.js-para-desarrolladores-Front-end_ed8/raw/master/assets/heroku.svg?sanitize=true)

- [Lenguajes soportados](https://devcenter.heroku.com/categories/language-support)
- [Soporte](https://help.heroku.com/)
- [Precio](https://www.heroku.com/pricing)
- **Documentacion**
  - [Seguridad](https://devcenter.heroku.com/categories/security)
  - [Command Line](https://devcenter.heroku.com/categories/command-line)
  - [Arquitectura](https://devcenter.heroku.com/categories/heroku-architecture)
  - [Deployment](https://devcenter.heroku.com/categories/deployment)
  - [Features](https://devcenter.heroku.com/categories/features)

#### Uso

**Instalación del Toolbelt**

- Universal, mediante `npm`

  ```
  npm install -g heroku
  ```
  
- Linux

  ```
  wget -O- https://toolbelt.heroku.com/install-ubuntu.sh | sh
  ```

- macOS (brew)

  ```
  brew install heroku/brew/heroku
  ```

- Windows ([Installer](https://cli-assets.heroku.com/heroku-cli/channels/stable/heroku-cli-x64.exe))
- Versiones ejecutables para Windows y OSX
- Es necesario tener instalado previamente Ruby en la máquina

**Login en Heroku**

```
heroku login
```

**Preparando la Aplicación**

- Ejemplo de Heroku 

```
git clone https://github.com/heroku/node-js-getting-started.git && cd node-js-getting-started
```

**Crear un proyecto**

- Con un nombre al azar

  ```
  heroku create
  ```

- Con nombre propio

  ```
  heroku create miproyecto
  ```

**Desplegando nuestro proyecto**

- Nota: Previamente tienes que tener el proyecto gestionado con Git.

  ```
  git push heroku master
  ```

**Escalando nuestro proyecto**

- Verificando el número de Dynos

  ```
  heroku ps
  ```

- Definiendo el número de Dynos

  ```
  heroku ps:scale web=1
  ```

**Abriendo nuestro proyecto**

```
heroku open
```

**Logs del proyecto**

```
heroku logs --tail
```

**Lanzar el proyecto en local**

```
heroku local web
```

### Heroku: Addons

- [Documentación General](https://devcenter.heroku.com/categories/add-on-documentation)
- [Lista de Addons](https://elements.heroku.com/addons)
  - [Raygun](https://elements.heroku.com/addons/raygun)
    - Informes de error en tiempo real
    - [Documentación para Node](https://devcenter.heroku.com/articles/raygun#using-with-node)
  - [SendGrid](https://elements.heroku.com/addons/sendgrid)
    - Sistema de envio de emails con muchos extras
    - [Documentación para Node](https://devcenter.heroku.com/articles/sendgrid#node-js)
  - [Easy SMS](https://elements.heroku.com/addons/easysms)
    - Envio/Recepción de SMS mundial
    - [Documentación](https://devcenter.heroku.com/articles/easysms)
  - [mLab MongoDB](https://elements.heroku.com/addons/mongolab)
    - MongoDB as a Service
    - [Documentación para Node](https://devcenter.heroku.com/articles/mongolab)
  - [GrapheneDB](https://elements.heroku.com/addons/graphenedb)
    - Neo4j Graph as a Service
    - [Documentación para Node](https://devcenter.heroku.com/articles/graphenedb#using-with-node-js-and-node-neo4j)
  - [ClearDB MySQL](https://elements.heroku.com/addons/cleardb)
    - MySQL
    - [Documentación](https://devcenter.heroku.com/articles/cleardb)
  - [Graph Story](https://elements.heroku.com/addons/graphstory)
    - Enterprise Neo4j Graph Databases as a Service
    - [Documentación](https://devcenter.heroku.com/articles/graphstory)
  - [Heroku Scheduler](https://elements.heroku.com/addons/scheduler)
    - Programador de tareas
    - [Documentación](https://devcenter.heroku.com/articles/scheduler#dyno-hour-costs)
  - [Process Scheduler](https://elements.heroku.com/addons/process-scheduler)
    - Programa el escalamiento de tus *process types* y *dynos* por horas
    - [Documentación](https://devcenter.heroku.com/articles/process-scheduler)
  - [DocRaptor](https://elements.heroku.com/addons/docraptor)
    - Conversor de HTML a PDF. Simple y robusto
    - [Documentación](https://devcenter.heroku.com/articles/docraptor)
  - [Tinfoil Security](https://elements.heroku.com/addons/tinfoilsecurity)
    - Escaner de seguridad
    - [Documentación](https://devcenter.heroku.com/articles/tinfoilsecurity)
  - [Auth0](https://elements.heroku.com/addons/auth0)
    - Gestión de credenciales
    - [Documentación del Addon](https://devcenter.heroku.com/articles/auth0)
    - [Documentación para Node](https://auth0.com/docs/quickstart/webapp/nodejs)
  - [OAuth.io](https://elements.heroku.com/addons/oauthio)
    - Gestión de credenciales. Más de 100 provedores 
    - [Documentación](https://devcenter.heroku.com/articles/oauthio) 
  - [CloudAMQP](https://elements.heroku.com/addons/cloudamqp)
    - RabbitMQ as a Service
    - [Documentación para Node](https://devcenter.heroku.com/articles/cloudamqp#use-with-node-js)
  - [Keen IO](https://elements.heroku.com/addons/keen)
    - Analíticas para desarrolladores
    - [Documentación para Node](https://devcenter.heroku.com/articles/keen#using-with-node)
  - [Bonsai Elasticsearch](https://elements.heroku.com/addons/bonsai)
    - Elasticsearch
    - [Documentación](https://devcenter.heroku.com/articles/bonsai)

