# 28. CRUD App 1.

En estas ***clases*** realizaremos una pequeña ***aplicación*** para entender mejor todo el aprendizaje de todas las ***clases anteriores***.

---
### Introducción.

Para estos ***ejercicios*** necesitaremos la creación de un nuevo ***proyecto de REACT***.

***Nota:*** Elimina todos los ***estilos*** y ***componentes*** para dejar todo en blanco.

---
## Creación de componentes.

En esta ***lección*** crearemos los ***componentes*** para este ***proyecto***.

A continuación, los ***componentes*** a utilizar:

***Nota:*** El código completo se presenta, analízalo para entenderlo:

---
### App.js

Este es el ***código*** principal.

	App.js

~~~jsx
//Importacion de Componente padre de la app del crud
import CrudApp from "./components/CrudApp";

function App() {
	return (
		<>
			<h1>Ejercicios con React</h1>
				<CrudApp/>
		</>
	);
}

export default App;
~~~

***Nota:*** Este es el ***archivo*** `App.js`. Donde se importará el ***componente*** llamado `CrudApp`.

---
### Componente `CrudApp`.

Este ***componente llamado*** `CrudApp` contiene todo el ***contenido*** de la ***App CRUD***.

~~~jsx
//Importaciones utiles
import React, {useState} from 'react';
import CrudForm from './CrudForm.jsx';
import CrudTable from './CrudTable.jsx';

//Varaible objeto que simula la BD
const initialDb = [
	{
		id: 1,
		name: "Seiya",
		constellation: "Pegaso",
	},
	{
		id: 2,
		name: "Shiryu",
		constellation: "Dragón",
	},
	{
		id: 3,
		name: "Hyoga",
		constellation: "Cisne",
	},
	{
		id: 4,
		name: "Shun",
		constellation: "Andrómeda",
	},
	{
		id: 5,
		name: "Ikki",
		constellation: "Fénix",
	},
];

//Funcion de componente
const CrudApp = () => {

	//Creacion de un State para almacenar la BD
	const [db, setDb] = useState(initialDb)

	//Renderizado
	return (
		<div>
			<h2>CRUD App</h2>
			<CrudForm/>
			<CrudTable data={db}/>
		</div>
	)
}

export default CrudApp
~~~

***Nota:*** Este ***componente*** importa sus ***componentes hijos*** llamados `CrudForm` y `CrudTable`, este ultimo recibe una ***prop*** llamado `data` el cual es el ***state*** de `db`.

---
### Componente `CrudForm`.

Este ***componente llamado*** `CrudForm` contiene la ***estructura*** del ***formulario*** para el ***CRUD***.

~~~jsx
//Importaciones
import React, {useState, useEffect} from 'react'

//Variable objeto para uitilizarse en la inicialización del estado de form
const initialForm = {
	name: "",
	constellation: "",
	id: null,
}

//Funcion de componente
const CrudForm = () => {

	//States
	const [form, setForm] = useState(initialForm);

	//Funciones para los eventos (vacias aun)
	const handleChange =(e) => {}

	const handleSumit =(e) => {}

	const handleReset =(e) => {}

	//Renderizado
	return (
		<div>
			<h3>Agregar</h3>
			<form onSubmit={handleSumit}>
				<input type="text" name="name" placeholder="nombre" onChange={handleChange} value={form.name}/>
				<input type="text" name="constellation" placeholder="Constelación" onChange={handleChange} value={form.constellation}/>
				<input type="submit" value="Enviar" onClick={handleSumit}/>
				<input type="reset" value="Limpiar" onClick={handleReset}/>
			</form>
		</div>
	)
}

export default CrudForm
~~~

---
### Componente `CrudTable`.

Este ***componente llamado*** `CrudTable` contiene la ***estructura*** de la ***tabla*** para la visualización de datos de la ***db*** del ***CRUD***.

~~~jsx
//Importaciones utiles
import React from 'react';
import CrudTableRow from './CrudTableRow.jsx';

//Funcion de componente, recibiendo de props data desestrucutada
const CrudTable = ({data}) => {

	//Renderizado
	return (
		<div>
			<h3>Tabla de datos</h3>
			<table>
				<thead>
					<tr>
						<th>Nombre</th>
						<th>constelación</th>
						<th>Acciones</th>
					</tr>
				</thead>
				<tbody>
					{data.length === 0 ? (
						<tr>
							<td colSpan="3">
								Sin datos
							</td>
						</tr> ) : (
						data.map(el => <CrudTableRow key={el.id} el={el}/>)
					)}
				</tbody>
			</table>
		</div>
	)
}

export default CrudTable
~~~

***Nota:*** Este componente utiliza un ***componente hijo*** llamado `CrudTableRow`, que renderizará cada elemento nuevo en la ***table*** dependiendo de cada dato encontrado en la ***db***.

***Nota:*** Los ***componentes hijos*** `CrudTableRow` reciben de ***props*** el ***elemento*** (un objeto con los atributos `id, name, constellation`) para cada uno.

---
### Componente `CrudTableRow`.

Este ***componente*** llamado `CrudTableRow` sirve para renderizar en el ***componente*** `CrudTable` cada ***línea*** de la tabla.

~~~jsx
//Importaciones necesarias
import React from 'react'

//Funcion de componente
const CrudTableRow = ({el}) => {

	//Renderizado
	return (
		<tr>
			<td>{el.name}</td>
			<td>{el.constellation}</td>
			<td>
				<button>Editar</button>
				<button>Eliminar</button>
			</td>
		</tr>
	);
}

export default CrudTableRow
~~~

***Nota:*** El componente recibe la ***props*** `el`, el cual es un ***objeto*** que contiene los atributos `ìd, name y constellation`, de los cuales, se utilizan `name y constellation`.

---
## Conclusión.

En esta ***clase*** solamente nos limitamos a ***crear*** las interfaces y componentes, aun sin una ***programación de funcionalidad***.

