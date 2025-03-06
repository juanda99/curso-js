## Uso de un servicio externo

Consumo de Datos de un Servicio Externo mediante peticiones a APIS:
	- La **carga de datos** debe ser **asíncrona** (usando fetch, axios...)
	- **Gestión de errores** (muestra de mensajes adecuados si la petición falla).

## Interfaz de usuario

- Diseño cuidado compatible con dispositivos móviles y escritorios (Responsive).
- Actualización dinámica de la interfaz sin necesidad de recargar la página:
	- usando elementos como innerHtml en JS o *useState* del framework React 
	- *React-router* en caso de que la web tenga varias url's en el caso de React
- Se recomienda usar un framework de CSS
- Se recomienda usar componentes de terceros, especialmente si usamos un framework como React

## Despliegue

- Uso de un package bundler como **Vite** (alternativas como **Parcel** o **Webpack** son viables, Webpack es el que usa *create-react-app*).  
    ✔ **Framework/Librería de Frontend:**

- Despliegue utilizando servidores propios o externos: Vercel, gh-pages... 
	- En caso de ser un servidor propio indicar en Readme.me la forma de hacerlo. Se valorará en ese caso el uso de contenedores.
	- En el caso de un servidor externo indicar url y la forma de despliegue.

## Control de versiones

- Realización de al menos 5 commits con mensajes claros de la funcionalidad añadida en cada uno de ellos.
- No es necesaria más de una rama de código.
- En caso de partir de un código ya existente, se deben guardar sus commits previos y no hacerlos propios. En el caso de uso de IA para generar un código base, se debe indicar en ese primer commit, sin "partirlo" en commits diferentes para cada funcionalidad. Es decir, vigilaré que cada commit haga lo que dice su mensaje. Eso es lo más importante aquí.

## Documentación

- Breve documentación (fichero README.md) donde se indica tanto el despliegue, como la forma en que cumple cada uno de los requisitos anteriores.



