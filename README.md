# Preguntas de Javascript

## Índice
1. [¿Qué devuelve la función saluda?](https://github.com/francoibanezweb/preguntas-de-javascript/edit/main/README.md#qu%C3%A9-devuelve-la-funci%C3%B3n-saluda)
2. [¿Qué devuelve esta serie de bucles?](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#qu%C3%A9-devuelve-esta-serie-de-bucles)
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

# ¿Qué devuelve esta serie de bucles?

```javascript
for (var i = 5; i < 8; i++){
  setTimeout(() => console.log(i), 1);
}

for(let i = 5; i < 8; i++){
  setTimeout(() => console.log(i), 1);
}
```
- A: `5 6 7`  y  `5 6 7`
- B: `5 6 7`  y  `7 7 7`
- C: `7 7 7`  y  `5 6 7`

---
<details><summary><b>Opción correcta y explicación propuesta</b></summary>
<p>

La correcta sería la C.

En JavaScript, las funciones [`setTimeout`](https://developer.mozilla.org/es/docs/Web/API/setTimeout)
se ejecutan de forma asíncrona. Esto significa que se colocan en la cola de 
eventos y se ejecutan después de que se hayan completado todas las tareas 
sincrónicas.

En el primer bucle, se utiliza la palabra reservada `var` para declarar la 
variable `i`. Al usar `var`, el alcance de la variable se vuelve global. Esto 
significa que todas las iteraciones del bucle comparten la misma variable `i`. 
Durante cada iteración, el valor de `i` se incrementa en 1. Sin embargo, debido 
a que las funciones `setTimeout` se ejecutan de forma asíncrona 
después de que el bucle haya terminado, todas las funciones `setTimeout` ven el 
mismo valor de `i`, que es 3 al final del bucle. Por lo tanto, cuando se 
ejecutan las funciones `setTimeout`, todas imprimen el valor 3.

En el segundo bucle, se utiliza la palabra reservada `let` para declarar la 
variable `i`. Al usar `let`, se crea una nueva variable `i` en cada iteración 
del bucle. Cada variable `i` tiene su propio alcance de bloque y se conserva 
dentro del bloque del bucle. Cuando se llama a la función `setTimeout` en cada 
iteración, se captura el valor actual de `i` dentro de ese alcance de bloque 
específico. Como resultado, cada función `setTimeout` ve un valor de `i` 
distinto correspondiente a su respectiva iteración del bucle.

En resumen, la diferencia en el comportamiento se debe al alcance de las 
variables `i`. Con `var`, se comparte una sola variable `i` en todo el bucle,
lo que provoca que todas las funciones `setTimeout` vean el mismo valor al 
final del bucle. Con `let`, se crea una nueva variable `i` en cada iteración del 
bucle, lo que permite que cada función `setTimeout` capture el valor 
correspondiente a su propia iteración.
</p>
</details>

##### [Tomé inspiración de este trabajo](https://github.com/lydiahallie/javascript-questions)
