

Este proyecto es un pequeño juego donde el usuario debe adivinar un
número secreto generado por la aplicación.
A través de este ejercicio se practican:

-   Variables
-   Condicionales
-   Eventos
-   Manipulación del DOM
-   Funciones
-   Uso básico de localStorage

------------------------------------------------------------------------

## 📁 Estructura del proyecto

Partimos de un proyecto base creado con Vite:

index.html
src/
├─ js/main.js
└─ styles/style.css

-   index.html → Contiene el HTML
-   style.css → Contiene los estilos
-   main.js → Contiene la lógica del juego

------------------------------------------------------------------------

## 🔹 Primeros pasos: Estado de la aplicación

``` js
const INIT_SCORE = 30;
const MAX_NUMBER = 100;
let score;
let highscore;
let secretNumber;
```

-   INIT_SCORE → puntuación inicial
-   MAX_NUMBER → número máximo posible (el número al azar estará entre 1 y MAX_NUMBER)
-   score → puntuación actual
-   highscore → mejor puntuación
-   secretNumber → número secreto

Usamos:

- const → cuando no cambia
- let → cuando sí cambia

------------------------------------------------------------------------

## 🔹 Selección de elementos del DOM

Guardamos los elementos HTML en variables:

``` js
const btnCheck = document.querySelector('.check');
const inputNumber = document.querySelector('.guess');
const message = document.querySelector('.message');
const number = document.querySelector('.number');
const scoreLabel = document.querySelector('.score');
const spanHighscore = document.querySelector('.highscore');
const btnAgain = document.querySelector('.again');
const pBetween = document.querySelector('.between');
```

Esto permite:

- Código más limpio
- Evitar repetir querySelector
- Manipular fácilmente los elementos

------------------------------------------------------------------------

## 🔹 Obtener número del input

``` js
const guessNumber = Number(inputNumber.value);
```
- Los input se obtienen mediante el atributo *value*, mientras que en el resto de los elementos es mediante *textContent*
- Los datos del DOM tienen formato string, hay que pasarlos a *Number* si procede.
------------------------------------------------------------------------
## 🔹 Eventos

Los eventos permiten reaccionar a acciones del usuario.

```js

btnCheck.addEventListener('click', function () {
	// aquí iría el código de mi función
	// ojo, se puede ver que es una función anónima
})
```


Significa:
Cuando el usuario hace click → ejecutar función.

---

## 🔹 Obtener número introducido


```js
const guessNumber = Number(inputNumber.value);
```

- value devuelve texto
- Number() lo convierte en número

## 🔹 Validación vacío

``` js
if (!guessNumber) {
  message.textContent = '⛔️ No number!';
}
```
- Si el usuario no escribe nada, mostramos error
------------------------------------------------------------------------

## 🔹 Número correcto

``` js
else if (guessNumber === secretNumber) {
```
Acciones:

- Mostrar mensaje correcto
- Cambiar estilos
- Verificar récord
------------------------------------------------------------------------
## 🔹 Guardar récord
```js
if (score >= highscore) {
  highscore = score;
  localStorage.setItem('highscore', highscore);
}
```

------------------------------------------------------------------------

## 🔹 Número alto

``` js
else if (guessNumber > secretNumber) {
```
Si score es 1:

- Fin del juego
- Desactivar botón
    
Si no:

- Mensaje "Too high"
- Restar punto
------------------------------------------------------------------------

## 🔹 Número bajo

``` js
else if (guessNumber < secretNumber) {
```
- Repetimos lógica. 
------------------------------------------------------------------------

## 🔹 Botón Again

``` js
btnAgain.addEventListener('click', initGame);
```

------------------------------------------------------------------------

## 🔹 Función initGame

``` js
function initGame() {
  score = INIT_SCORE;
  secretNumber = Math.floor(Math.random() * MAX_NUMBER + 1);
}
```

Se encarga de:

- Reiniciar puntuación
- Limpiar input
- Restaurar estilos
- Generar nuevo número
- Leer highscore
------------------------------------------------------------------------


## Código final

```js
import 'the-new-css-reset/css/reset.css';
import '../styles/style.css';

// DEFINIR MIS CONSTANTES Y VARIABLES -> EL ESTADO DE MI APP
const INIT_SCORE = 30;
const MAX_NUMBER = 100;
let score;
let highscore;
let secretNumber;

// SELECCIONAR ELEMENTOS DEL DOM
const btnCheck = document.querySelector('.check');
const inputNumber = document.querySelector('.guess');
const message = document.querySelector('.message');
const number = document.querySelector('.number');
const scoreLabel = document.querySelector('.score');
const spanHighscore = document.querySelector('.highscore');
const btnAgain = document.querySelector('.again');
const pBetween = document.querySelector('.between');

// EVENTOS DEL CÓDIGO

// si yo pulso el boton btnCheck saco un mensaje por consola
btnCheck.addEventListener('click', function () {
  // obtengo el valor del inputNumber
  const guessNumber = Number(inputNumber.value);
  // si no han introducido nada, muestro un mensaje
  if (!guessNumber) {
    message.textContent = '⛔️ No number!';
  } else if (guessNumber === secretNumber) {
    message.textContent = '🎉 Correct Number!';
    number.style.fontSize = '9rem';
    number.style.backgroundColor = '#ffff00';
    number.style.width = '22rem';
    document.body.style.backgroundColor = '#60b347';
    if (score >= highscore) {
      highscore = score;
      spanHighscore.textContent = highscore;
      message.textContent = '🎉 Correct Number! Record!';
      // lo guardo en localStorage
      localStorage.setItem('highscore', highscore);
    }
  } else if (guessNumber >= secretNumber) {
    if (score === 1) {
      message.textContent = '📈 Too high! Game over!';
      btnCheck.disabled = true;
      document.body.style.backgroundColor = '#bb4949';
      number.textContent = 'X';
    } else {
      message.textContent = '📈 Too high!';
    }
    score--;
    scoreLabel.textContent = score;
  } else if (guessNumber < secretNumber) {
    if (score === 1) {
      message.textContent = '📈 Too low! Game over!';
      btnCheck.disabled = true;
      document.body.style.backgroundColor = '#bb4949';
      number.textContent = 'X';
    } else {
      message.textContent = '📈 Too low!';
    }
    score--;
    scoreLabel.textContent = score;
  }
});

btnAgain.addEventListener('click', initGame);

function initGame() {
  btnCheck.disabled = false;
  score = INIT_SCORE;
  scoreLabel.textContent = score;
  message.textContent = 'Start guessing...';
  number.textContent = '?';
  number.style.fontSize = '6rem';
  number.style.backgroundColor = '#fff';
  number.style.width = '15rem';
  document.body.style.backgroundColor = '#222';
  inputNumber.value = '';
  pBetween.textContent = `(Between 1 and ${MAX_NUMBER})`;

  // genero número aleatorio entre 1 y MAX_NUMBER
  secretNumber = Math.floor(Math.random() * MAX_NUMBER + 1);
  number.textContent = secretNumber;
  // obtener el highscore del localStorage
  highscore = Number(localStorage.getItem('highscore')) || 0;
  spanHighscore.textContent = highscore;
}

initGame();
```
