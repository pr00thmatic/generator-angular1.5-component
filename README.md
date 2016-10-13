# Uso

Aún no es estable, pero para usarlo...

    yo angular1.5-component

Con la llegada de angular 1.5, los componentes han cambiado mucho o.o, este módulo de yeoman genera un scaffolding para un nuevo componente! lo único que necesita es el nombre en kebab-case :O

En el `index.html`, debes inyectar los archivos js generados:

    <script src="components/nombre-componente/nombre-componente.component.js"></script>
    <script src="components/nombre-componente/nombre-componente.module.js"></script>

Se debe añadir al array de componentes en `app.js` el nombre del componente que se creó, en camelCase algo así:

    angular
      .module('miApp', [
        'ngAnimate',
        // ...
        'nombreComponente'
    ]) // ...

Aún no inyecta los archivos .js en el index n.n'

# Instalación

    $ git clone https://github.com/VengadoraVG/generator-angular1.5-component.git
    $ cd generator-angular1.5-component
    $ sudo npm link

## Dependencias

* esprima
* escodegen
* prompt

Para verificar si ya están instalados:

    $ node
    > prompt = require('prompt');

Si la consola se queja diciendo `Error: Cannot find module 'x'`, es porque la dependencia no está instalada, y deberás instalarla.

Para instalar cada una de las dependencias:

    $ sudo npm install esprima --save
    $ sudo npm install escodegen --save
    $ sudo npm install prompt --save

respectivamente

Se usó `esprima` para modificar los archivos javascript. También se usó `escodegen` para convertir de nuevo a un string lo parseado mediante esprima.

Se usó `prompt`, para preguntar el nombre del componente

### probablemente ya instaladas

* fs

Se usó `fs` para la creación de archivos y carpetas, pero probablemente ya lo tengas instalado.

# developing notes...

ok, entonces el scaffolding con yeoman, básicamente hace esto:

## prompt input

Pregunta por el nombre del componente, rogando porque esté en kebab-case, lo vamos a usar en todas partes!

    name

TODO: a veces el prompt se "ensucia" con output del código de yeoman... investigar cómo hacer para obtener un prompt limpio. Aunque este problema aún no se está mostrando, podría llegar a suceder más adelante...

## scaffolding

Dentro de `app/`, crea una carpeta llamada `name`.

### template

Dentro de la carpeta `app/name`, crea un archivo llamado `name.template.html` en blanco.

### module

Dentro de `app/name`, crea un archivo llamado `name.module.js`, su contenido es:

    angular.module(camelCaseName, []);

Donde `camelCaseName` es el nombre en camel case, duh!

### component

Dentro de `app/name`, crea un archivo llamado `name.component.js`, su contenido es

    angular.
      module('camelCaseName').component('camelCaseName'), {
        templateUrl: 'name/name.template.html',
        controller: function camelCaseNameController($scope) {
        }
      });

## sauce

Creando un componente, según el tutorial de angular :O

https://docs.angularjs.org/tutorial/step_03

Se usó esprima y escodegen para modificar los archivos :)
