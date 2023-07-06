# Preguntas de Javascript

## Índice
1. [¿Qué devuelve la función saluda?](https://github.com/francoibanezweb/preguntas-de-javascript/edit/main/README.md#qu%C3%A9-devuelve-la-funci%C3%B3n-saluda)

# ¿Qué devuelve la función saluda? 
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/)

```javascript
function saluda(){
   console.log(nombre)
   console.log(edad)
var nombre = "Franco"
let edad = 27
}
```
- A: `ReferenceError` y `27`
- B: `undefined` y `ReferenceError`
- C: `Franco` y `undefined`
- D: `Franco` y `ReferenceError`
  
---
<details><summary><b>Opción correcta y explicación propuesta</b></summary>
<p>
   
#### La correcta sería la B
1. Para las variables declaradas con `var`, durante la fase de creación del 
contexto de ejecución, se reserva un espacio en memoria y se asigna el valor 
predeterminado `undefined`. Esto se conoce como 
"[hoisting](https://developer.mozilla.org/es/docs/Glossary/Hoisting)" o 
elevación. En el ejemplo, la variable "nombre" se declara con `var`, por lo que 
se eleva y se inicializa con el valor `undefined` antes de que se alcance la 
línea de código donde se define.
2. Sin embargo, las variables declaradas con `let` o `const` también se elevan, 
pero no se inicializan. Éstas tienen una "[zona muerta temporal](https://
wesbos.com/temporal-dead-zone)" en la que no son accesibles antes de la línea de
código en la que se declaran (se inicializan). Si intentamos acceder a una 
variable `let` o `const` antes de su declaración, se lanzará un `ReferenceError`
. En el ejemplo, la variable `edad` de declara con `let`, y como intentamos 
acceder a ella antes de su declaración, se produce un `ReferenceError`.

</p>
</details>



##### [Tomé inspiración de este trabajo](https://github.com/lydiahallie/javascript-questions)
