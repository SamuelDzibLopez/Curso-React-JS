# 22. Forms.

Los ***formularios*** son una parte esencial de los sitios y aplicaciones.

En ***React*** se le conocen a los formularios por ***2 diferentes*** formas de controlarse:

	- Formularios controlados: Formularios que son gestionados por el State de un componente.
	- Formularios no controlados: Formularios con inputs gestionados de manera independiente, ya sea con id´s o referencias.

Utilizar ***formularios no controlados*** es similar a ***vanila JS***.

---
A continuación, se explican ejemplos de diferentes campos de texto útiles en ***formularios***, así como su utilización en ***REACT***.

---
## Inputs text.

Los ***inputs*** de tipo ***texto*** (sean ***text***, ***number***, ***mail***, etc.) son los campos mas utilizados.

Un ejemplo de un ***componente***, el cual contiene un ***formulario*** con un ***input*** de tipo ***text***.

~~~jsx
//Importacion de libreria React y hook useState
import React, {useState} from "react";

//Funcion de componente 
export default function Formularios () {

	//Creacion de state nombre, para el estado del valor del input text
	const [nombre, setNombre] = useState("");

	//Impresion en consola de state nombre
	console.log(nombre);

	//Renderizado
	return (
		<>
			<h2>Formularios</h2>
			<form>
				<label htmlFor="nombre">
					Nombre
				</label>

				<input
					type="text"
					id="nombre"
					name="nombre"
					value={nombre}
					onChange={(e) => setNombre(e.target.value)}
				/>
				<button>Enviar</button>
			</form>
		</>
	)
}
~~~

***Nota:*** Este ***formulario controlado*** permite actualizar el valor del estado llamado ***nombre***, tomando el valor dentro del ***input*** cada vez que se ejecuta la función del evento ***onChange***.

---
## inputs radio.

Otro de los ***campos*** más importantes en los formularios son los ***inputs*** de tipo ***radio***.

A continuación, se presenta un ejemplo de como ***REACT*** permite utilizar este tipo de ***inputs***:

~~~jsx
//Importación de libreria de react y hook useState
import React, {useState} from "react";

//Funcion de componente
export default function Formularios () {

	//Creacion de state sabor, para el estado del valor del radio seleccionado
	const [sabor, setSabor] = useState("");

	//impresion en consola de state sabor
	console.log(sabor);

	//Renderizado
	return (
		<>
			<h2>Formularios</h2>

			<form>
				<p>Elige tu Sabor JS Favorito</p>

				<input
					type="radio"
					id="vanila"
					name="sabor"
					value="vanilla"
					onChange={e => setSabor(e.target.value)}
				/>
				<label htmlFor="vanila">Vanilla</label>

				<input
					type="radio"
					id="react"
					name="sabor"
					value="react"
					onChange={e => setSabor(e.target.value)}
				/>
				<label htmlFor="react">React</label>

				<input
					type="radio"
					id="vue"
					name="sabor"
					value="vue"
					onChange={e => setSabor(e.target.value)}
				/>
				<label htmlFor="vue">Vue</label>

				<button>Enviar</button>
			</form>
		</>
	)
}
~~~

***Nota:*** Este ***formulario controlado*** permite actualizar el valor del estado llamado ***sabor***, tomando el valor asignado cuando se selecciona un ***radio*** ejecutando la función del evento ***onChange***.

---
## Select.

Los ***campos*** de estilo ***select*** y ***options*** son otro tipo de etiquetas muy comunes entre los ***formularios***.

A continuación, un ejemplo de elementos ***select*** en ***REACT***:

~~~jsx
//Importacion de libreria react y hook useState
import React, {useState} from "react";

//Funcion de componente
export default function Formularios () {

	//Creacion de state lenguaje para el estado del valor del option seleccionado  del select 
    const [lenguaje, setLenguaje] = useState("");

	//Impresion de state lenguaje
    console.log(lenguaje);

	//Renderizado
    return (
        <>
            <h2>Formularios</h2>

            <form>

                <p>Elige tu lenguaje de programación favorito</p>

                <select name="lenguaje" onChange={(e) => setLenguaje(e.target.value)}>
                    <option value="">---</option>
                    <option value="js">JavaScript</option>
                    <option value="php">PHP</option>
                    <option value="go">GO</option>
                    <option value="python">Python</option>
                </select>

                <button>Enviar</button>

            </form>
        </>
    )
}
~~~

***Nota:*** Este ***formulario controlado*** permite actualizar el valor del estado llamado ***lenguaje***, tomando el valor asignado cuando se selecciona un ***option*** del ***select*** ejecutando la función del evento ***onChange***.

---
## Checkbox.

A diferencia de los ***inputs*** y los ***radio***, los inputs de tipo ***checkbox*** son diferentes, debido a su atributo ***true/false***.

~~~jsx
//Importacion de libreria react y hook useState
import React, {useState} from "react";

//Funcion de componente
export default function Formularios () {

	//Creacion de state terminos para el estado del valor del checkbox (false por default) 
    const [terminos, setTerminos] = useState(false);

	//Impresion en consola de state terminos
    console.log(terminos);

	//Renderizado
    return (
        <>
            <h2>Formularios</h2>

            <form>
                <label htmlFor="terminos">Acepto términos y condiciones</label>

                <input
                    type="checkbox"
                    id="terminos"
                    name="terminos"
                    onChange={(e) => setTerminos(e.target.checked)}
                />

                <button>Enviar</button>
            </form>
        </>
    )
}
~~~

---
## Envío de formulario.

Ahora, para poder realizar en evento ***onSubmit*** en un formulario de ***REACT*** realizamos la siguiente manera, como el ejemplo:

~~~jsx
//Importacion de libreria react y hook useState
import React, {useState} from "react";

//Funcion componente
export default function Formularios () {

	//Creacion de state nombre, para el estado del valor del input text
	const [nombre, setNombre] = useState("");

	//Impresion de state nombre
	console.log(nombre);

	//Arrow funcion para evento onSubmit de form
	const handleSubmit = e => {

		//Eliminacion de funcionamiento default de evento
		e.preventDefault();

		//Despliegue de alert con uso de state
		alert(`Formulario enviado: ${nombre}`);

	}

	//Renderizado
	return (
		<>
			<h2>Formularios</h2>

			<form onSubmit={handleSubmit}>
				<label htmlFor="nombre">
					Nombre
				</label>

				<input
					type="text"
					id="nombre"
					name="nombre"
					value={nombre}
					onChange={(e) => setNombre(e.target.value)}
				/>

				<button>Enviar</button>
			</form>
		</>
	)
}
~~~

***Nota:*** la etiqueta `form` tiene un evento ***onSubmit*** que ejecuta la función `handleSubmit`. 

---
## Formularios complejos

Imaginemos que tenemos un ***formulario*** mucho mas grande, por lo que, en lugar de tener una variable de ***state*** por cada ***valor*** de ***input***, podemos optimizar nuestra lógica, un ejemplo:

~~~jsx
//Importacion de libreria de React y hook useState
import React, {useState} from "react";

//Funcion de componente
export default function Formularios () {

	//Creacion de state form, definido como un objeto, donde se guardaran los valores de los inputs en atributos y valores 
	const [form, setForm] = useState({});

	//Funcion para el evento onChange de los inputs 
	const handleChange = e => {
		//Actualizar state con spread operator
		setForm({
			...form,
			[e.target.name]: e.target.value,
		});
	}

	//Funcion para el evento onChange de el checkbox 
	const handleChecked = e => {
		//Actualizar state con spread operator
		setForm({
			...form,
			[e.target.name]: e.target.checked,
		});
	}

	//Funcion para el evento onSubmit de form
	const handleSubmit = e => {
		e.preventDefault();
		alert("El formulario se envio");
	}

	//Impresion de state form
    console.log(form);

	//Renderizado
	return (
		<>
			<h2>Formularios</h2>

			<form onSubmit={handleSubmit}>
				<label htmlFor="nombre">
					Nombre
				</label>

				<input
					type="text"
					id="nombre"
					name="nombre"
					value={form.nombre}
					onChange={handleChange}
				/>

				<p>Elige tu Sabor JS Favorito</p>

				<input
					type="radio"
					id="vanila"
					name="sabor"
					value="vanilla"
					onChange={handleChange}
				/>
				<label htmlFor="vanila">Vanilla</label>

				<input
					type="radio"
					id="react"
					name="sabor"
					value="react"
					onChange={handleChange}
				/>
				<label htmlFor="react">React</label>

				<input
					type="radio"
					id="vue"
					name="sabor"
					value="vue"
					onChange={handleChange}
				/>
				<label htmlFor="vue">Vue</label>

				<p>Elige tu lenguaje de programación favorito</p>

				<select name="lenguaje" onChange={handleChange}>
					<option value="">---</option>
					<option value="js">JavaScript</option>
					<option value="php">PHP</option>
					<option value="go">GO</option>
					<option value="python">Python</option>
				</select>

				<label htmlFor="terminos">Acepto términos y condiciones</label>

				<input
					type="checkbox"
					id="terminos"
					name="terminos"
					onChange={handleChecked}
				/>

				<button>Enviar</button>
			</form>
		</>
	)
}
~~~

***Nota:*** Las funciones `handleChange` y `handleChecked` se asignan a cada evento ***onChange*** de los ***inputs***, permitiendo ingresar al ***state*** `form` los valores como ***atributos*** y ***valores***, con ayuda del `spread operator`.


