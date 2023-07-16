# Preguntas de Javascript

##### [Crédito: Idea original](https://github.com/lydiahallie/javascript-questions)

## Índice
1. [Comportamiento de variables `var` y `let` en JavaScript: Ejemplo de "hoisting" y "zona muerta temporal".](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#1-qu%C3%A9-devuelve-la-funci%C3%B3n-saluda)
2. [Alcance de variables y setTimeout en JavaScript.](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#2-qu%C3%A9-devuelve-esta-serie-de-bucles)
3. [Funciones regulares y flecha con el uso del this en JavaScript.](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#3-qu%C3%A9-imprimir%C3%ADan-estos-consolelog--)
4. [Conversiones booleanas y evaluación de expresiones en JavaScript.](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#4-qu%C3%A9-devolver%C3%ADa-el-siguiente-c%C3%B3digo)
5. [Acceso a propiedades de objetos en JavaScript: Notación de corchetes y notación de puntos](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#5-cu%C3%A1l-de-%C3%A9stas-opciones-es-incorrecta)
6. [Manejo de objetos por referencia en JavaScript](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#6-qu%C3%A9-devuelve-este-c%C3%B3digo)
7. [Comparación entre operadores == y === en JavaScript: Valor vs. Valor y Tipo](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#7-qu%C3%A9-imprimir%C3%ADan-estos-consolelog-)
8. [TypeError: Acceso incorrecto al método estático en una instancia específica](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#8-qu%C3%A9-devolver%C3%ADa-este-c%C3%B3digo)
9. [Depuración de errores y el uso estricto en JavaScript](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#9-qu%C3%A9-imprimir%C3%ADa-este-consolelog-)
10. [Las funciones en JavaScript: objetos invocables](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#10-qu%C3%A9-sucede-en-este-caso)
11. [Optimización de memoria en JavaScript mediante el uso de prototipos](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#11-qu%C3%A9-devuelve-esta-funci%C3%B3n)
12. [Creación de instancias: Uso de 'new' vs. in 'new': Impacto en la asignación de propiedades](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#12-qu%C3%A9-devuelve-esta-funci%C3%B3n)
13. [Fases de propagación de eventos en la programación de la interfaz de usuario](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#13-cu%C3%A1les-son-las-3-fases-de-la-propagaci%C3%B3n-de-eventos)
14. [Herencia de prototipos y acceso a métodos en JavaScript](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#14-todos-los-objetos-tienen-un-prototipo)
15. [Tipado dinámico y coerción implícita de tipos](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#15-qu%C3%A9-devuelve-esta-funci%C3%B3n)
16. [Operadores unarios de incremento y sus resultados. ](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#16-qu%C3%A9-devuelve-esta-funci%C3%B3n)
17. [Plantillas etiquetadas en JavaScript: Personaliza y modifica las salidas de las plantillas literales](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#17-qu%C3%A9-devuelve-esta-funci%C3%B3n)
18. [Comparación de objetos en JavaScript](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#18-qu%C3%A9-devuelve-esta-funci%C3%B3n)
19. [El operador de propagación (spread operator) en JavaScript"](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#19-qu%C3%A9-devuelve-esta-funci%C3%B3n)
20. [La importancia de utilizar 'use strict' para evitar variables globales accidentales](https://github.com/francoibanezweb/preguntas-de-javascript/tree/main#20-qu%C3%A9-devuelve-esta-funci%C3%B3n)
21. [Evaluación de una cadena: el uso de eval()]()

---
# 1. ¿Qué devuelve la función saluda? 
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)
<!-- El link del índice pensado para ser clickeado desde el navegador -->

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
  
<div align="center">

<details><summary><b>RESPUESTA</b></summary>
<p>
   
## La correcta es la `B`.

<div align="left">

1. Para las variables declaradas con `var`, durante la fase de creación del 
contexto de ejecución, se reserva un espacio en memoria y se asigna el valor 
predeterminado `undefined`. Esto se conoce como 
"[hoisting](https://developer.mozilla.org/es/docs/Glossary/Hoisting)" o 
elevación. En el ejemplo, la variable "nombre" se declara con `var`, por lo que 
se eleva y se inicializa con el valor `undefined` antes de que se alcance la 
línea de código donde se define.
2. Sin embargo, las variables declaradas con `let` o `const` también se elevan, 
pero no se inicializan. Éstas tienen una "[zona muerta temporal](https://wesbos.com/temporal-dead-zone)" 
en la que no son accesibles antes de la línea de
código en la que se declaran (se inicializan). Si intentamos acceder a una 
variable `let` o `const` antes de su declaración, se lanzará un `ReferenceError`
. En el ejemplo, la variable `edad` de declara con `let`, y como intentamos 
acceder a ella antes de su declaración, se produce un `ReferenceError`.

</div>

<img src="./assets/images/1.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="555" height="300"
     style="border: 1px solid black; text-align: center;">


</p>
</details>

</div>

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


<div align="center">
<details><summary><b>RESPUESTA</b></summary>
<p>

## La correcta es la `C`.

<div align="left">

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

</div>

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
</div>

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

<div align="center">
<details><summary><b>RESPUESTA</b></summary>
<p>

## La correcta es la `B`.

<div align="left">

Porque `forma.diametro()` es una función regular que accede 
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

</div>

<img src="./assets/images/3.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="500" height="250"
     style="border: 1px solid black; text-align: center;">

</p></details>
</div>

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

<div align="center">
<details><summary><b>RESPUESTA</b></summary> <p>

## La correcta es la `A`.

<div align="left">
En el primer caso `+true` se trata de convertir el valor booleano `true` en un 
número. Cuando se convierte un valor booleano a número, `true` se convierte en 1
y `false` se convierte en 0. Por lo tanto, `+true` devuelve el número 1.

En el segundo caso, `!"Franco"` es una expresión de negación lógica(`!`) que se 
aplica a la cadena de texto "Franco". En JavaScript, cualquier cadena de texto 
vacía se considera verdadera en un contexto booleano. Al negarla, estamos 
preguntando si este valor verdader es falso. Por lo tanto, `!"Franco"` devuelve
el valor booleano false.
</div>
<img src="./assets/images/4.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="500" height="200"
     style="border: 1px solid black; text-align: center;">

</p></details>
</div>

---

# 5. ¿Cuál de éstas opciones es incorrecta?
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)

```javascript
  const pajarito = {
    tamanio : "pequenio"
  };

  const raton = {
    nombre : "Perez",
    pequenio : true
  };
```
- A: `raton.pajarito.tamanio`
- B: `raton[pajarito.tamanio]`
- C: `raton[pajarito["tamanio"]]`

<div align="center">
<details><summary><b>RESPUESTA</b></summary> <p>

## La incorrecta sería la A.

<div align="left">

En JavaScript, todas las claves de un objeto se interpretan como [`cadenas`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/String)
, a menos que sean de tipo "símbolo". Aunque no las escribamos explícitamente 
como cadenas, se comportan internamente como cadenas.

Cuando utilizamos la [`notación de corchetes`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Operators/Property_accessors#notaci%C3%B3n_por_corchetes)
para acceder a las propiedades de un objeto, JavaScript interpreta la 
declaración. Comienza evaluando lo que está dentro de los corchetes, desde el 
corchete de apertura `"["` hasta el corchete de cierre `"]"`. Solo de esta manera se
evaluará correctamente la expersión.

Por ejemplo, en el caso de `raton[pajarito.tamanio]`, primero se evalúa 
`pajarito.tamanio`, que tiene un valor de "pequenio". Luego, JavaScript 
interpreta `raton["pequenio"]`, lo cual devuelve `true`.

Sin embargo, con la [`notación de puntos`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Operators/Property_accessors#notaci%C3%B3n_por_punto),
esto no ocurre de la misma manera. Si intentamos acceder a una propiedad 
utilizando la notación de puntos, como `raton.pajarito.tamanio`, JavaScript 
busca una propiedad llamada `"pajarito"` dentro del objeto `raton`. Como 
`raton.pajarito` es `undefined`, en realidad estamos intentando acceder a 
`undefined.tamanio`. Esto no es válido y generará un error similar a 
"Cannot read property `'tamanio'` of undefined".

</div>

<img src="./assets/images/5.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="500" height="200"
     style="border: 1px solid black; text-align: center;">

</p></details>
</div>

---

# 6. ¿Qué devuelve este código?
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)

```javascript
  let a = { saludo: "¿Qué tal?" };
  let b;

  b = a;
  a.saludo = "¡Hola!";
  console.log(b.saludo);
```
- A: `¡Hola!`
- B: `undefined`
- C: `ReferenceError`
- D: `TypeError`

<div align="center">
<details><summary><b>RESPUESTA</b></summary> <p>

## La correcta es la `A`.

<div align="center">

En `JavaScript`, los objetos se manejan por referencia. Cuando se asignan a 
variables o se pasan como argumentos a funciones, todos apuntan a la misma 
ubicación en memoria. Por lo tanto, cuando se cambia un objeto, ésto se verá 
reflejado en todas las otras referencias que apunten a ese objeto.

Primero se crea un objeto `a` con un valor determinado. Se asigna la referencia
`a` a la variable `b`, es por eso que ambas variables apuntan al mismo objeto en 
la memoria.

Cuando se modifica el objeto a través de la variable `a`, el cambio se refleja 
también en la variable `b` porque ambas apuntan al mismo objeto.

En `JavaScript`, cuando se cambia un objeto, todos los objetos que compartan la 
misma referencia se verán afectados por ese cambio.

</div>

<img src="./assets/images/6.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="500" height="200"
     style="border: 1px solid black; text-align: center;">

</p></details>
</div>

---

# 7. ¿Qué imprimirían estos console.log( )?
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)

```javascript
  let a = 3;
  let b = new Number(3);
  let c = 3;

  console.log(a == b);
  console.log(a === b);
  console.log(b === c);

```
- A. `true` `false` `true`
- B. `false` `false` `true`
- C. `true` `false` `false`
- D. `false` `true` `true`

<div align="center">
<details><summary><b>RESPUESTA</b></summary> <p>

## La correcta es la `C`.

<div align="left">

"`new Number( )`" es un constructor de funciones integrado en JavaScript. 
Aunque parece representar un número, en realidad es un objeto con 
características adicionales.

Cuando utilizamos el operador `"=="`, se verifica si dos valores son iguales, 
sin tener en cuenta el tipo de  dato. En este caso, ambos tienen el valor de 3, 
por lo que se devuelve `"true"`.

sin embargo, cuando utilizamos el operador `"==="`, se verifica tanto el valor 
como el tipo de dato. Dado que "`new Number( )`" no es un número, sino un objeto
, los dos valores no son iguales y se devuelve `"false"`.

</div>

<img src="./assets/images/7.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="350" height="200"
     style="border: 1px solid black; text-align: center;">

</p></details>
</div>

---

# 8. ¿Qué devolvería este código?
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)

```javascript
  class camaleon  {
    static cambiarColor (colorNuevo){
      this.color = colorNuevo;
      return this.color;
    }

    constructor({color = "verde"} = {}){
      this.color = color;
    }
  }
  const manchita = new camaleon({color : "azul"});
  manchita.cambiarColor("naranja");

```
- A. `verde`
- B. `naranja`
- C. `azul`
- D. `TypeError`

<div align="center">
<details><summary><b>RESPUESTA</b></summary> <p>

## La correcta es la `D`.

<div align="left">

El método cambiarColor es estático y no se puede acceder a través de una 
instancia como `manchita.cambiarColor("naranja")`. Debería ser llamado 
directamente en la clase camaleon, como `camaleon.cambiarColor("naranja")`. 
Esto causa un TypeError.

</div>

<img src="./assets/images/8.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="500" height="340"
     style="border: 1px solid black; text-align: center;">

</p></details>
</div>

---

# 9. ¿Qué imprimiría este console.log( )?
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)

```javascript
 let saludo;
 asludo = {}; // Error de tipeo
 console.log(asludo);

```
- A. `{}`
- B. `ReferenceError: asludo is not defined`
- C. `undefined`

<div align="center">
<details><summary><b>RESPUESTA</b></summary> <p>

## La correcta es la `A`.

<div align="left">

En este caso, JavaScript registra el objeto porque acabamos de crear un objeto 
vacío en el objeto global. Cuando escribimos erróneamente `saludo` como `asludo`
, el intérprete de JavaScript lo interpreta como `global.asludo = {}`
(o window.asludo = {} en un navegador).

Para evitar este tipo de errores, podemos utilizar el `"modo estricto"` 
(["use strict"](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Modo_estricto)).
Esto garantiza que una variable se declare antes de asignarle 
cualquier valor.

</div>

<img src="./assets/images/9a.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="350" height="200"
     style="border: 1px solid black; text-align: center;">
  <img src="./assets/images/9b.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="350" height="200"
     style="border: 1px solid black; text-align: center;">

</p></details>
</div>

---

# 10. ¿Qué sucede en este caso?
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)

```javascript
 function ladrar( ){
  console.log("Guau!");
 }
 
 ladrar.animal = "perro";

```
- A. No pasa nada, es válido
- B. `SyntaxError`. No es posible agregar propiedades a una función así.
- C. `undefined`
- D. `ReferenceError`

<div align="center">
<details><summary><b>RESPUESTA</b></summary> <p>

## La correcta es la `A`.

<div align="left">

En JavaScript las funciones son `objetos`.(Excepto los tipos primitivos, `todo` 
es un objeto en JavaScript).

Una función se considera un objeto. El código que escribas no es en realidad la 
función en sí, sino que la función es un objeto que posee propiedades. Una de 
esas propiedades es la capacidad de ser invocada.

</div>

<img src="./assets/images/10.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="350" height="200"
     style="border: 1px solid black; text-align: center;">

</p></details>
</div>

---

# 11. ¿Qué devuelve esta función?
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)

```javascript
function Persona(nombre, apellido){
  this.nombre = nombre;
  this.apellido = apellido;
}

const asociado = new Persona("Franco", "Ibañez");

Persona.obtenerNombreCompleto = function(){
  return `${this.nombre} ${this.apellido}`;
}

console.log(asociado.obtenerNombreCompleto());

```
- A. `TypeError`
- B. `SyntaxError`
- C. `Franco Ibañez`
- D. `undefined` `undefined`

<div align="center">
<details><summary><b>RESPUESTA</b></summary> <p>

## La correcta es la `A`.

<div align="left">

En JavaScript, no es posible añadir propiedades a un constructor como se hace 
con los objetos. Para agregar una característica a todos los objetos al mismo 
tiempo, se debe utilizar el prototipo en su lugar. 
Se debería haber hecho algo así:
```javascript
Persona.prototype.obtenerNombreCompleto = function(){
  return `${this.nombre} ${this.apellido}`
}
```
de esta forma, "asociado.obtenerNombreCompleto" hubiese funcionado 
correctamente.

La ventaja de utilizar el prototipo radica en la optimización del uso de memoria
. Si se agregara este método directamente al constructor, todas las instancias
de "Persona" tendrían esta propiedad, lo que consumiría más memoria. Sin embargo
, al añadirlo al prototipo, solo se guarda una copia en la memoria y todas las 
instancias pueden acceder a él. Esto evita el desperdicio innecesario de espacio 
de espacio en memoria.

</div>

<img src="./assets/images/11a.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="350" height="200"
     style="border: 1px solid black; text-align: center;">
<img src="./assets/images/11b.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="350" height="200"
     style="border: 1px solid black; text-align: center;">

</p></details>
</div>

---

# 12. ¿Qué devuelve esta función?
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)

```javascript
function Persona(nombre, apellido){
  this.nombre = nombre;
  this.apellido = apellido;
}

const franco = new Persona("Franco", "Ibañez");
const juan = Persona("Juan", "Sabato");

console.log(franco);
console.log(sarah);

```
- A: `Persona {nombre: "Franco", apellido: "Ibañez"}` y `undefined`
- B: `Persona {nombre: "Franco", apellido: "Ibañez"}` 
      y `Persona {nombre: "Juan", apellido: "Sabato"}`
- C: `Persona {nombre: "Franco", apellido: "Ibañez"}` y `{}`
- D: `Persona {nombre: "Franco", apellido: "Ibañez"}` y `ReferenceError`

<div align="center">
<details><summary><b>RESPUESTA</b></summary> <p>

## La correcta es la `A`.

<div align="left">

Cuando se crean las 2 instancias de la clase Persona, la instancia `franco` se 
crea utilizando la palabra reservada `new`, lo que significa que se crea un 
nuevo objeto vacío y se asigna a `this` dentro la función `Persona`.

Al crear la instancia `juan`, no se utiliza la palabra reservada `this`. Dentro
de la función Persona, el `this` se refiere al objeto global en lugar de crear 
un nuevo objeto. Las propiedades `nombre` y `apellido` se asignan al objeto 
global en lugar de a un nuevo objeto.
</div>

<img src="./assets/images/12.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="350" height="200"
     style="border: 1px solid black; text-align: center;">

</p></details>
</div>

---

# 13. ¿Cuáles son las 3 fases de la propagación de eventos?
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)


- A: `Target` > `Capturing` > `Bubbling`
- B: `Bubbling` > `Target` > `Capturing`
- C: `Target` > `Bubbling` > `Capturing`
- D: `Capturing` > `Target` > `Bubbling`

<div align="center">
<details><summary><b>RESPUESTA</b></summary> <p>

## La correcta es la `D`.

<div align="left">

Estas fases son importantes en la programación de eventos en el ámbito de la 
interfaz de usuario y se refieren al orden en que los eventos se propagan a 
través de los elementos del DOM (Modelo de Objetos del Documento).

La respuesta correcta es D: Capturing > Target > Bubbling. Esto significa que el
evento primero pasa por la fase de Capturing, luego alcanza el elemento objetivo
(Target) y finalmente se propaga en la fase de Bubbling.

Durante la fase de Capturing, el evento se propaga desde el elemento raíz del 
DOM hacia el elemento objetivo. A medida que se propaga, atraviesa los elementos
ancestros en el camino hacia el elemento objetivo.

Una vez que el evento alcanza el elemento objetivo, comienza la fase de 
Bubbling. En esta fase, el evento se propaga desde el elemento objetivo hacia el
elemento raíz del DOM. Al igual que en la fase de Capturing, atraviesa los 
elementos ancestros en su camino hacia el elemento raíz.

Es importante comprender estas fases de propagación de eventos para manejar 
adecuadamente los eventos en la programación de la interfaz de usuario. 
Dependiendo del caso de uso, se puede aprovechar la fase de Capturing o la fase 
de Bubbling para capturar o manejar eventos en elementos específicos del DOM.

</div>

<img src="https://camo.githubusercontent.com/5fd2d347d044150e4ae35091622f0628f0eb7893966f03c8955ca271f3153e47/68747470733a2f2f692e696d6775722e636f6d2f4e31386f5267642e706e67"
     alt="Captura del output en la terminal del ejercicio"
     width="350" height="200"
     style="border: 1px solid black; text-align: center;">

</p></details>
 </div>

---

# 14. Todos los objetos tienen un prototipo.
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)


- A: `Verdadero`
- B: `Falso`

<div align="center">
<details><summary><b>RESPUESTA</b></summary> <p>

## La correcta es la `B`.

<div align="left">

En JavaScript, todos los objetos tienen un prototipo, excepto el [objeto base](https://stackoverflow.com/questions/56659303/what-is-base-object-in-javascript).
El objeto base es el punto final de la cadena de prototipos y no tiene ningún 
prototipo al que acceder. Esta es la razón por la que el objeto base no tiene 
métodos o propiedades específicas disponibles para su uso.

Sin embargo, cuando creamos objetos a partir de constructores o clases, esos 
objetos heredan el prototipo de su constructor o clase. El prototipo actúa como 
un "modelo" para los objetos y contiene métodos y propiedades compartidos que 
pueden ser utilizados por los objetos creados a partir de él.

Por ejemplo, el componente en cuestión tiene acceso a algunos métodos y 
propiedades, como el método `.toString()`. Esto se debe a que el objeto del 
componente hereda el prototipo que contiene ese método.

Cuando se accede a un método o propiedad en un objeto, JavaScript busca primero 
en el objeto en sí. Si no se encuentra allí, continúa buscando en la cadena de 
prototipos del objeto hasta encontrarlo. Esto se conoce como herencia de 
prototipos.

Entonces, aunque no podemos encontrar directamente un método o propiedad en un 
objeto, JavaScript desciende por la cadena de prototipos y lo encuentra allí, lo
que lo hace accesible para su uso posterior.

Este mecanismo de herencia de prototipos en JavaScript permite el uso de los 
métodos y propiedades incorporados del lenguaje, ya que están disponibles en los
prototipos de los objetos. 

</div>

</p></details>
</div>

---

# 15. ¿Qué devuelve esta función?
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)

```javascript
function sumar(a,b){
  return a + b;
}

sumar(2, "5");

```
- A. `NaN`
- B. `7`
- C. `TypeError`
- D. `"25"`

<div align="center">
<details><summary><b>RESPUESTA</b></summary> <p>

## La correcta es la `D`.

<div align="left">

En JavaScript, no es necesario declarar explícitamente el tipo de una variable, 
ya que se determina automáticamente durante la ejecución del programa. Esto se 
debe a que JavaScript es un lenguaje de tipado dinámico o de tipado débil.

La [coerción implícita de tipos](https://developer.mozilla.org/es/docs/Glossary/Type_coercion)
es un concepto en JavaScript donde los valores pueden convertirse 
automáticamente en otro tipo sin necesidad de ser declarado. 
Esto permite que los valores se ajusten y se utilicen de manera flexible en 
diferentes operaciones.

Un ejemplo de coerción implícita ocurre cuando se realiza una suma entre un 
número y una cadena. En este caso, JavaScript convierte el número en una cadena 
para que la operación tenga sentido y pueda devolver un resultado. Por ejemplo, 
al sumar el número 2 con la cadena "5", JavaScript trata al número como una 
cadena y realiza una concatenación de cadenas, resultando en el valor "25".

La coerción en JavaScript implica la conversión de un tipo de dato a otro de 
forma automática según el contexto de la operación o expresión. Esto 
proporciona flexibilidad en la manipulación de valores, pero también requiere 
cuidado al realizar operaciones para evitar resultados inesperados.

</div>

<img src="./assets/images/15.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="350" height="200"
     style="border: 1px solid black; text-align: center;">

</p></details>
</div>

---

# 16. ¿Qué devuelve esta función?
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)

```javascript
let numero = 0;
console.log(numero++);
console.log(++numero);
console.log(numero);

```
- A. `1` `1` `1`
- B. `1` `2` `2`
- C. `0` `2` `2`
- D. `0` `1` `2`

<div align="center">
<details><summary><b>RESPUESTA</b></summary> <p>

## La correcta es la `C`.

<div align="left">

Aquí debemos tener en cuenta el comportamiento del operador unario ++ : <br>
Si lo aplicamos `postfix`...(algo++)
1. Devuelve el valor actual.
2. Incrementa el valor en 1.

Si lo aplicamos `prefix`...(++algo)
1. Incrementa el valor en 1
2. Devuelve el valor actual

</div>

<img src="./assets/images/16.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="350" height="200"
     style="border: 1px solid black; text-align: center;">

</p></details>
</div>

---

# 17. ¿Qué devuelve esta función?
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)

```javascript
function obtenerInfoPersona(uno, dos, tres){
  console.log(uno);
  console.log(dos);
  console.log(tres);
}
const persona = "Franco";
const edad = 27;

obtenerInfoPersona`${persona} tiene ${edad} años`

```
- A. `"Franco"` `27` `[""," tiene ", " años"]`
- B. `[""," tiene ", " años"]` `"Franco"` `27`
- C. `"Franco"` `[""," tiene ", " años"]` `27`

<div align="center">
<details><summary><b>RESPUESTA</b></summary> <p>

## La correcta es la `B`.

<div align="left">

Las [`plantillas etiquetadas`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Template_literals#plantillas_etiquetadas)
son una funcionalidad avanzada de las `plantillas literales` en JavaScript. 
Al utilizar las plantillas etiquetadas, podemos modificar la salida de las 
plantillas utilizando una función personalizada (la `función etiquetada`).
[Más info](https://codeburst.io/javascript-template-literals-tag-functions-for-beginners-758a041160e1)

Cuando se utiliza una `plantilla etiquetada`, la llamada se convierte en una 
invocación de función, donde la plantilla literal se pasa como argumento. El 
primer argumento de la función es siempre un array que contiene las cadenas de 
caracteres de la plantilla. Los argumentos restantes se asocian con las 
expresiones de la plantilla.

La `función etiquetada` puede realizar cualquier operación deseada con estos 
argumentos. Puede manipular las cadenas de la plantilla, combinarlas con los 
valores de las expresiones, realizar cálculos o cualquier otro procesamiento 
necesario. Luego la función devuelve la cadena final manipulada o puede incluso
un resultado completamente diferente, dependiendo de la lógica implementada 
dentro de la función.

Es importante destacar que el nombre de la función utilizada como etiqueta no 
tiene nada de especial, puede ser cualquier nombre de función válido 
en JavaScript.

</div>

<img src="./assets/images/17.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="350" height="200"
     style="border: 1px solid black; text-align: center;">

</p></details>
</div>

---

# 18. ¿Qué devuelve esta función?
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)

```javascript
function verificarEdad(data){
  if(data === {edad: 18}){
    console.log("¡Eres mayor de edad!");
  }else if(data == {edad: 18}){
    console.log("Aún eres mayor de edad.");
  }else{
    console.log("Hmm...Supongo que no tienes una edad.")
  }
}
verificarEdad({edad: 18});
```
- A. `¡Eres mayor de edad!`
- B. `Aún eres mayor de edad.`
- C. `Hmm...Sunpongo que no tienes una edad.`

<div align="center">
<details><summary><b>RESPUESTA</b></summary> <p>

## La correcta es la `C`.

<div align="left">

La función `verificarEdad` verifica la edad de una persona según los datos 
proporcionados. Al llamar a `verificarEdad({ edad: 18 })`, el resultado sería la 
opción C: `"Hmm..Sunpong que no tienes edad"`.

El código compara el parámetro data con objetos que contienen la propiedad edad 
establecida en 18. Sin embargo, la comparación de objetos en `JavaScript` se 
basa en la `referencia de memoria`, no en los valores de las propiedades.

En la primera condición, `data === { edad: 18 }`, se utiliza el operador de 
igualdad estricta ( `===` ), pero como los objetos no apuntan a la misma 
ubicación en la memoria, la comparación devuelve false.

En la segunda condición, `data == { edad: 18 }`, se utiliza el operador de 
igualdad no estricta ( `==` ), que realiza una conversión de tipos. Sin embargo,
la comparación de objetos sigue siendo basada en la referencia de memoria, por 
lo que también devuelve false.

Como ninguna de las condiciones anteriores se cumple, se ejecuta el bloque else 
y se imprime `"Hmm..Sunpong que no tienes edad"`.

</div>

<img src="./assets/images/18.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="520" height="350"
     style="border: 1px solid black; text-align: center;">

</p></details>
</div>

---

# 19. ¿Qué devuelve esta función?
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)

```javascript
function obtenLaEdad(...args){
  console.log(typeof args);
}
obtenLaEdad(27);
```
- A. `number`
- B. `array`
- C. `object`
- D. `NaN`

<div align="center">

<details><summary><b>RESPUESTA</b></summary> <p>

## La correcta es la `C`.

<div align="left">

El [operador de propagación (spread operator) (...)](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Operators/Spread_syntax)
se utiliza para convertir los argumentos de una función en un array.
Al usar el operador spread, los argumentos se colocan dentro de corchetes [], 
lo que crea un nuevo array con esos elementos.

Dado que un array es un tipo de objeto en JavaScript, el operador typeof 
devuelve `"object"` cuando se aplica a un array. Esto se debe a que, desde el 
punto de vista de JavaScript, un array es un objeto especializado que contiene 
una colección ordenada de elementos.

En resumen, el operador de propagación ( `...` ) se utiliza para convertir los 
argumentos en un array, y `typeof args` devolverá "object" debido a que un array 
es considerado un tipo especial de objeto en JavaScript.

</div>

<img src="./assets/images/19.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="400" height="200"
     style="border: 1px solid black; text-align: center;">

</p></details>

</div>

---

# 20. ¿Qué devuelve esta función?
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)

```javascript
function obtenerEdad(){
  "use strict";
  edad = 27;
  console.log(edad);
}

obtenerEdad();
```
- A. `27`
- B. `undefined`
- C. `ReferenceError`
- D. `TypeError`

<div align="center">

<details><summary><b>RESPUESTA</b></summary> <p>

## La correcta es la C.

<div align="left">

Al utilizar `"use strict"`, se garantiza que no se declaren variables globales 
de manera accidental. En este caso, no declaramos la variable `edad`, y debido a
la inclusión de `"use strict"`, se generará un error de referencia. Si no 
hubiéramos utilizado `"use strict"`, la operación habría funcionado 
correctamente, ya que la propiedad `edad` se habría agregado al objeto global.

</div>

<img src="./assets/images/20.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="450" height="250"
     style="border: 1px solid black; text-align: center;">
</p></details>

</div>

---

# 21. ¿Cuál es el valor de `suma`?
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)

```javascript
const suma = eval("10*10+5");
```
- A. `105`
- B. `"105"`
- C. `TypeError`
- D. `"10*10+5"`

<div align="center">

<details><summary><b>RESPUESTA</b></summary> <p>

## La correcta es la A.

<div align="left">

El código proporcionado declara una constante llamada `"sum"` y le asigna el 
resultado de evaluar la expresión `"10*10+5"`. La evaluación de esta expresión 
resulta en el número `105`.

La función `eval()` se utiliza para evaluar códigos proporcionados como una 
cadena. En este caso, la cadena contiene una expresión aritmética que se evalúa 
y devuelve el resultado numérico.

</div>

<img src="./assets/images/21.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="400" height="170"
     style="border: 1px solid black; text-align: center;">
</p></details>

</div>

---
