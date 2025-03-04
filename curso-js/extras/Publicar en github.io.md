Ver en https://github.com/gitname/react-gh-pages

Instalamos el paquete de node:
```bash
$ npm i -D gh-pages
# npm install --save-dev gh-pages
```
Añadimos el parámetro homepage al package.json con la url modificando {usuario} y {repo-name} por el usuario y el repositorio en cuestión:
```json
{
  "name": "my-app",
  "version": "0.1.0",
+ "homepage": "https://{usuario}.github.io/{repo-name},
  "private": true,
```

Añadimos el script de deploy:
- Primero hacemos una compilación con el "predeploy" que lo ejecutará siempre antes del deploy
- En el deploy indicamos el directorio donde están los ficheros compilados. ***Cambiar dist por el que proceda***

```json
"scripts": {
+   "predeploy": "npm run build",
+   "deploy": "gh-pages -d dist",
    "start": "react-scripts start",
    "build": "react-scripts build",
```

Podríamos haber hecho un solo script:
```js
"scripts": {
+   "deploy": "npm run build && gh-pages -d dist",
    "start": "react-scripts start",
    "build": "react-scripts build",
```

Si usamos ***vite*** deberemos añadir el campo *base* que es el directorio que forma parte de la url de enlace para la carga de las hojas de estilo y el fichero de javaScript.
Lo hacemos modificando el fichero *vite.config.js*
- Esto en el caso de una aplicación en React:
```js
import { defineConfig } from 'vite'  
import react from '@vitejs/plugin-react'  
  
// https://vitejs.dev/config/  
export default defineConfig({  
plugins: [react()],  
base: "/nombre-repositorio-github/"  
})
```
- Si la aplicación es de Vanilla JS, habría que añadir el fichero con este contenido:
```json
import { defineConfig } from "vite";
// https://vite.dev/config/
export default defineConfig({
	base: "/nombre-repositorio-github/",
});
```


En el repositorio de GitHub -> Settings -> Pages (barra lateral).
 Seleccionar fuente: ***Deploy from branch*** y como rama ***gh-pages***.
 