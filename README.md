# Preguntas de Javascript

##### [Crédito: Idea original](https://github.com/lydiahallie/javascript-questions)

## Índice
1. [Comportamiento de variables `var` y `let` en JavaScript: Ejemplo de "hoisting" y "zona muerta temporal".](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#1-qu%C3%A9-devuelve-la-funci%C3%B3n-saluda)
2. [Alcance de variables y setTimeout en JavaScript.](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#2-qu%C3%A9-devuelve-esta-serie-de-bucles)
3. [Funciones regulares y flecha con el uso del this en JavaScript.](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#3-qu%C3%A9-imprimir%C3%ADan-estos-consolelog--)
4. [Conversiones booleanas y evaluación de expresiones en JavaScript.](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#4-qu%C3%A9-devolver%C3%ADa-el-siguiente-c%C3%B3digo)

---
# 1. ¿Qué devuelve la función saluda? 
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)

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


<img src="./assets/images/1.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="555" height="300"
     style="border: 1px solid black; text-align: center;">


</p>
</details>

---

# 2. ¿Qué devuelve esta serie de bucles?
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)

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

<img src="./assets/images/2a.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="500" height="150"
     style="border: 1px solid black; text-align: center;">

<img src="./assets/images/2b.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="490" height="90"
     style="border: 1px solid black; text-align: center;">

<img src="./assets/images/2c.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="500" height="100"
     style="border: 1px solid black; text-align: center;">

<img src="./assets/images/2d.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="490" height="90"
     style="border: 1px solid black; text-align: center;">
</p>
</details>

---

# 3. ¿Qué imprimirían estos console.log( ) ?
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)

```javascript
const forma = {
  radio: 10,
  diametro(){
    return this.radio * 2;
  },
  perimetro: () => 2 * Math.PI * this.radio,
};

console.log(forma.diametro());
console.log(forma.perimetro());
``` 
- A: `20` y `62.83185307179586`
- B: `20` y `NaN`
- C: `20` y `63`
- D: `NaN` y `63`

<details><summary><b>Opción correcta y explicación propuesta</b></summary>
<p>

Sería la `B`, porque `forma.diametro()` es una función regular que accede 
correctamente a la propiedad `radio` del objeto `forma` utilizando la palabra 
clave `this`. Por lo tanto, al llamar a `console.log(forma.diametro())`, se 
imprimirá el valor de 20.

Por otro lado, `forma.perimetro` es una función flecha que hereda el ámbito 
circundante, que en este caso sería el ámbito global o del archivo. La palabra
clave `this` dentro de `perimetro` no se refiere al objeto `forma`, sino a su 
ámbito circundante. Dado que no hay una propiedad `radio` en el ámbito 
circundante, se devuelve `undefined`, y al realizar el cálculo, el resultado es 
NaN (Not a Number). Por lo tanto, al llamar a `console.log(forma.perimetro())`, 
se imprimirá NaN.

<img src="./assets/images/3.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="500" height="250"
     style="border: 1px solid black; text-align: center;">

</p></details>

--- 

# 4. ¿Qué devolvería el siguiente código?
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)

```javascript
  +true;
  !"Franco";
```
- A: `1` y `false`
- B: `false` y `NaN`
- C: `false` y `false`

<details><summary><b>Opción correcta y explicación propuesta</b></summary> <p>

La correcta sería la A.

En el primer caso `+true` se trata de convertir el valor booleano `true` en un 
número. Cuando se convierte un valor booleano a número, `true` se convierte en 1
y `false` se convierte en 0. Por lo tanto, `+true` devuelve el número 1.

En el segundo caso, `!"Franco"` es una expresión de negación lógica(`!`) que se 
aplica a la cadena de texto "Franco". En JavaScript, cualquier cadena de texto 
vacía se considera verdadera en un contexto booleano. Al negarla, estamos 
preguntando si este valor verdader es falso. Por lo tanto, `!"Franco"` devuelve
el valor booleano false.

<img src="./assets/images/4.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="500" height="200"
     style="border: 1px solid black; text-align: center;">

</p></details>

---
