
# 13. Component Life Cycle

El ***Ciclo de vida*** de los ***components*** son métodos especiales que ***REACT*** nos ofrece para ejecutar ciertas cosas de manera automática.

Existen 3 ciclos de vida

	- Montaje
		- Insersion en el DOOM
	- Actualizacion
		- Renderizado y cambio de State
	- Desmontaje
		- Eliminación del componente del DOM

Algunos métodos para estos ***states*** son:
## Montaje:

El **constructor***:

~~~
constructor ()
~~~

Este método se ejecuta al inicio de todo ***component***, desde el momento de inicializar el ***state***.

El **render***:

~~~
render ()
~~~

Es el método que se encarga de renderizar en pantalla (las veces que sean necesarias), el ***component*** cuando se hace un cambio de ***state***.

y el **ComponentDidMount**

~~~
componentDidMount ()
~~~

Este método, se ejecuta, cuando un ***component*** es insertado en el DOM.

***Nota:*** NO es igual que el método render, para hacer el método ***componentDidMount()*** primero debe ejecutarse ***render()***.
## Actualización:

El **render**:

~~~
render ()
~~~

Este método, es el mismo que el anterior, simplemente se ejecuta, tanto cuando se renderiza la primera vez, como cuando se actualice.

Y el **ComponentDidUpdate**:

~~~
componentDidUpdate ()
~~~

Este método, se ejecuta, cuando el componente, es actualizado, cuando cambia de ***state***.

	Puede servirnos para obtener los datos del state o props antess de cambiar
## Desmontaje:

El **ComponentWillUnmount**:

~~~
componentWillUnmount ()
~~~

Evento que se ejecuta cuando el ***component*** es removido del DOM.

## Ejemplo con 2 componentes

En el siguiente ejemplo, podras ver, una funcionalidad de los ***métodos del ciclo de vida***

	- Es un codigo para realizar un reloj.

	- Se trata de un componente padre con 2 botones 
		- Uno para iniciar el tiempo
		- otro para detener.
	-Cada que se inicie el componente hijo se inserta en el DOM y se actualiza cada segundo.
	-Cada que se detiene el componente hijo se elimina del DOM y se actualiza su estado por ultima vez (visible: true).

	El componente hijo recibe de props del padre la hora.

A continuación el código del elemento padre:

~~~
import React, { Component } from "react";

export default class CicloVida extends Component {

	//Cuando el component se inicializa
	constructor (props) {
		super(props);
		console.log("0, Metodo constructor: Se inicializa, aun NO esta en el DOM");

		this.state = {
			hora: new Date().toLocaleTimeString(),
			visible: false
		}

		this.temporizador = null
	}

	//Metodo cunado el component se inserta en el DOM (no cunado se dibuja en pantalla)
	componentDidMount() {
		console.log("1, Metodo componentDidMount, El componente ya se encuentra en el DOM");
	}

	//Cuando el componente se actualiza (cambia de estado y  se renderiza nuevamente)
	//Puede servirnos para guardar las props antes de cambiar de estado (antes de cambiar las props)

	componentDidUpdate (prevProps, prevState) {
		console.log("2, Metodo componentDidUpdate, El state del componente a cambiado");
		console.log(prevProps);
		console.log(prevState);
    }

	tiktak = () => {
		this.temporizador = setInterval (() => {
			this.setState ({
				hora: new Date().toLocaleTimeString()
			})
		}, 1000)
	}

	iniciar = () => {
		this.tiktak();
		this.setState({
			visible: true
		})
	}

	detener = () => {
		clearInterval(this.temporizador);
		this.setState({
			visible: false
		})
	}

	//Cuando el metodo se renderiza en pantalla (una primeera vez o mas)
	render () {
		console.log("4, Metodo render: el componente se (re)dibuja en el DOM (renderizado en pantalla)");
		return (
			<>
				<h2>
					Ciclo de vida de los componentes
				</h2>

				{this.state.visible && <Reloj hora = {this.state.hora}/>}

				<button onClick={this.iniciar}>
					Iniciar
				</button>

				<button onClick={this.detener}>
					Detener
				</button>
			</>
		)
	}
}
~~~

Y el código del ***component hijo***.

~~~
class Reloj extends Component {
	constructor (props) {
		super(props);
	}
	
	//Cuando el component el eliminado del DOM
	componentWillUnmount () {
		console.log("3, Metodo componentWillUnmount, El componente a sido eliminado del DOM");
	}

	render () {
		return <h3>{this.props.hora}</h3>
	}
}
~~~

***Nota:*** No olvidemos importar el ***component hijo*** y exportar el ***component padre***.

	El component hijo (Reloj) no esta export default

