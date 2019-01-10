# Git

## Instalación

Para instalar Git tenemos que entrar en [Git](https://git-scm.com/) e instalarlo para nuestro SO.

Normalmente en Ubuntu y OSX ya viene instalado de serie. Podemos comprobar si lo tenemos instalado ejecutando:
```
git --version
```

## Introducción a git

### Ramas

Un repositorio de git se divide en ramas. Normalmente, la rama principal se llama master y se sacan ramas a partir de ella para después mergearlas.
Mergear una rama es añadir los cambios hechos en una rama a la rama destino. 

Esto nos permite hacer cambios sin alterar el código de la rama principal. Antes de mergear una rama se suele revisar por los demás integrantes del
equipo para asegurar que todo está bien.

## Comandos más utilizados

* Clonar un repositorio:

```
git clone https://github.com/user/repo.git
```

* Cambio de rama
```
git checkout nombre_de_rama
```

* Crear una rama nueva
```
git checkout -b nombre_de_rama_nueva
```

* Mirar en que rama estas:
```
git branch
```

* Añadir todos los ficheros a una rama:
```
git add .
```

* Añadir solo ciertos ficheros:
```
git add ruta_al_fichero/fichero.js ruta_al_fichero/fichero2.js
```

* Crear un commit:
```
git commit -m 'nombredelcommit'
```

* Push de los cambios al repositorio online
```
git push origin nombrerama
```

* Pull del repositorio
```
git pull
```

## .gitignore

El archivo .gitignore es un archivo que se encuentra en la raiz de nuestro repositorio y se utiliza para evitar
subir ciertos archivos al repositorio (claves, librerías externas, etc...). Acepta expresiones regulares para poder
excluir varios ficheros a la vez.
