# 12. Communication Between Components

Esta clase tiene como objetivo entender como se realiza la comunicación entre componentes.

	REACT es Unidireccional (una sola dirección)
## Comunicación de un componente Padre a un Hijo

	Con las props

Para ello, creamos un ***component*** llamado **"Padre"**.

~~~
export default class Padre extends Component {
	state = {
		contador: 0,
	}

	incrementarContador = (e) => {
		this.setState({
			contador: this.state.contador + 1
		})
	}

	render() {
		return (
			<>
				<h2>
					Comunicación entre Componentes
				</h2>
				<Hijo
					incrementarContador = {this.incrementarContador}
					
					//Comunicacion de Padre a Hijo
					mensaje = "Mensaje para el hijo 1"
				/>

				<Hijo
					incrementarContador = {this.incrementarContador}

					//Comunicacion de Padre a Hijo
					mensaje = "Mensaje para el hijo 2"
				/>

				{console.log("renderizando padre")}
				{console.log(this.state.contador)}
				</>

        )

    }

}
~~~

También creamos otro ***component*** "Hijo", el cual renderizaremos en el "Padre".

~~~
function Hijo (props) {
	return (
		<>
			<h3>
				{props.mensaje}
			</h3>
			<button
				//Comunicacion de Hijo a Padre, ejecutando el evento
				onClick={props.incrementarContador}>
					+
			</button>
			
			{console.log("Renderizando Hijo")}
		</>
	)
}
~~~

De esta manera, un ***Componente Padre, puede comunicarse con un Componente Hijo***. 

***Nota:*** 
- No olvides importar el ***componente Padre*** para ser renderizado en pantalla
- Importar el ***componente hijo*** en el archivo del componente ***padre***.
## Comunicación entre Hijo a Padre

	Con eventos

***¿Cómo puede hacer esto?***

Que el ***Component hijo*** pueda afectar el ***Estado*** del ***Component Padre***. por medio de un ***event***.

En este mismo ejemplo, se aplica esta comunicación, mediante el paso de un ***evento*** como ***prop*** al ***component***.

En la parte del llamado del ***componente Hijo***:

~~~
<Hijo

	//(Paso del evento mediante una prop)
	incrementarContador = {this.incrementarContador}
					
	//Comunicacion de Padre a Hijo
	mensaje = "Mensaje para el hijo 1"
/>

<Hijo
	//(Paso del evento mediante una prop)
	incrementarContador = {this.incrementarContador}

	//Comunicacion de Padre a Hijo
	mensaje = "Mensaje para el hijo 2"
/>
~~~

Y en el ***Hijo***, la comunicación es al realizar el evento:

~~~
function Hijo (props) {
	return (
		<>
			<h3>
				{props.mensaje}
			</h3>
			<button
			
				//Comunicacion de Hijo a Padre, ejecutando el evento
				onClick={props.incrementarContador}>
					+
			</button>
			{console.log("Renderizando Hijo")}
		</>
	)
}
~~~

De esta manera, podemos afectar (comunicar) al padre, cambiando el ***state*** (Renderizando) del ***componente padre***.

Al activar el evento en el ***Hijo***, cambiamos el ***state*** del padre ejecutando la función, graacias a esto, se realiza una ***Comunicación***.

## Comunicación entre componentes no relacionados directamente.

Cuando queremos comunicar componentes no relacionados directamente podemos usar:

	librerias



