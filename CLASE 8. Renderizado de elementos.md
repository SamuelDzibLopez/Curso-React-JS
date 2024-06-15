# 8. Elements Rendering

Renderizado de listas de elementos

En ocasiones necesitaremos renderizar elementos o listas (**ol** o **ul**) en nuestra interfaz, ya sean **arrays** o algún otro tipo de dato.

Para ello un ejemplo basico es:

~~~
import React, {Component} from "react";

export default class RenderizadoElementos extends Component {
	constructor (props) {
		super(props);
		this.state = {
			seasons : ["Primavera", "Verano", "Otoño", "Invierno"],
		}
	}
	render () {
		return (
			<div>
				<h2>
					Renderizado de elemento
				</h2>
				<h3>
					Estaciones del año
				</h3>
				<ol>
					{
					this.state.seasons.map((el) => (
						<li>{el}</li>))
					}
				</ol>
			</div>
		)
	}
}
~~~

En este ejemplo, tenemos un atributo array (**seasons**), que necesitamos renderizar un en el componente **RenderizadoElementos**, cada elemento del array se renderiza en **ol** dentro de un **li**,

***Nota:*** Después de importar nuestro componente en el documento del DOOM, y llamarlo, podremos visualizarlo.

## Atributo key

En el anterior ejemplo, si nosotros renderizamos el ***component***, podremos ver, desde la consola, que muestra un ***warning***, esto se debe a que al renderizar un elemento, este necesita de un atributo único (**una key, o un id**).

		react-jsx-dev-runtime.development.js:95  Warning: Each child in a list should have a unique "key" prop.

El error a mostrarse, debería ser similar al anterior texto.

Para ello, ***REACT*** nos proporciona un atributo llamado ***key***.

Lo único a hacer es ***agregar el atributo key*** a nuestra etiqueta ***JSX***.

~~~
<li key={el}>{el}</li>
~~~

Agregando como valor un dato único, en este caso el mismo texto del contenido de la etiqueta.

***Nota:*** Este atributo ***key*** no se renderiza en el DOOM del HTML, únicamente sirve para identificar el elemento en ***REACT***.

## Renderizado de Elementos REACT

Sucede lo mismo con renderizado de componentes REACT y listas de componentes REACT. necesitamos de una ***key***, a continuación, un ejemplo de un renderizado de ***component*** con ***key***. basado en el ejemplo anterior.

Primero, vamos a crear un archivo con un **JSON**, para poder tener un elemento a ***iterar***.

	Lo llamaremos data.js

~~~
{
	"frameworks" : [
		{
			"id": 1,
			"name" : "REACT",
			"web" : "http://reactjs.org"
		},
		{
			"id": 2,
			"name" : "ANGULAR",
			"web" : "http://angularjs.org"
		},
		{
			"id": 3,
			"name" : "VUE",
			"web" : "http://vuejs.org"
		},
		{
			"id": 4,
			"name" : "POLYMER",
			"web" : "http://polymerjs.org"
		},
		{
			"id": 5,
			"name" : "SVELTE",
			"web" : "http://sveltejs.org"
		}
	]

}
~~~

Este es un ***JSON*** que tiene como atributo un ***array*** con otros ***json*** dentro.

Después, creamos un nuevo componente que se renderizara.

En el ejemplo anterior, renderizábamos un ***elemento de REACT (li)***, aquí estamos renderizando directamente un ***componente de REACT***.

~~~
function ElementoLista (props) {
	return (
		<li>
			<a href={props.el.web}>{props.el.name}</a>
		</li>
	)
}
~~~

Una función de un ***componet*** que renderiza un ***li***.

El ***a*** redirigirá hacia la **URL (atributo web)** del ***JSON*** en iteración, y el texto será el ***nombre (atributo name)*** del ***JSON*** en iteración.

Todos estos datos se reciben como ***props*** al llamar al componente en el ***component*** padre más adelante.

***Nota:*** Recordemos que todas las ***props*** enviadas a un componente, se reciben mediante el ***objeto: props***.

Después en nuestro componente padre

	-Importamos el componente ElementoLista
	-Importamos el data.json

~~~
import data from "../helpers/data.json";
~~~

Para ser usados en el ***componet*** padre.

y renderizaremos el elemento en ***RenderizadoElemento***

~~~
export default class RenderizadoElementos extends Component {
	constructor (props) {
		super(props);
		this.state = {
			seasons : ["Primavera", "Verano", "Otoño", "Invierno"],
		}
	}
	render () {
		console.log(data);
		return (
			<div>
				<h2>
					Renderizado de elemento
				</h2>
				<h3>
					Estaciones del año
				</h3>
				<ol>
					{
						this.state.seasons.map((el) => (
							<li key={el}>{el}</li>
						))
					}
				</ol>
				<h3>Frameworks Frontend JS</h3>
				<ul>
					{data.frameworks.map((el) =>
						<ElementoLista
							key={el.id}
							el = {el}
						/>
					)}
				</ul>
			</div>
		)
	}
}
~~~

Solo se le agregan líneas de código, al ***component*** que teníamos anteriormente.

Lo que hace la parte anexada del código es:

	-Imprimir un <h3> con un texto
	-Crear un <ul> donde se renderizaran los componentes <ElementosLista/> de forma iterada.
	-Hacer un .map al JSON importado (son 5 veces), y por cada map, captura el elemento (el json secundario con informacion de los frameworks), para luego RENDERIZAR el COMPONENTE <ElementosLista/>, pasandole:
		 -Como atributo key (de REACT) el valor del atributo id del elemento
		 -Y el elemento completo como prop "el" (todo el JSON secundario (id, name, web)), para luego poder ser usado en el componente hijo 

***Nota:*** Recordemos que el atributo ***key*** se le asigna directamente al componente renderizado para evitar el **warning de REACT**,  por lo que este, no es utilizado en el código del ***component*** hijo.

Si queremos hacer mas estético nuestro componente hijo, simplemente agregamos el **target="_blank"**

~~~
function ElementoLista (props) {
	return (
		<li>
			<a href={props.el.web} target="_blank">{props.el.name}</a>
		</li>
	)
}
~~~

Simplemente, para abrir nuestro **enlace** en una nueva pestaña.

**DE ESTA MANERA, RENDERIZAMOS UNA LISTA DE COMPONENTES**
