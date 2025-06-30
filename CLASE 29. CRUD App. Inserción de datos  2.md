# 29. CRUD App 2.

En esta ***clase*** modificaremos y agregaremos funcionalidad a nuestro ***proyecto***, para que esta tenga la funcionalidad de ***inserción*** de datos y registros nuevos-

	Accion: CREATE.

---

Para esta ***clase*** modificaremos ***2 archivos*** de ***componentes***:

	- CrudApp.
	- initialForm.

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
	const updateData =(data) => {}

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
			<h3>Agregar</h3>
			<form onSubmit={handleSumit}>
				<input 
					type="text" 
					name="name" 
					placeholder="nombre" 
					onChange={handleChange} 
					value={form.name}
				/>
				<input 
					type="text" 
					name="constellation" 
					placeholder="Constelación" 
					onChange={handleChange} 
					value={form.constellation}
				/>
				<input
					type="submit" 
					value="Enviar" 
					onClick={handleSumit}
				/>
				<input 
					type="reset" 
					value="Limpiar" 
					onClick={handleReset}
				/>
			</form>
		</div>
	)
}

export default CrudForm
~~~

---
## Otros componentes.

Los otros ***componentes*** y ***archivos*** siguen igual, sin modificaciones.

---
## Conclusión.

En esta ***lección*** se lograron ***fortalecer*** temas tales como:

	- Logica de renderizado de "padres a hijos" e "hijos a padres". (Con props y states).
	- Envio de props entre componentes (funciones comunes y funciones actualizadoras de states).
	- Logica de actualizaciones de states de hijos a padres.
	- Temas de JS (Spread operator y otros temas).