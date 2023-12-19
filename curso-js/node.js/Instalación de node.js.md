
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

De https://github.com/nodesource/distributions

```bash
sudo apt-get update
sudo apt-get install -y ca-certificates curl gnupg
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg
NODE_MAJOR=20
echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_$NODE_MAJOR.x nodistro main" | sudo tee /etc/apt/sources.list.d/nodesource.list
sudo apt-get update
sudo apt-get install nodejs -y
```

### nvm

Ver la parte de install en el repositorio de GitHub:
https://github.com/nvm-sh/nvm


Más info en la propia web de node.js:

Ver más en https://nodejs.org/en/download/package-manager/