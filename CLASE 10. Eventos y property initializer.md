
# 10. Events and Property Initializer

En la anterior clase, creábamos funciones dentro de un componente y las asignábamos cada que sucedía un evento.

	Aprendimos que para poder asignar una funcion a un componente, debiamos bindear.

Una nueva manera para simplificar todo el ***bindeo*** de una función, podemos usar las ***ARROW FUNCTIONS***.

Tenemos el mismo código que la clase anterior, con diferencias
	
	- Eliminamos el constructor.
	- el this.state ya no necesita el "this.".
	- las "fumciones" sumar y restar ahora son "arrow functions".

~~~
import React, { Component} from "react";

//Properties initializer
export default class EventosES7 extends Component {
	state = {
		contador:0,
	}

	sumar = (e) => {
		console.log("Sumando");
		console.log(this);
		
		this.setState({
			contador: this.state.contador + 1,
		})
	}

	restar = (e) => {
		console.log("Restando");
		console.log(this);
		
		this.setState({
			contador: this.state.contador - 1,
		})
	}

	render() {
		return (
			<div>
				<h2>
					Eventos en Componentes ES7
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

De esta nueva manera (**traída desde ES7**), nos permite definir y asignar las funciones sin necesidad del ***bindeo***.

***Nota:*** Recordemos que las ***arrow functions*** obtienen el contexto donde se declaran.

