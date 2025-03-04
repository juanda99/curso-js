
- Vamos a preparar un servidor web que muestre datos ficticios de cuentas bancarias. El repo con toda la práctica hecha es el siguiente:
	https://github.com/juanda99/faker-server

- Creamos la carpeta para el proyecto y lo inicializamos como proyecto de node:
```
mkdir faker-server
cd faker server
npm init
```
- Instalamos express, un servidor web minimalista y "unopinated":
```
npm install express
```
- Creamos un fichero ***index.mjs***
	- en node por defecto, las librerías se importan con *require*, como lo queremos hacer igual que en *JavaScript*, mediante módulos, el fichero lo debemos guardar con extension *mjs*
```js
// const express = require('express')
import express from 'express'

// creamos el web server
const app = express()

// definimos endpoints:

app.get('/', function (req, res) {
  res.send('Hola Mundo')
})

app.get('/accounts', function (req, res) {
  res.send('Aquí mostraría las cuentas')
})

// arrancamos la app
// app.listen(port, [opcional función])
app.listen(3000, function () {
  console.log('app listening on port 3000!')
})```

- Ejecutamos mediante *node index.mjs* y desde el navegador vemos que nos devuelve los datos en las siguientes urls:
```
localhost:3000
localhost:3000/accounts
```

- Si modificamos los ficheros, hay que volver a reiniciar nuestro servidor. Para evitarlo, instalamos un monitor de node:
```
npm install nodemon
```
- Ahora podemos arrancar nuestro programa mediante ***nodemon index.mjs*** y se actualiza cada vez que cambiamos el código fuente. 
	- Ojo, nodemon no está en el path del sistema, así que habría que llamarlo con 
	```bash
	node_modules/.bin/nodemon index.mjs
	```

- Lo introducimos como script ***npm start*** en el fichero package.json para que sea más sencillo:
```json
...
"scripts": {
	"test": "echo \"Error: no test specified\" && exit 1",
	"start": "nodemon index.mjs"
...
},
```

- Por último vamos a añadir la [librería faker](https://fakerjs.dev/) para insertar datos ficticios:
```bash
npm install @faker-js/faker
```

- El código usando la librería quedaría así:
```js
// const express = require('express')
import express from 'express'
import { faker } from '@faker-js/faker'

const app = express()

function createAccount() {
  const nombre = faker.person.fullName()
  const email = faker.internet.email()
  const direccion = faker.location.streetAddress()
  const edad = Number(faker.number.bigInt({ min: 18n, max: 99n }))
  return { nombre, email, direccion, edad }
}

function createAccounts(n) {
  const accounts = []
  for (let i = 0; i < n; i++) {
    accounts.push(createAccount())
  }
  return accounts
}

// creo 30 cuentas falsas
const accounts = createAccounts(30)

app.get('/', function (req, res) {
  res.send('Hola Mundo')
})

app.get('/accounts', function (req, res) {
  // const accountTexto = JSON.stringify(accounts)
  // res.send(accountTexto)
  res.json(accounts)
})

app.listen(3000, function () {
  console.log('Example app listening on port 3000!')
})
```

- Ojo, usamos *res.json* porque accounts es un objeto y hay que pasarlo a texto. La otra opción sería hacerlo así:

```
const accountTxt = JSON.stringify(accounts)
res.send(accountTxt)
```

- Advertencia:
	- JSON.stringify falla con el tipo de dato bigInt, por lo que tuvimos que convertirlo primero mediante Number a un tipo más pequeño
	
```
const edad = Number(faker.number.bigInt({ min: 18n, max: 99n }))
```

- TODO: instalar *cors* para que se pueda acceder a los datos desde una API.