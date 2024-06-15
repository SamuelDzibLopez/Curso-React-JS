# 6. State

## Estado.

Un estado, es el momento actual de un componente, cambiando sus propiedades.

REACT tiene separado sus componentes por nodos, de tal manera que cada vez que deseamos actualizar un componente (una propiedad o visualmente), es necesario cambiar el estado de ese componente; Para ello, REACT realiza un cambio de estado, lo cual es un cambio de ***props*** al mismo tiempo que hace un ***renderizado nuevo*** del ***componente*** en pantalla.

De esta manera, no tiene que actualizar toda la estructura de la pagina (Todo el DOOM), sino, únicamente, el componente que se cambia de estado.

***Estado = cambio de props + renderizado;***

## Declaración de estado.

Para poder declarar el estado de un **componente**, hacemos lo siguiente en un componente:

Agregamos el método ***setState()***

~~~
this.setState({
 //Aqui adentro va el cambio a hacer al cambiar de estado
);
~~~

Un ejemplo mas emplio, aplicado a un componente es:

~~~
import React, {Component} from "react";
//Esportar la clase Component de REACT

//Creacion del componente mediante clase
export default class Estado extends Component {

	/*Creacion del constructor (la funcion tiene una propiedad state 
	(que es un objeto tambien), al mismo tiempo, este tiene contador, que es 0)*/
	constructor (props) {
		super(props);
		this.state = {
			contador: 0,
		}

		//Creacion de un intervalo de cada 1 segundo se ejecute
		setInterval(() => {
		
		//Utilizamos el metodo setState del componente REACT
		this.setState({
		
			//Contador++
			contador: this.state.contador + 1,
		});

		//Impresion de state, cada que se ejecuta el intervalo
		console.log(this.state);
		}, 1000)
	}

	/*metodo render (util en todos los componentes de clases para
	renderizar contenido JSX)*/
	render() {
		//Lo que devuelve la funcion del componente
		return(
			<div>
				<h2>
					El estado
				</h2>
				<p>
					{this.state.contador}
				</p>
			</div>
		)
	}
}
~~~

La función (**componente**) anterior, es un componente que cambia de estado y se renderiza con un intervalo de tiempo de 1 segundo, sumando al atributo contador++, hijo del objeto **state**, que a su vez es un objeto y propiedad de la función padre (**el componente**).

De esta manera, el **componente** cambia sus propiedades y cada que esto ocurre, se renderiza nuevamente en pantalla, visualizando el cambio de estado.

## Cambio de estado de componentes padres a hijos

El ***estado*** de un elemento padre, se le puede pasar como ***prop*** a un elemento hijo.

A continuación, un ejemplo aplicado:

Primero, creamos un componente hijo, declarado desde una funcion expresada.

~~~
function EstadoAHijo(props) {
	return (
		<div>
			<h3>
				{props.contadorHijo}
			</h3>
		</div>
	);
}
~~~

Esta funciono recibirá propiedades del **componente padre***.

Después, hacemos un pequeño cambio a nuestro componente que usamos anteriormente  (El componente se llama **"estado"**).

Dentro del **return** de ese componente, mandamos a llamar el ***componente hijo***, pasandole como ***prop***, el contador que tenia el ***padre***.

~~~
<EstadoAHijo
	contadorHijo = {this.state.contador}
/>
~~~

De esta manera, podemos cambiar el ***estado** de un ***elemento hijo*** dentro de otro elemento, que es el ***padre***.

***Nota:*** Recordemos que ***cambiar el estado***, **No es más que actualizar las props y renderizar en pantalla de nuevo un componente**.
