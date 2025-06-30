# 25. React´s Frameworks CSS.

Existen diferentes ***frameworks*** útiles para nuestros proyectos, compatibles con ***REACT***.

Para esta clase, es recomendable la creación de nuevo proyecto de ***React***, el cual:

	- No tenga estilos CSS integrados.
	- El app.js sea simple (Solo un h1 con nombre de clase).

Donde en dicho ***proyecto*** aprenderemos como utilizar los diferentes ***frameworks***.

---
## Bootstrap.

Para poder utilizar ***bootstrap*** dentro de nuestro proyecto, basta con ingresar la etiquetas especificadas en la pagina oficial de ***bootstrap*** en nuestro archivo `index.html`.

	https://getbootstrap.com/

Vemos cuales serian estas:

~~~html
 <!--Hoja de estilos CSS de Bootstrap-->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
~~~

Y:

~~~html
 <!--script de Bootstrap-->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-YvpcrYf0tY3lHB60NNkmXc5s9fDVZLESaAA55NDzOxhy9GkcIdslK1eN7N6jIeHz" crossorigin="anonymous"></script>
~~~

***Nota:*** Con estos elementos ingresados, en nuestro proyecto ya podremos utilizar componentes de ***bootstrap***  en nuestro proyecto.

### Ejemplo de uso de Bootstrap con React.

Veamos un ejemplo:

Suponiendo que las ***etiquetas requeridas*** ya se encuentren en nuestro `index.html` del proyecto, podemos generar un archivo `.jsx` con el siguiente componente:

No olvidemos eliminar cualquier `archivo de estilos y CSS`:

~~~jsx
import React from "react";

export function Navbar() {
	 return (
		 <nav className="navbar navbar-expand-lg bg-body-tertiary">
			 <div className="container-fluid">
				<a className="navbar-brand" href="#">
					Navbar
				</a>
				<button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
					<span className="navbar-toggler-icon"></span>
				</button>
				<div className="collapse navbar-collapse" id="navbarSupportedContent">
					<ul className="navbar-nav me-auto mb-2 mb-lg-0">
						<li className="nav-item">
							<a className="nav-link active" aria-current="page" href="#">
								Home
							</a>
						</li>
						<li className="nav-item">
							<a className="nav-link" href="#">
								Link
							</a>
						</li>
						<li className="nav-item dropdown">
							<a className="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
								Dropdown
							</a>
							<ul className="dropdown-menu">
								<li>
									<a className="dropdown-item" href="#">
										Action
									</a>
								</li>
								<li>
									<a className="dropdown-item" href="#">
										Another action
									</a>
								</li>
								<li>
									<hr className="dropdown-divider" />
								</li>
								<li>
									<a className="dropdown-item" href="#">
										Something else here
									</a>
								</li>
							</ul>
						</li>
						<li className="nav-item">
							<a className="nav-link disabled" aria-disabled="true">
								Disabled
							</a>
						</li>
					</ul>
					<form className="d-flex" role="search">
						<input className="form-control me-2" type="search" placeholder="Search" aria-label="Search" />
						<button className="btn btn-outline-success" type="submit">
							Search
						</button>
					</form>
				</div>
			</div>
		</nav>
	);
}

export default function Bootstrap() {
	return (
		<>
			<h2>Bootstrap</h2>
		</>
	);
}
~~~

***Nota:*** Debido a que en ***React*** el contenido a renderizar de un ***componente*** es ***JSX*** y no ***HTML***, posiblemente necesites modificar algunas etiquetas de componentes de ***Bootstrap***, tales como los `<input/>` y ``className`.

 Y llamarlos en nuestro `App.js`:

~~~jsx
import Bootstrap, {Navbar} from './components/Bootstrap.jsx';

function App() {
	return (
		<div>
			<h1>Frameworks CSS con React</h1>
			<Bootstrap/>
			<Navbar/>
		</div>
	);
}

export default App;
~~~

***Nota:*** Esto debería mostrar un ***navbar*** de ***Bootstrap***, ***¡intenta importar algún otro componente de Bootstrap!***.

---
## Bulma

***Bulma*** es un ***framework*** principalmente de ***CSS***, pero es muy similar a ***bootstrap***.

	https://bulma.io/documentation/start/installation/

al igual que el ***framework*** anterior, la manera mas fácil de importar para utilizar es mediante un ***CDN***:

El cual es:

~~~html
<!--Bulma-->
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/bulma@1.0.2/css/bulma.min.css"
>
~~~

***Nota:*** Y colocarlo en el `index.html` de nuestro proyecto.

***Nota:*** ¡Es importante utilizar solo un ***framework*** por proyecto, esto debido a que los ***frameworks*** suelen utilizar las mismas ***clases***.

### Ejemplo de uso de Bulma con React.

Veamos un ejemplo de uso:

Tenemos los ***2 componentes*** en un archivo `.jsx`.

~~~jsx
import React from "react";

export function Card() {
	return (
		<div className="card">
			<div className="card-image">
				<figure className="image is-4by3">
					<img src="https://bulma.io/assets/images/placeholders/1280x960.png" alt="Placeholder image" />
				</figure>
			</div>
			<div className="card-content">
				<div className="media">
					<div className="media-left">
						<figure className="image is-48x48">
							<img src="https://bulma.io/assets/images/placeholders/96x96.png" alt="Placeholder image" />
						</figure>
					</div>
					<div className="media-content">
						<p className="title is-4">John Smith</p>
						<p className="subtitle is-6">@johnsmith</p>
					</div>
				</div>
				<div className="content">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus nec iaculis mauris. <a>@bulmaio</a>. <a href="#">#css</a>
				<a href="#">#responsive</a>
				<br />
					<time dateTime="2016-1-1">11:09 PM - 1 Jan 2016</time>
				</div>
			</div>
		</div>
	);
}

export default function Bulma() {
	return (
		<>
			<h2>Bulma</h2>
		</>
	);
}
~~~

***Nota:*** No olvides al tomar un ***componente*** cambiar ***atributos*** y ***etiquetas*** ***HTML*** a ***JSX***.

Para llamarlo en el archivo `App.js`:

~~~jsx
import Bulma, {Card} from "./components/Bulma.jsx";

function App() {
	return (
		<div>
			<h1>Frameworks CSS con React</h1>
			<Bulma/>
			<Card/>
		</div>
	);
}

export default App;
~~~

La ventaja de muchos ***frameworks*** es el ***RESPONSIVE***.

