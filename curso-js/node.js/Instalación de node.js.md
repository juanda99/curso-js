
Comprobamos que esté instalado node.

```
node --version / node -v
npm --version / npm -v
``` 
  
Si no es así, se puede instalar como paquete del sistema (npm viene incluido en node.js):
```
apt remove nodejs
apt install nodejs
```

La versión de nodejs que tenemos es la 12 (Ubuntu 22.04). Como es un poco antigua, vamos a instalar algo más actual.

Se puede instalar mediante un gestor  de versiones como ***nvm (node version manager)*** o añadir repositorio de node.js.

### Añadir repositorio node.js

```bash
cd ~
curl -sL https://deb.nodesource.com/setup_18.x -o nodesource_setup.sh
```

### nvm

Ver la parte de install en el repositorio de GitHub:
https://github.com/nvm-sh/nvm


Más info en la propia web de node.js:

Ver más en https://nodejs.org/en/download/package-manager/