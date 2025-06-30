# 30. CRUD App 3.

En esta ***clase*** realizaremos la lógica para la ***edición de registros*** de nuestro ***CRUD***.

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
	const deleteData =(id) => {}

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
### Componente `CrudForm`.

La modificación del ***componente*** `CrudForm`.

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
const CrudForm = ({createData, updateData, dataToEdit, setDataToEdit}) => {

	//State
	const [form, setForm] = useState(initialForm);

	//Effect
	useEffect(() => {
		if(dataToEdit) {
			setForm(dataToEdit);
		} else {
			setForm(initialForm)
		}
	}, [dataToEdit])

	//Funciones para los eventos (vacias aun)

	//Funcion de evento onchange de input
	const handleChange =(e) => {

		//Actualizacion de state de objeto form
		setForm({
			...form,
			[e.target.name]: e.target.value,
		 });
	}

	//Funcion de evento onSubmit de form
	const handleSumit =(e) => {
		e.preventDefault();

		//Si algun atributo de state:form (se actualiza constantemente) es vacio
		if (!form.name || !form.constellation) {
			alert("Datos imcompletos");
			return;
		}

		//Si el id es null (cuando se quiere crear un registro)
		if (form.id === null) {
			//Funcion actualizadora de state de componente padre (Insertar un nuevo registro)
			createData(form);
		} else {
			//Funcion actualizadora de state de componente padre (Actualizar un registro existente)
			updateData(form);
		}

		//Ejecucion de funcion de reseteo
		handleReset();
	}

	//Funcion de evento reset de form
	const handleReset =(e) => {
		//Actualizacion de estado de form como initialForm (vacio completamente)
		setForm(initialForm);

		//Limpiar state de padre para definir si es create o insert
		setDataToEdit(null);
	}

	//Renderizado
	return (
		<div>
			<h3>{dataToEdit ? "Editar" : "Agregar"}</h3>
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

La modificación del ***componente*** `CrudTable`.

~~~jsx
import React from 'react';
import CrudTableRow from './CrudTableRow.jsx';

const CrudTable = ({data, deleteData, setDataToEdit, }) => {
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
							data.map(el => <CrudTableRow
								key={el.id}
								el={el}
								setDataToEdit={setDataToEdit}
								deleteData={deleteData}
							/>
						)
					)}
				</tbody>
			</table>
		</div>
	)
}

export default CrudTable
~~~

---
### Componente `CrudTableRow`.

La modificación del ***componente*** `CrudTableRow`.

~~~jsx
import React from 'react'

const CrudTableRow = ({el, setDataToEdit, deleteData}) => {

	let {name, constellation, id} = el;

	return (
		<tr>
			<td>{name}</td>
			<td>{constellation}</td>
			<td>
				<button onClick={() => setDataToEdit(el)}>Editar</button>
				<button onClick={() => deleteData(id)}>Eliminar</button>
			</td>
		</tr>
	);
}

export default CrudTableRow
~~~

---