
## Objetivos

- [ ] Instalar librerías para un proyecto base  📅 2023-12-19 
- [ ] Buscar librerías en el repositorio de npm 📅 2023-12-19 


## Instalación de paquetes

### Producción:
Paquetes que enriquecen nuestro sitio web, como un mapa de Google, un formulario de contacto, un chat de whatsapp...

```bash
npm install --save-prod <nombre paquete>
# o más fácil
npm i <nombre paquete>
```

### Desarrollo
Paquetes que formateen el código, que avisen de errores de código, hace minify del código, comprime imágenes sin perdida de calidad...

```bash
npm install --save-dev <nombre paquete>
# o más fácil
npm i -D <nombre paquete>
```


## Borrar paquetes

```bash
npm remove <nombre-paquete>
```


## Ficheros de dependencias

### package.json
Guardamos listado de dependencias de nuestro proyecto.  Usa [[Versionado semántico]].

### package-lock-json
Asegura la replica exacta de nuestra instalación. Versiones exactas.


## Repositorio npm

Ver https://www.npmjs.com/


