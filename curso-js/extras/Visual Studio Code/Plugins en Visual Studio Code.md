##  Login
Debemos hacer login para sincronizar nuestra configuración entre todos los equipos

## [prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

¡¡**Necesita tener instalado el paquete de [[prettier]] en el sistema!!**

Instalarla y habilitarla.

Definirlo como el formateador por defecto de nuestro código (*Preference->Settings -> Default formatter*)

Configurar también *Format on save: true*


### Probar funcionamiento

```js
"use  strict"

const nombre = "pepe"
if(nombre=="pepe") console.log('¡Te llamas pepe!')
const edad = (añoNacimiento) => 2022 - añoNacimiento 
```

Guarda el código  anterior  y observa que prettier hace ciertos cambios (según nuestra configuración)
	- Elimina líneas blancas extra
	- Añade línea blanca al final
	- Fin de línea con ;
	- Espacio entre if y condición
	- Comillas dobles
	- ...

Está bien que lo haga por nosotros pero  puede ser que algunas cosas nos gusten a "nuestro modo". Es un formateador "con opinión" pero nos da cierta libertad.
- Creamos un  fichero .prettierrc y  cambiamos las  opciones que no nos gusten, por ejemplo single quotes,  el paréntesis en la función  flecha anterior o la finalización con ;
- Mira  en https://prettier.io/docs/en/configuration.html



## [eslint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
¡¡**Necesita tener  instalado el paquete de [[eslint]] en el sistema**!!

## [htmlhint](https://marketplace.visualstudio.com/items?itemName=mkaufman.HTMLHint)
Extensión para poder ver los errores en el código html
¡¡**Necesita tener  instalado el paquete de htmlhint en el sistema**!!


## [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)

## [Todo highlight](https://marketplace.visualstudio.com/items?itemName=wayou.vscode-todo-highlight)

Subraya etiquetas **TODO** y  **FIXME**
## [Todo tree](https://marketplace.visualstudio.com/items?itemName=Gruntfuggly.todo-tree)
Muestra listado de etiquetas

## [Quokka.js](https://marketplace.visualstudio.com/items?itemName=WallabyJs.quokka-vscode)

## [Snippets para ecosistema React y ES7](ES7+ React/Redux/React-Native snippetsES7+ React/Redux/React-Native snippets)



