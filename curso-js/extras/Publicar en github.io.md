Ver en https://github.com/gitname/react-gh-pages

Instalamos el paquete de node:
```bash
$ npm i -D gh-pages
```
Añadimos el parámetro homepage al package.json con la url:
```json
{
  "name": "my-app",
  "version": "0.1.0",
+ "homepage": "https://{usuario}.github.io/{repo-name},
  "private": true,
```
Añadimos el script de deploy:

```json
"scripts": {
+   "predeploy": "npm run build",
+   "deploy": "gh-pages -d build",
    "start": "react-scripts start",
    "build": "react-scripts build",
```

Podríamos haber hecho un solo script:
```js
"scripts": {
+   "deploy": "npm run build && gh-pages -d build",
    "start": "react-scripts start",
    "build": "react-scripts build",
```

Si usamos ***vite*** deberemoa añadir el campo *base* que es el directorio que forma parte de la url de enlace para la carga de las hojas de estilo y el fichero de javaScript.
```js
import { defineConfig } from 'vite'  
import react from '@vitejs/plugin-react'  
  
// https://vitejs.dev/config/  
export default defineConfig({  
plugins: [react()],  
base: "/nombre-repositorio-github/"  
})
```


En el repositorio de GitHub -> Settings -> Pages (barra lateral).
 Seleccionar fuente: ***Deploy from branch*** y como rama ***gh-pages***.
 