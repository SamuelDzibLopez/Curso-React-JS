
# 7. Conditional Rendering

En muchas ocasiones, nuestra APP, deberá cambiar el ***estado*** y con ello renderizar diferentes **componentes**.

Para ello, tenemos el ***Renderizado Condicional***.

Con ayuda de un operador ternario, podemos renderizar un componente u otro.

Un ejemplo:

Tenemos este componente ***padre***.

***Nota:*** No olvidemos el ***import de Component de REACT***.

~~~
export default class RenderizadoCondicional extends Component {
	render() {
		return (
			<div>
				<h2>
					Renderizado Condicional
				</h2>
				
				<Login/>
				<Logout/>
				
			</div>
		)
	}
}
~~~

Que a su vez, **renderiza 2 elementos hijos**, los cuales son:

Login.

~~~
function Login () {
	return (
		<div>
			<h3>
				Login
			</h3>
		</div>
	);
}
~~~

Y Logout.

~~~
function Logout () {
	return (
		<div>
			<h3>
				Logout
			</h3>
		</div>
	);
}
~~~

Ambos, simplemente renderizan contenido JSX.

Pero, si quiero renderizar solo uno de ellos a la vez, podemos resolverlo, utilizando una condición.

Cambiando el **componente padre*** de la siguiente forma:

~~~
export default class RenderizadoCondicional extends Component {
	//Creacion del constructor
	constructor (props) {
		super (props);
		this.state = {
			session: true,
		}
	}
	
	render() {
		return (
			<div>
				<h2>
					Renderizado Condicional
				</h2>
				
				{/*Operador terminario*/}
				{this.state.session ? <Login/> : <Logout/>}
				
			</div>
		)
	}
}
~~~

El siguiente cambio crea una ***prop*** ***state***, donde **session** es un atributo de valor **boolean**.

Dentro de nuestro ***render*** y ***return*** utilizamos un ***operador terminario***; si ***this.state.session*** es igual a ***true***, entonces renderiza ***Login***, si no, renderiza ***Logout***.