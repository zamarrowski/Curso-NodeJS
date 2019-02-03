# Ejercicios

**1 -** Inicializa un repositorio utilizando **npm** y **git**.
Deberás preparar un entorno básico de testing siguiendo los siguientes patrones:
- Crea un directorio `lib/` donde irá el código de tu proyecto.
- Crea un directorio `tests/` donde irán las pruebas unitarias.
- En el `package.json` se debe crear el script `test` para que se ejecuten los tests del proyecto.
- Cuando ejecutes los tests (utilizando `mocha + chai`) se deben ejecutar todos los ficheros en el directorio `tests/`.

**2 -** Aplicando **TDD** y utilizando el repositorio del ejercicio anterior, crea una función `atm` que devuelva el número más eficiente de billetes dados los siguientes casos:
- Si un valor no es válido (ej. negativo) no debe devolver nada.
- La función debe devolver billetes de entre 5 y 50€.

**Ejemplo** (5€)
  - 1 billete de 5€.

**Ejemplo** (35€)
  - 1 billete de 5€.
  - 1 billete de 10€.
  - 1 billetes de 20€.

**Ejemplo** (165€)
  - 1 billete de 5€.
  - 1 billete de 10€.
  - 3 billetes de 50€.

**3 -** Crea una función que acepte como primer argumento un número.
Esa función debe devolver un objeto con los métodos `add()` y `subtract()`, y a su vez esos métodos se podrán ir encadenando hasta el infinito.
- Cuando se llame a la función `add()`, tendrá que imprimir por consola el número anterior `+1`.
- Cuando se llame a la función `subtract()`, tendrá que imprimir por consola el número anterior `-1`.

Ejemplo:

```javascript
function createNumber() {
  // return ...
}

createNumber(5)   // prints "5"
  .add()          // prints "6"
  .add()          // prints "7"
  .subtract()     // prints "6"
  .add()          // prints "7"
  // ...
```