# 9. Events and Binding

Podemos hacer renderizados de componentes cada que se ejecute un evento; Ya sea un **click** o algún otro.

Para ello, en ***REACT***, se le asignan a los componentes, funciones, tales como antiguamente se hacían en ***HTML***.

De la siguiente forma, como un ejemplo:

~~~
<button onClick={this.sumar}>
	+
</button>
~~~

Esta manera, se llama a una función, llamada **sumar** definida en el **component (por ello tiene el this)** cada que se hace **click** en el elemento button **JSX**.

***Nota:*** Existe una diferencia entre los eventos en ***REACT*** y el ***antiguo HTML***, usamos el **cameCase**.

De esta forma, ya podemos crear un componente para ejemplificar mejor:

~~~
import React, { Component} from "react";

export default class Eventos extends Component {
	constructor (props) {
		super(props);
		this.state = {
			contador:0,
		}
	}

	sumar (e) {
		console.log("Sumando");
		console.log(this);
		this.setState({
			contador: this.state.contador + 1,
		})
	}

	render() {
		return (
			<div>
				<h2>
					Eventos en Componentes
				</h2>
				<nav>
					<button onClick={this.sumar}>
						 +
					</button>

					<button>
						-
					</button>
				</nav>
				<h3>
					{this.state.contador}
				</h3>
			</div>
		)
	}
}
~~~

En el presente ****component***, se presenta un renderizado de **2 botones**, donde uno tiene asignado cada vez que se ejecute el evento ***onClick*** se ejecute la función ***sumar***.

Y el **h3** renderiza el valor del ***state.contador*** que por inicio es **0**. 

PERO..., Existen algunos inconvenientes en este código, ya que en la función ***sumar*** el **this** no esta definido

	Podemos verificarlo dando click en el boton +

Deciendo el siguiente error.

	Cannot read properties of undefined (reading 'setState')

Lo que significa que no puedes usar un ***read properties*** en algo (**this** en este caso) que no esta definido.

Esto sucede con los ***components*** basados en ***clases***.

Para ello, hay que hacer un pequeño cambio en el ***constructor*** del ***component***.

Asi:

~~~
constructor (props) {
	super(props);
		this.state = {
			contador:0,
		}

		this.sumar = this.sumar.bind(this);
}
~~~

A esto se le llama ***bindear***.

Lo que hace es:

	-Declararle a la clase una propiedad llamada sumar, que iguala al metodo sumar que ya tiene y le enlaza o bondea el elemento this.

Quedando de la siguiente manera:

~~~
import React, { Component} from "react";

export default class Eventos extends Component {
	constructor (props) {
		super(props);
		this.state = {
			contador:0,
		}

		this.sumar = this.sumar.bind(this);
	}

	sumar (e) {
		console.log("Sumando");
		console.log(this);
		this.setState({
			contador: this.state.contador + 1,
		})
	}

	render() {
		return (
			<div>
				<h2>
					Eventos en Componentes
				</h2>
				<nav>
					<button onClick={this.sumar}>
						+
					</button>

					<button>
						-
					</button>
				</nav>
				<h3>
					{this.state.contador}
				</h3>
			</div>
		)
	}
}
~~~

Listo, ya funciona el botón de **suma**, agreguémosle el botón de **resta**.

Creamos una nueva función.

~~~
restar (e) {
	console.log("Sumando");
	console.log(this);
	this.setState({
		contador: this.state.contador - 1,
	})
}
~~~

Lo bindeamos en el ***constructor***.

~~~
this.restar = this.restar.bind(this);
~~~

Y le asignamos el ***event*** al botón de resta.

~~~
<button onClick={this.restar}>
	-
</button>
~~~

Listo, nuestro código de ***component***, queda de la siguiente manera.

~~~
import React, { Component} from "react";

export default class Eventos extends Component {
	constructor (props) {
		super(props);
		this.state = {
			contador:0,
		}

		this.sumar = this.sumar.bind(this);
		this.restar = this.restar.bind(this);
	}

	sumar (e) {
		console.log("Sumando");
		console.log(this);
		this.setState({
			contador: this.state.contador + 1,
		})
	}

	restar (e) {
		console.log("Sumando");
		console.log(this);
		this.setState({
			contador: this.state.contador - 1,
		})
	}

	render() {
		return (
			<div>
				<h2>
					Eventos en Componentes
				</h2>
				<nav>
					<button onClick={this.sumar}>
						+
					</button>

					<button onClick={this.restar}>
						-
					</button>
				</nav>
				<h3>
					{this.state.contador}
				</h3>
			</div>
		)
	}
}
~~~