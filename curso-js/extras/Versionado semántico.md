NPM utiliza algo conocido como [versionado semántico](https://semver.org/lang/es/) para establecer el número de versión de cada una de sus dependencias.

En esencia esta forma de enumerar las versiones es sencilla, todas las versiones tienen 3 dígitos: `x.y.z`

-   El primer dígito representa un cambio mayor.
-   El segundo dígito representa un cambio menor.
-   El tercer dígito representa un parche.

![Diagrama de versionado semántico](https://bernardoayala.com/img/versionado-semantico1.webp)

Cuando creas una nueva versión de tu paquete, debes seguir ciertos criterios a la hora de incrementar estos dígitos:

-   Incrementas el primero si los cambios son tan grandes que cambian la forma en la que funcionaba tu paquete.
-   Incrementas el segundo si agregas una nueva funcionalidad que es compatible con tus versiones anteriores.
-   Incrementas el tercero si lo que hiciste fue arreglar un bug.

![Diagrama de versionado semántico](https://bernardoayala.com/img/versionado-semantico2.webp)

Este sistema para enumerar versiones es el estándar a través de los distintos lenguajes de programación y gestores de paquetes, y es importante que todos los paquetes de `npm` respeten esta notación debido a que esta es importante para establecer reglas sobre las versiones de las dependenicas dentro del archivo `package.json`

Dentro del archivo `package.json` tenemos una serie de símbolos que sirven para establecer reglas para las versiones:

-   `^`: Cuando utilizas el comando `npm update` solo se actualizan parches y cambios menores. Ejemplo: `^2.3.0` puede actualizarse a `2.4.0` o `2.3.1`
-   `~`: En este caso solo se actualizarán los parches. Siguiendo el ejemplo anterior `~2.3.0` puede actualizarse a `2.3.1` pero no a `2.4.0`
-   `>`: Aceptas cualquier versión superior a la actual.
-   `>=`: Aceptas cualquier versión igual o superior a la actual.
-   `<`: Aceptas cualquier versión menor a la actual.
-   `<=`: Aceptas cualquier versión menor o igual a la actual.
-   `=`: Aceptas solo la versión exacta que está listada.
-   `-`: Aceptas un rango de versiones. Ejemplo: `1.2.0` - `1.6.3`
-   `||`: Sirve para combinar reglas. Ejemplo: `< 3.2 || > 3.6`
-   `latest`: Para establecer que deseas usar siempre la última versión disponible.
-   Sin símbolo: Equivalente a `=`, aceptas solo la versión exacta.