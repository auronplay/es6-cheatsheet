# es6-cheatsheet
Una hoja de de trucos que contiene la ES2015 [ES6]_(ecmascript 6) tips, trucos, las mejores prácticas y  
snippets de ejemplo para su flujo de trabajo diario. Las contribuciones son bienvenidas!
## Tabla de contenidos

- [var versus let / const](#var-versus-let--const)
- [Replacing IIFEs with Blocks](#replacing-iifes-with-blocks)
- [Arrow Functions](#arrow-functions)
- [Strings](#strings)
- [Destructuring](#destructuring)
- [Modules](#modules)
- [Parameters](#parameters)
- [Classes](#classes)
- [Symbols](#symbols)
- [Maps](#maps)
- [WeakMaps](#weakmaps)
- [Promises](#promises)

## var versus let / const
> Ademas de `var`, ahora tenemos acceso a dos nuevos identificadores
-`let` y `const`, a diferencia de var, las declaraciones `const` no son 
elevadas a la parte superior de su ambito envolvente.

Un ejemplo usando `var`:

```javascript
var snack = 'Meow Mix';

function getFood(food) {
    if (food) {
        var snack = 'Friskies';
        return snack;
    }
    return snack;
}
getFood(false); // undefined
```
Sin embargo, observemos lo que sucede cuando reemplazamos `var` con `let`:

```javascript
let snack = 'Meow Mix';

function getFood(food) {
    if (food) {
        let snack = 'Friskies';
        return snack;
    }
    return snack;
}

getFood(false); // 'Meow Mix'
```
Este cambio en el comportamiento destaca que tenemos que tener cuidado con la refactorización de codigo heredado que utiliza `var`.A ciegas reemplazando instancias de ` var` con `let` puede conducir a un comportamiento inesperado.

> **Nota**: `let` y `const` son bloques de ambito  Por lo tanto , haciendo referencia a los 
identificadores de bloque de ámbito antes de que sean definidos producirá un `ReferenceError`. 

```javascript
console.log(x);

let x = 'hi'; // ReferenceError: x is not defined
```
> **Mejores practicas**: Deja las declaraciones `var` dentro de código
heredado paradenotar que debe ser refactorizado cuidadosamente. Cuando
trabaje en un nuevo código, use `let` para las variables que van
a cambiar su valor con el tiempo y `const` para variables que no pueden ser reasignadas.

<sup>[(regresar a la tabla de contenidos)](#tabla-de-contenidos)</sup>

# Reemplazando IIFEs con bloques.
