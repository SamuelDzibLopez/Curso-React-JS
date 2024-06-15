# 5. Props.

### Creación de las propiedades.

Una propiedad es un valor o dato que un ***componente***, para ser utilizado dentro de este.
Las propiedades nos ayudan a poder reutilizar de mayor manera nuestros componentes, creando de esta manera "cajas vacías" a ser llenadas por propiedades a como deseemos.

### Declaración de las propiedades.

Las propiedades a enviar a un componente se declaran al momento de usar un componente.
Se definen dentro de la ***etiqueta JSX*** del ***componente***.

***Nota:***
Las ***props*** se agregar de manera similar al de agregar ***atributos a etiquetas HTML*** comunes.

De la siguiente manera:

~~~
<Componente
	msg = "¡Hola!, Soy un componente de clase."
/>
~~~

O bien, podría verse también así:

~~~
<Componente msg = "¡Hola!, Soy un componente de clase." />
~~~

### Recibir propiedades en los componentes

Al enviar propiedades, el componente debe ser capaz de recibirlas, para ello, debemos escribir en el componente (en la función o en la clase).

Un ejemplo:

~~~
import React from "react";

export default function Propiedades (props) {
    return (
        <div>
            <h2>
                {props}
            </h2>
        </div>
    );
}
~~~

Donde en los parámetros a recibir en la función del componente tenemos las propiedades (props).

### Propiedades por default

Podemos asignar ***propiedades por default*** a nuestros componentes, para que si estos no reciben parámetros, se les asignen los definidos.

Para ello, agregamos a nuestro ***componente*** un código, quedando de la siguiente manera:

~~~
import React from "react";

export default function Propiedades (props) {
	return (
		<div>
			<h2>
				{props.porDefecto}
			</h2>
		</div>
	);
}

Propiedades.defaultProps = {
	porDefecto: "Las Props",
}
~~~


En el ejemplo anterior, se manda un ***objeto*** con una propiedad llamada ***porDefecto*** la cual se imprime el el h2 del componente.

### Tipos de datos en las propiedades

#### Strings, numbers y booleans 

Podemos enviar ***diferentes tipos de datos*** en las ***propiedades*** para ser utilizado en un componente, tal como se envían al siguiente componente.

~~~
<Propiedades
	cadena="Cadena" 
	Numero = {19} 
	boolean = {true} 
/>
~~~

Para propiedades que no sean de tipo ***cadena***, se utilizan los { }, para el contenido.

Quedando en el componente, de la siguiente manera.

~~~
import React from "react";

export default function Propiedades (props) {
	return (
		<div>
			<h2>
				{props.porDefecto}
			</h2>
			<ul>
				<li>
					{props.cadena}
				</li>
				<li>
					{props.numero}
				</li>
				<li>
					{props.boolean}
				</li>
			</ul>
		</div>
	);
}
  
Propiedades.defaultProps = {
	porDefecto: "Las Props",
}
~~~

***Nota:***
El tipo de dato ***boolean*** no se visualiza como un texto, este puede servir para una condición a realizar o un ***operador ternario***.

Si queremos imprimir dato con el ***boolean***, podemos hacer algo asi

~~~
<li>
	{props.boolean ? "Verdadero" : "Falso"}
</li>
~~~

De esta manera, si el ***props.boolean*** es ***true***, se imprime **"Verdadero"**, si no, se imprime **"Falso"**.

#### Arrays, objets, REACT elements, functions y REACT components

También podemos pasar datos mas complejos, tales como ***arrays***.

Para ello, la sintaxis es la siguiente:

~~~
<Propiedades
	cadena="Cadena"
	numero = {19}
	boolean = {true}
	 arreglo = {[1,2,3]}
/>
~~~

Recibiendo, dentro del componente de la siguiente manera:

~~~
<li>
	{props.arreglo}
</li>
~~~

Imprimiendo, de esta manera, el ***array***.

***Nota:*** El siguiente ejemplo, imprime todos los elementos del ***array*** juntos y seguidos, (en el ejemplo: 123), si queremos imprimir un arrat, de mejor manera, podemos usar el método **.join()**.

~~~
<li>
	{props.arreglo.join(", ")}
</li>
~~~

También, podemos enviar y recibir un objeto.

~~~
<Propiedades
	cadena="Cadena"
	numero = {19}
	boolean = {true}
	arreglo = {[1,2,3]}
	objeto = {{nombre:"Roberto", correo: "Roberto@gmail.com"}}
 />
~~~

Pero, la manera de recibirlo en el componente, es por atributo.

~~~
<li>
	{props.objeto.nombre}
</li>
~~~

También, un **componente** puede recibir un ***elemento de REACT:***

~~~
<Propiedades
	cadena="Cadena"
	numero = {19}
	boolean = {true}
	arreglo = {[1,2,3]}
	objeto = {{nombre:"Roberto", correo: "Roberto@gmail.com"}}
	elementoReact = {<i>Esto es un elemento de REACT</i>}
/>
~~~

Y recibirlo:

~~~
<li>
	{props.elementoReact}
</li>
~~~

***Nota:*** Un **Elemento REACT NO** es un elemento HTML, sino que utiliza ***JSX***.

también podemos recibir funciones como propiedades:

~~~
<Propiedades
	cadena="Cadena"
	numero = {19}
	boolean = {true}
	arreglo = {[1,2,3]}
	objeto = {{nombre:"Roberto", correo: "Roberto@gmail.com"}}
	elementoReact = {<i>Esto es un elemento de REACT</i>}
	funcion = {(num) => num * num}
/>
~~~

Donde, dentro del componente, podemos usarla.

~~~
<li>
	{props.arreglo.map(props.funcion)}
</li>
~~~

Y por ultimo, podemos recibir incluso otro ***componente de REACT:***

~~~
<Propiedades
	cadena="Cadena"
	numero = {19}
	boolean = {true}
	arreglo = {[1,2,3]}
	objeto = {{nombre:"Roberto", correo: "Roberto@gmail.com"}}
	elementoReact = {<i>Esto es un elemento de REACT</i>}
	funcion = {(num) => num * num}
	componenteReact = {<Componente msg = "Soy un componente pasado como prop"/>}
/>
~~~

Para utilizar dentro:

~~~
<li>
	{props.componenteReact}
</li>
~~~
## Manejo de inicialización de props y requerid

Primero debemos ejecutar el comando en nuestro proyecto:

~~~
npm i -S prop-types
~~~

Descargando la librería de REACT para las **props**.

***Nota:*** Para mayor información, podemos consultar la información en **npm:**

~~~
[prop-types - npm (npmjs.com)](https://www.npmjs.com/package/prop-types)
~~~

Ya una vez, descargada la dependencia, podemos hacer uso de ella, para ello, importamos en nuestro documento a usar.

~~~
import PropTypes from "prop-types";
~~~

Y debajo de nuestra función de **componente**, colocamos las reglas:

~~~
Propiedades.propTypes = {
    numero: PropTypes.number,
}
~~~

Donde, definimos:

	-primero el nombre del ***componente***.
	- Segundo, el ***.propTypes*** por regla.
	- y dentro de los ***{ }***:
		- El nombre de la ***prop*** y ***:***
		- el ***PropType. 
		- Y por ultimo, el tipo de dato que se espera

En total, el código completo quedaría:

~~~
import React from "react";
import PropTypes from "prop-types";

export default function Propiedades (props) {
	return (
		<div>
			<h2>
				{props.porDefecto}
			</h2>
			<ul>
				<li>
					{props.cadena}
				</li>
				<li>
					{props.numero}
				</li>
				<li>
					{props.boolean ? "Verdadero" : "Falso"}
				</li>
				<li>
					{props.arreglo.join(", ")}
				</li>
				<li>
					{props.objeto.nombre}
				</li>
				<li>
					{props.elementoReact}
				</li>
				<li>
					{props.arreglo.map(props.funcion)}
				</li>
				<li>
					{props.componenteReact}
				</li>
			</ul>
		</div>
	);
}

Propiedades.defaultProps = {
	porDefecto: "Las Props",
}

Propiedades.propTypes = {
	numero: PropTypes.number,
}
~~~

En el ejemplo anterior, esperábamos que la ***propiedad*** **numero** fuese de tipo **number**.

**SI ESTO NO SE CUMPLE, SE MOSTRARÁ UN "WARNING" EN LA CONSOLA, AUNQUE EL PROGRAMA SI COMPILARA.**

Un ejemplo mas visual:

~~~
MyComponent.propTypes = {
	optionalArray: PropTypes.array,
	optionalBigInt: PropTypes.bigint,
	optionalBool: PropTypes.bool,
	optionalFunc: PropTypes.func,
	optionalNumber: PropTypes.number,
	optionalObject: PropTypes.object,
	optionalString: PropTypes.string,
	optionalSymbol: PropTypes.symbol,
  }
~~~

***Nota:*** Se presentan los diferentes tipos de datos.

También podemos definir que una propiedad sea ***obligatoria***.

Simplemente, agregamos la propiedad.

~~~
Propiedades.propTypes = {
	numero: PropTypes.number.isRequired
}
~~~

Quedando de la siguiente manera.

**SI ESTO NO SE CUMPLE, SE MOSTRARÁ UN "WARNING" EN LA CONSOLA, AUNQUE EL PROGRAMA SI COMPILARA.**




