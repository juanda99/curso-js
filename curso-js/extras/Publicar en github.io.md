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

```
"scripts": {
+   "predeploy": "npm run build",
+   "deploy": "gh-pages -d build",
    "start": "react-scripts start",
    "build": "react-scripts build",
```