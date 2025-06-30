# 23. CSS Styles.

Los ***estilos CSS*** permiten poder personalizar la visualización de los elementos de nuestra aplicación.

Existen múltiples maneras de agregar estos estilos a nuestros proyectos de ***REACT***.

	1. Estilos de hojas CSS externas.
	2. Estilos en linea (Atributo style).
	3. Estilos en linea (Objeto JS).
	4. Estilos en modulos.

Veamos a continuación más detalles:

---
## CSS en estructura de proyecto REACT.

Primeramente, necesitamos conocer donde se suelen colocar los ***estilos CSS*** en la estructura de un proyecto ***REACT***.

~~~
my-app/
  README.md
  node_modules/
  package.json
  public/
    index.html
    favicon.ico
  src/
    App.css
    App.js
    App.test.js
    index.css
    index.js
    logo.svg
    components/
    hooks/
    styles/
	    styles.css
~~~

Los ***CSS*** son colocados dentro del directorio `src/` creando un directorio nuevo `styles/`, donde dentro de esta, colocaremos todos nuestros archivos relacionados con ***estilos***.

---
A hora si, aprendamos las diferentes maneras de ingresar ***estilos CSS*** en nuestro ***proyecto***. 

---
## 1. Estilos de hojas CSS externas.

La manera estandarizada de agregar ***estilos CSS*** es por medio de ***importaciones estándar*** de hojas de ***estilos CSS externas***.

Para importar una hoja CSS externa, se realiza con la siguiente sintaxis:

~~~jsx
//importacion de hoja CSS externa llamada "Estilos.css", junto con su ruta 
import "./../styles/Estilos.css";
~~~

Veamos un ejemplo:

Tenemos el siguiente archivo externo CSS con el contenido:

~~~css
.estilos h3 {
	padding: 2rem;
	text-align: center;
}

.bg-react {
	background-color: #61dafb;
}
~~~

***Nota:*** Crea un archivo en el directorio de la estructura del proyecto por default; para este ejemplo, llamaremos al archivo `Estilos.css`.

Y un componente ***JSX*** llamado `Estilos.jsx`, que contiene:

~~~jsx
//importacion de libreria react
import React from "react";

//importacion de hoja CSS externa
import "./../styles/Estilos.css";

//Funcion de componente
export default function Estilos () {

	//Renderizado
	return (
		<section className="estilos">
			<h2>Estilos CSS en REACT</h2>
			<h3 className="bg-react">Estilo de hoja externa</h3>
		</section>
	)
}
~~~

***Nota:*** Para este tipo de importaciones, utilizamos en los ***elementos JSX*** el atributo `className`, que en ***HTML*** simple es igual a `class`.

---
## 2. Estilos en línea (Atributo style).

Otra manera de ingresar ***estilos CSS*** para nuestro proyecto es definiendo estilos en tipo línea, desde el ***elemento JSX*** del componente.

Ejemplo:

~~~jsx
//importacion de libreria react
import React from "react";

//Funcion de componente
export default function Estilos () {

	//Renderizado
	return (
		<section className="estilos">
			<h2>Estilos CSS en REACT</h2>
			<h3 style={{backgroundColor:"#61dafb", padding:"2rem", textAlign:"center", borderRadius:"10px", margin:"5px"}}>Estilos en linea (Atributo style)</h3>
		</section>
	)
}
~~~

***Nota:*** De este modo, no necesitamos un ***archivo .css***; sin embargo, esto puede resultar difícil de entender. 

***Nota:*** No olvides que el atributo `style` contiene 2 `{}`.

---
## 3. Estilos en línea (Objeto JS).

Una diferentes manera de definir los ***estilos CSS*** a los ***elementos JSX*** es definiéndolos en un ***objeto JS*** y asignarlo en el atributo `style`.

Veamos un ejemplo:

~~~jsx
//Importacion de libreria react
import React from "react";

//Funcion de componente
export default function Estilos () {

	//objeto JS con estilos CSS
	let myStyles = {
		backgroundColor:"#61dafb",
		padding:"2rem",
		textAlign:"center",
		borderRadius:"10px",
		border: "3px solid red",
		margin: "5px",
	}

	//Renderizado
	return (
		<section className="estilos">
			<h2>Estilos CSS en REACT</h2>
			<h3 style={myStyles}>Estilos en linea (Objeto JS)</h3>
		</section>
	)
}
~~~

***Nota:*** El contenido dentro del atributo `style` es un objeto, por lo que puede ser definido en formato ***JS*** y asignarlo al elemento ***JSX***.

---
## 4. Estilos en módulos.

Existe una manera mas elegante de aplicar ***estilos CSS*** a nuestro proyecto, esto es por medio de ***módulos***.

Para ello, nuestro archivo ***CSS*** necesita llamarse con extensión final:

`.module.css`

Y en nuestro ***componente*** realizaremos la ***importación*** como ***módulo***.

~~~jsx
import nombreModulo from "ruta/archivo.module.css";
~~~

***Nota:*** Tal cual realizaríamos como un componente ***JSX*** común.

Hagamos un ejemplo, creando un archivo llamado: 

`Estilos.module.css`

Con el contenido:

~~~css
h3 {
	padding: 2rem;
	text-align: center;
}

.error {
	background-color: #dc3545;
}

.success {
	background-color: #198754;
}
~~~

Y dentro de nuestro ***componente*** ingresaremos el ***código***:

~~~jsx
//Importacion de libreria react
import React from "react";

//Importacion de estilos CSS como modulo llamado "moduleStyles" 
import moduleStyles from "./../styles/Estilos.module.css";

//Funcion de componente
export default function Estilos () {

	//Renderizado
	return (
		<section className="estilos">
			<h2>Estilos CSS en REACT</h2>
			<h3 className={moduleStyles.error}>Estilos con Módulos</h3>
			<h3 className={moduleStyles.success}>Estilos con Módulos</h3>
		</section>
	)
}
~~~

***Nota:*** Al utilizar en el archivo `.module.css` reglas generales, estas se aplicarán de manera automática, pero las ***clases*** deben definirse en los ***elementos JSX*** con el atributo `className`.

***Nota:*** La variable `moduleStyles` de la importación es un ***objeto*** que contiene todas las clases del archivo  `Estilos.module.css` dentro, por lo que al querer utilizar una de ellas (por ejemplo, la clase `success`), es necesario definirse como `moduleStyles.success`.