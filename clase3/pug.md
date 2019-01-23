# Pug

**[Jade... ya no se llama jade. Ahora se llama PUG](https://github.com/pugjs/pug/issues/2184)**

![PUG_logo](https://camo.githubusercontent.com/a43de8ca816e78b1c2666f7696f449b2eeddbeca/68747470733a2f2f63646e2e7261776769742e636f6d2f7075676a732f7075672d6c6f676f2f656563343336636565386664396431373236643738333963626539396431663639343639326330632f5356472f7075672d66696e616c2d6c6f676f2d5f2d636f6c6f75722d3132382e737667)

**Implementaciones en otros lenguajes**
- [php](https://github.com/kylekatarnls/jade-php)
- [scala](https://scalate.github.io/scalate/documentation/scaml-reference.html)
- [ruby](https://github.com/slim-template/slim)
- [python](https://github.com/SyrusAkbary/pyjade)
- [java](https://github.com/neuland/jade4j)


- **Entendiendo la mécanica**
  - index.jade:

    ```jade
    doctype html
    html(lang="en")
      head
        title= pageTitle
        script(type='text/javascript').
          if (foo) {
             bar(1 + 5)
          }
      body
        h1 Jade - node template engine
        #container.col
          if youAreUsingJade
            p You are amazing
          else
            p Get on it!
          p.
            Jade is a terse and simple
            templating language with a
            strong focus on performance
            and powerful features.
    ```
  
  - index.html:

    ```html
    <!DOCTYPE html>
    <html lang="en">
      <head>
        <title>Jade</title>
        <script type="text/javascript">
          if (foo) {
             bar(1 + 5)
          }
        </script>
      </head>
      <body>
        <h1>Jade - node template engine</h1>
        <div id="container" class="col">
          <p>You are amazing</p>
          <p>
            Jade is a terse and simple
            templating language with a
            strong focus on performance
            and powerful features.
          </p>
        </div>
      </body>
    </html>
    ```
  
- Bootstrap:
  - index.jade:

    ```jade
    doctype html
    html
      head
        title title
        include ./includes/styles.jade
      body
        .row
          .container
            .jumbotron
              h1 Hola, desde Bootstrap!
              p ¿Qué te parece?
              p
                a.btn.btn-primary.btn-lg(href='http://getbootstrap.com/', role='button') Aprende más!
        include ./includes/scripts.jade
    ```

  - includes/styles.jade

    ```jade
    //- includes/styles.jade
    // Bootstrap
    link(rel='stylesheet', href='//maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css')
    ```

  - includes/scripts.jade

    ```jade
    //- includes/scripts.jade
    // Jquery
    script(src='//ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js')
    // Bootstrap
    script(src='//maxcdn.bootstrapcdn.com/bootstrap/3.3.5/js/bootstrap.min.js')
    ```

  - index.html

    ```html
    <!DOCTYPE html>
    <html>
      <head>
        <title>title</title>
        <!-- Bootstrap-->
        <link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css">
        </head>
      <body>
        <div class="row">
          <div class="container">
            <div class="jumbotron">
              <h1>Hello, desde Bootstrap!</h1>
              <p>¿Qué te parece?</p>
              <p>
                  <a href="http://getbootstrap.com/" role="button" class="btn btn-primary btn-lg">Aprende más!</a>
              </p>
            </div>
          </div>
        </div>
        <!-- Jquery-->
        <script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
        <!-- Bootstrap-->
        <script src="//maxcdn.bootstrapcdn.com/bootstrap/3.3.5/js/bootstrap.min.js"></script>
      </body>
    </html>
    ```

- [Pug - Github](https://github.com/pugjs/pug)
- [Pug - Getting Started](https://pugjs.org/api/getting-started.html)
- [Jade Syntax Documentation by example](http://naltatis.github.io/jade-syntax-docs/)

