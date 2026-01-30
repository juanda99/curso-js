
## index.html

- En el código html, dejamos solo *un elemento ancla* que será donde inyectaremos nuestro código html mediante JavaScript

``` html
<div id="app"></div>
```

------------------------------------------------------------------------

## main.js

- Main.js solo decide qué vista cargar.
- Importamos la vista que presenta el formulario para obtener el nombre del jugador

``` js
import 'the-new-css-reset/css/reset.css';
import '../styles/style.css';
import { renderWelcome } from './views/welcomeView.js';

renderWelcome();
```



------------------------------------------------------------------------

## Estructura vistas

/src/js/views
- welcomeView.js
- gameView.js

------------------------------------------------------------------------

# welcomeView.js

``` js
import { renderGame } from './gameView.js';
export let userName;

export function renderWelcome() {
  document.querySelector('#app').innerHTML = `
    <h1>Welcome</h1>
    <input id="userName"/>
    <button id="startGame">Start</button>
  `;

  document.querySelector('#startGame').addEventListener('click', () => {
    userName = document.querySelector('#userName').value;
    if (userName.trim() !== '') {
      renderGame();
    }
  });
}
```

------------------------------------------------------------------------

# gameView.js

``` js
import { userName } from './welcomeView.js';

export function renderGame() {
  document.querySelector('#app').innerHTML = `
    <h1>${userName}, guess my number</h1>
    <input class="guess"/>
    <button class="check">Check</button>
    <p class="message"></p>
    <p>Score: <span class="score"></span></p>
  `;

  const INIT_SCORE = 30;
  const MAX_NUMBER = 100;
  let score;
  let secretNumber;

  const inputNumber = document.querySelector('.guess');
  const message = document.querySelector('.message');
  const scoreLabel = document.querySelector('.score');
  const btnCheck = document.querySelector('.check');

  btnCheck.addEventListener('click', () => {
    const guess = Number(inputNumber.value);
    if (guess === secretNumber) {
      message.textContent = 'Correct';
    } else {
      score--;
      message.textContent = 'Wrong';
    }
    scoreLabel.textContent = score;
  });

  function initGame() {
    score = INIT_SCORE;
    scoreLabel.textContent = score;
    secretNumber = Math.floor(Math.random() * MAX_NUMBER + 1);
  }

  initGame();
}
```

------------------------------------------------------------------------

# Flujo SPA

1.  main.js → renderWelcome()
2.  Usuario escribe nombre
3.  Click Start
4.  renderGame()
5.  Juego activo

------------------------------------------------------------------------

# Conceptos Clave

-   Modularización
-   Separación de responsabilidades
-   Renderizado dinámico
-   Estado encapsulado (imports & exports)
-   SPA (Single Page Application) básica

------------------------------------------------------------------------


# Publicar en Github

- Tenemos que subir el contenido a GitHub
- [[Publicar en github.io]]


# Servidor con Docker

- Dockerfile:
```bash
# voy a utilizar nginx como servidor web
FROM nginx:latest
# Copiar los archivos de la aplicación web al directorio raíz de nginx
COPY ./dist /usr/share/nginx/html
```

- docker-compose.yml:
```
services:
  web:
    build:
      context: .
      # dockerfile: Dockerfile
    ports:
      - "8080:80"

```

