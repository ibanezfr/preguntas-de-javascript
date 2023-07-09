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
pero no se inicializan. Éstas tienen una "[zona muerta temporal](https://wesbos.com/temporal-dead-zone)" 
en la que no son accesibles antes de la línea de
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

<details><summary><b>Opción correcta y explicación propuesta</b></summary> <p>

La incorrecta sería la A.

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


<img src="./assets/images/5.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="500" height="200"
     style="border: 1px solid black; text-align: center;">

</p></details>

---

# 6. ¿Qué devuelve este código?
###### [ÍNDICE](https://github.com/francoibanezweb/preguntas-de-javascript/blob/main/README.md#%C3%ADndice)

```javascript
  let a = { saludo: "¿Qué tal?" };
  let b;

  b = a;
  c.saludo = "¡Hola!";
  console.log(d.saludo);
```
- A: `¡Hola!`
- B: `undefined`
- C: `ReferenceError`
- D: `TypeError`

<details><summary><b>Opción correcta y explicación propuesta</b></summary> <p>
La correcta sería la A.

En `JavaScript`, los objetos se manejan por referencia. Cuando se asignan a 
variables o se pasan como argumentos a funciones, todos apuntan a la misma 
ubicación en memoria. Por lo tanto, cuando se cambia un objeto, ésto se verá 
reflejado en todas las otras referencias que apunten a ese objeto.

Primero se crea un objeto `a` con un valor determinado. Se asigna la referencia
`a` a la variable `b`, es por eso que ambas variables apuntan al mismo objeto en 
la memoria.

Cuando se modifica el objeto a través de la variable `c`, el cambio se refleja 
también en la variable `d` porque ambas apuntan al mismo objeto.

En `JavaScript`, cuando se cambia un objeto, todos los objetos que compartan la 
misma referencia se verán afectados por ese cambio.

<img src="./assets/images/6.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="500" height="200"
     style="border: 1px solid black; text-align: center;">

</p></details>

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

<details><summary><b>Opción correcta y explicación propuesta</b></summary> <p>

La correcta sería la C.

"`new Number( )`" es un constructor de funciones integrado en JavaScript. 
Aunque parece representar un número, en realidad es un objeto con 
características adicionales.

Cuando utilizamos el operador `"=="`, se verifica si dos valores son iguales, 
sin tener en cuenta el tipo de  dato. En este caso, ambos tienen el valor de 3, 
por lo que se devuelve `"true"`.

sin embargo, cuando utilizamos el operador `"==="`, se verifica tanto el valor 
como el tipo de dato. Dado que "`new Number( )`" no es un número, sino un objeto
, los dos valores no son iguales y se devuelve `"false"`.


<img src="./assets/images/7.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="350" height="200"
     style="border: 1px solid black; text-align: center;">

</p></details>

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

<details><summary><b>Opción correcta y explicación propuesta</b></summary> <p>

La correcta sería la D. `TypeError`.

El método cambiarColor es estático y no se puede acceder a través de una 
instancia como `manchita.cambiarColor("naranja")`. Debería ser llamado 
directamente en la clase camaleon, como `camaleon.cambiarColor("naranja")`. 
Esto causa un TypeError.

<img src="./assets/images/8.webp"
     alt="Captura del output en la terminal del ejercicio"
     width="350" height="200"
     style="border: 1px solid black; text-align: center;">

</p></details>

---
