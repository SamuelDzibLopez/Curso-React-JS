# 11. Native Events, sinthetics, and personality

Para una mejor comprensión y contenido de este tema:

~~~
[SyntheticEvent – React (reactjs.org)](https://es.legacy.reactjs.org/docs/events.html)
~~~

El ejemplo de un ***native event*** y un ***sinthetic event***.

~~~
import React, { Component } from "react";

export default class MasSobreEventos extends Component {
	handleClick = (e) => {
		//Evento sintetico de REACT
		console.log(e);
		
		//Impresion del elemento JSX (HTML) en la que se hace el evento
		console.log(e.target);
		
		//Evento nativo de vanila JS
		console.log(e.nativeEvent);
		
		//Impresion del elemento JSX (HTML) del evento nativo
		console.log(e.nativeEvent.target);
	}

	render () {
		return (
			<div>
				<h2>
					Mas sobre eventos
				</h2>
				<button onClick={this.handleClick}>
					Saludar
				</button>
			</div>
		)
	}
}
~~~

	-Los eventos NATIVOS son los eventos que podemos usar desde directamente JS.
	 -Los eventos SINTETICOS son los eventos que REACT nos da para usar.

Hagamos un poco mas, complejo el evento, pasando parámetros.
## Pasando parámetros a eventos

Enviemos un mensaje al evento y que este se imprima en consola.

~~~
import React, { Component } from "react";

export default class MasSobreEventos extends Component {
	handleClick = (e, mensaje) => {
		//Evento sintetico de REACT
		console.log(e);
		
		//Impresion del elemento JSX (HTML) en la que se hace el evento
		console.log(e.target);
		
		//Evento nativo de vanila JS
		console.log(e.nativeEvent);
		
		//Impresion del elemento JSX (HTML) del evento nativo
		console.log(e.nativeEvent.target);

		//Impresion de mensaje
		console.log(mensaje);
	}

	render () {
		return (
			<div>
				<h2>
					Mas sobre eventos
				</h2>
					<button onClick={(e) => this.handleClick(e, "Hola, pasando parametro desde un evento")}>
					Saludar
				</button>
			</div>
		)
	}
}
~~~

Con ayuda de una ***arrow function*** podemos obtener un parámetro de un evento.
## Eventos personalizados.

Los eventos personalizados, son eventos que queremos asignar a un ***nuevo componente*** desde otro.

Pongamos el siguiente código para ejemplo:

~~~
function Boton () {
	return (
		<button>
			Boton hecho componente
		</button>
	)
}
~~~

Creamos un nuevo componente en un nuevo archivo e importamos el ***componente*** al **MasSobreEventos***.

Renderizamos el componente ***Boton*** dentro de ***MasSobreEventos*** y le asignamos el evento creado anteriormente **(handleClick)**.

Agregamos al final el codigo:

~~~
<Boton onClick={(e) => this.handleClick(e, "Hola, pasando parametro desde un evento")}/>
~~~

Intentando que cada que el evento ***onClick*** se realice, se ejecute la función **handleClick**.

***Nota:*** Sin embargo... ***ESTO NO FUNCIONARA, NUESTRA FUNCION NO SE EJECUTARA AL DAR CLICK EN EL COMPONENTE EXTERNO.***

Para ello es necesario los ***Eventos personalizados***.

Lo único a hacer es pasar el evento como una ***prop*** al ***componente***.

~~~
<Boton myOnClick={(e) => this.handleClick(e, "Hola, pasando parametro desde un evento")}/>
~~~

	Pasamos al componente Boton, una prop llamada "myOnClick", que es una arrow function a un evento.

También necesitamos modificar nuestro componente.

	¡UNICAMENTE RECIBIENDO LAS PROPS!
	Y ¡ASIGNANDO COMO EVENTO onClick LA PROP!

~~~
function Boton (props) {
	return (
		<button onClick={props.myOnClick}>
			Boton hecho componente
		</button>
	)
}
~~~

De esta manera nuestro ***component*** Boton ya tiene el evento

A esto se le llama un ***Evento Personalizado***.

	LOS "ATRIBUTOS DE EVENTOS" SON PARA LAS ETIQUETAS JSX, ¡NO PARA LOS COMPONENTES!
	Si queremos asignar un evento a un componente, debemos pasar el evento como una prop.



