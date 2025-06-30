# 30. CRUD App 4.

En esta ***clase*** realizaremos la lógica para la ***eliminación de registros*** de nuestro ***CRUD***, así como ***agregado*** de ***estilos CSS***.

---
## Modificaciones de archivos.

A continuación, los archivos y su contenido modificado.

Intenta comprender la lógica:

---
### Componente `CrudApp`.

La modificación del ***componente*** `CrudApp`.

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
	const [db, setDb] = useState(initialDb);

	//Creacion de un State para evaluar insert o update
	const [dataToEdit, setDataToEdit] = useState(null);

	//Funciones para acciones CRUD

	//Insercion de nuevo registro
	const createData =(data) => {
 
		//Numero "pseudo-aleatorio" con base al tiempo
		data.id = Date.now();

		//Visualizable al enviar el formulario (Es el objeto que se recibe al ejecutar la funcion que ingresará un nuevo registro a nuestra BD)
		console.log(data);
      
		//Insercion de nuevo registro a la db
		setDb([...db, data]);
	}

	//Actualizacion de registro existente
	const updateData =(data) => {
		//Recorrido con map para encontrar registro coincidente y actualizar bd
		let newData = db.map(el => el.id === data.id ? data : el);

		//Actualizacion de state db con funcion actualizadora
		setDb(newData);
	}

	//Eliminacion de registro existente
	const deleteData =(id) => {
		//Confirmacion
		let isDelet = window.confirm(`¿Seguro quieres eliminar el registro con id: ${id}`);

		//Control de opcion de confirmacion
		if (isDelet) {
			let newData =  db.filter(el => el.id !== id);
			setDb(newData);
		} else {
			return;
		}
	}

	//Renderizado
	return (
		<div>
			<h2>CRUD App</h2>
			<CrudForm
				createData={createData}
				updateData={updateData}
				dataToEdit={dataToEdit}
				setDataToEdit={setDataToEdit}
			/>

			<CrudTable
				data={db}
				deleteData={deleteData}
				setDataToEdit={setDataToEdit}
			/>
		</div>
	)
}

export default CrudApp;
~~~

---
## Estilos CSS.

Para los ***estilos CSS*** agregaremos:

~~~css
html {
	box-sizing: border-box;
	font-size: 16px;
	font-family: sans-serif;
}

*,
*:after,
*::before {
	box-sizing: border-box;
}

input[type="text"] {
	border: thin solid #dedede;
	border-radius: 0.25rem;
	margin-bottom: 1rem;
	outline: none;
	display: block;
	width: 100%;
	font-size: 1rem;
	line-height: 1;
	background-color: transparent;
}

button, input[type="submit"], input[type="reset"] {
	border: thin solid #444;
	border-radius: 0.25rem;
	padding: 0.5rem 1rem;
	margin: 0 0.5rem 0 0;
	display: inline-block;
	background-color: #eee;
	color: #444;
	font-weight: bold;
	font-size: 1rem;
	line-height: 1;
	text-transform: none;
	text-decoration: none;
	text-align: center;
	vertical-align: middle;
	cursor: pointer;
}

form {
	margin-bottom: 1rem;
}

hr {
	margin: 2rem auto;
}

table {
	border-spacing: 0;
	border-collapse: collapse;
	width: 100%;
}

th, td {
	text-align: left;
	padding: 0.5rem;
	border-bottom: thin solid #dedede;
}
~~~

***Nota:*** Puedes agregar los estilos ***CSS*** desde el archivo `index.css`, el cual se encuentra enlazado desde el `index.html`.

