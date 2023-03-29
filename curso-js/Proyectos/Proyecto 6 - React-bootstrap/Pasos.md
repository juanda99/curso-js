
Creamos la aplicación react:

```bash
npx create-react-app products
```

Instalamos la librería *react-bootstrap*:
```bash
npm install react-bootstrap bootstrap
```
Importamos la librería css de bootstrap, usando CDN, fichero local o SASS:

```bash

# opción 1
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/css/bootstrap.min.css"
  integrity="sha384-rbsA2VBKQhggwzxH7pPCaAqO46MgnOM80zW1RWuH61DGLwZJEdK2Kadq2F9CUG65"
  crossorigin="anonymous"
/>

#opción 2
{/* The following line can be included in your src/index.js or App.js file */}

import 'bootstrap/dist/css/bootstrap.min.css';

# opción 3
/* The following line can be included in a src/App.scss */

@import "~bootstrap/scss/bootstrap";

/* The following line can be included in your src/index.js or App.js file */

import './App.scss';
```

En el caso de usar Sass, habrá que añadir la librería de sass:

```bash
npm i -D sass
```


## Enrutamiento en react

Buscamos paquetes en npm. No viene un paquete ya integrado en el framework como en Angular. Pero hay un estándar de facto, *react-router*.

```jsx

import './App.scss'
import { createBrowserRouter, RouterProvider } from 'react-router-dom'
import Home from './pages/Home'
import Products from './pages/Products'
import Contact from './pages/Contact'

const router = createBrowserRouter([
  {
    path: '/',
    element: <Home />,
  },
  {
    path: 'products',
    element: <Products />,
  },
  {
    path: 'contact',
    element: <Contact />,
  },
])

function App() {
  return <RouterProvider router={router} />
}

export default App
```


También se puede elegir otro tipo de sintaxis más al estilo jsx: https://reactrouter.com/en/main/utils/create-routes-from-elements


## Añadir un layout

```bash
import './App.scss'
import { createBrowserRouter, RouterProvider } from 'react-router-dom'
import Home from './pages/Home'
import Products from './pages/Products'
import Contact from './pages/Contact'
import Container from 'react-bootstrap/Container'
import Menu from './components/Menu'
const router = createBrowserRouter([
  {
    path: '/',
    element: <Home />,
  },
  {
    path: 'products',
    element: <Products />,
  },
  {
    path: 'contact',
    element: <Contact />,
  },
])

function App() {
  return (
    <>
      <Menu />
      <Container fluid="md">
        <RouterProvider
          router={router}
          fallbackElement={<p>Cargando página...</p>}
        />
      </Container>
    </>
  )
}

export default App
```

Y ahora el componente de Menu:

```jsx
import Container from 'react-bootstrap/Container'
import Nav from 'react-bootstrap/Nav'
import Navbar from 'react-bootstrap/Navbar'

function Menu() {
  return (
    <Navbar bg="light" expand="lg">
      <Container>
        <Navbar.Brand href="/">Logotipo</Navbar.Brand>
        <Navbar.Toggle aria-controls="basic-navbar-nav" />
        <Navbar.Collapse id="basic-navbar-nav">
          <Nav className="me-auto">
            <Nav.Link href="/">Home</Nav.Link>
            <Nav.Link href="/products">Productos</Nav.Link>
            <Nav.Link href="/contact">Contactar</Nav.Link>
          </Nav>
        </Navbar.Collapse>
      </Container>
    </Navbar>
  )
}

export default Menu
```

Al cambiar entre páginas hay recarga, está llamando al servidor...

Hay que usar un "Link" del paquete react-router o similar (ver https://www.npmjs.com/package/react-router-bootstrap)

