- Usaremos la página web https://vite.dev/
- El comando de ejecución del nuevo proyecto es:
```
npm create vite@latest
```

- Crearemos un proyecto con React o con VanillaJS, según corresponda, basta seguir los pasos

- Una opción sería coger un template adecuado a nuestras características de modo que no tengamos que configurar los linters, css, o lo que corresponda. 
- Por ejemplo: 
- https://github.com/Barata-Ribeiro/vite-vanilla-js-template
```bash
npm install -g degit 
degit Barata-Ribeiro/vite-vanilla-js-template <miProyecto>
cd <miProyecto>
npm install # al descarga el proyecto los paquetes no están en node_modules
npm run dev
```

- Recordar que en el fichero package.json, en la parte de scripts está como funcionar con vite, principalmente:
  ```
  npm run dev # para ejecutar un live server
  num run build # para "compilar" nuestro proyecto en la carpeta /dist
  ```
## Notas:
- *degit* solo copia el último código, es mucho más ligero que hacer un *git clone*

  