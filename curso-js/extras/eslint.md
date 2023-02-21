
## Instalación

### Instalación interactiva
```bash
npm init @eslint/config
```
Nos instala eslint y nos crea un fichero de configuración

### Instalación manual
```bash
npm install -D eslint
```
Copiamos el fichero de configuración de eslint de otro proyecto

## Integración con  [[prettier]]

```bash
npm install -D eslint-config-prettier
```

Añadir en  el fichero *.eslintrc.json*:

```js
{
  "extends": [
    "some-other-config-you-use",
    "prettier"
  ]
}
```

## Configurar en [[Plugins en Visual Studio Code|Visual Studio Code]]