Aplicación cuenta-bancaria. Sigue el workflow que aparece en el repositorio y la documentación [[6. Arrays]]

- Crea al menos 3 commits descriptivos del proyecto.
- Compila el proyecto y crea un script ***npm run build*** para subirlo a un servidor. Actualiza el fichero *README.md* con la url de acceso.



## Tareas

- [ ]  Implementar movimientos con un array de objetos del tipo: #todo 

```json
const movements = [
  {
    date: '2021-01-01',
    value: 1000,
  },
  {
    date: '2021-01-02',
    value: 2000,
  },
  {
    date: '2021-01-03',
    value: 3000,
  },
  {
    date: '2021-01-04',
    value: 4000,
  },
  {
    date: '2021-01-05',
    value: 5000,
  },
  {
    date: '2021-01-06',
    value: 6000,
  },
  {
    date: '2021-01-07',
    value: 7000,
  },
  {
    date: '2021-01-08',
    value: 8000,
  }
]

```

- [ ] Implementar transferencias entre cuentas #todo 
	- [ ] La cantidad a traspasar mayor que 0
	- [ ] Usuario destino debe existir
	- [ ] Usuario origen debe tener suficiente para el traspaso

- [ ] Solicitud de prestamos #todo 
- [ ] Poder ordenar el listado de movimientos. #todo 
- [ ] Mostrar fechas con texto del tipo "hace 2 días" mediante la librería moment.js. #todo 
- [ ] Recibir los movimientos de una petición AJAX #todo 