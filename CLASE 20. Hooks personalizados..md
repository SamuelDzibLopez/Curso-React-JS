# 20. Customs Hooks.

	https://react.dev/learn/reusing-logic-with-custom-hooks#custom-hooks-sharing-logic-between-components

Una de las cosas que nos permite la ***librería*** de ***react.js*** es poder realizar nuestros propios ***hooks***.
## Ubicación de hooks personalizados.

Por lo general, al crear ***hooks*** se suele crear en la estructura básica del proyecto (dentro del directorio ***src***) un nuevo directorio llamado ***hooks***.

~~~
my-app/
  README.md
  node_modules/
  package.json
  public/
    index.html
    favicon.ico
  src/
    App.css
    App.js
    App.test.js
    index.css
    index.js
    logo.svg
    hooks/
~~~

## Nombramiento de hooks personalizados.

Así también, los ***hooks personalizados*** suelen llamarse por nombre:

	- Son escritos utilizando el formato lowerCamelCase.
	- inician con la palabra "use" (en minuscula).
	- son extensión .js.

Como el ejemplo:

~~~
useFetch.js
~~~

---
## Ejemplo de hook personalizado.

Para el siguiente ***ejemplo*** tendremos ***2 archivos***, uno será el ***componente*** y otro el ***archivo custom hook***.

El ejemplo será crear un ***custom hook*** a utilizar en un ***component***, para poder hacer una ***petición fetch***.

Crearemos un ***componente*** llamado:

```
CustomHooks.jsx
```

Y un ***Custom Hook*** llamado:

```
useFetch.js
```

***Nota:*** No olvides importar el ***component*** en el ***App.js***.

---
### Componente.

El ***componente*** importa el ***Custom Hook*** llamado `useFetch` de `"../hooks/useFetch.js"`.

~~~jsx
//Importación de libreria de REACT
import React from "react";

//Importacion de "Custom Hook" creado
import { useFetch } from "../hooks/useFetch.js";

//Componente
export default function CustomHooks () {

	//Definicion de URL para fetch
	let url = "https://pokeapi.co/api/v2/pokemon/";

	//Ejecución de "Custom Hook" enviando la url como parametro
	let {data, isPending, error} = useFetch(url);
	//utilización de desestructuración para obtener los datos return del fetch

	//Parte a renderizar
	return (
		<>
			<h2>Hooks Personalizados</h2>

			<h3>{JSON.stringify(isPending)}</h3>
			<h3>
				<mark>
					{JSON.stringify(error)}
				</mark>
			</h3>
			<h3>
				<pre style={{whiteSpace: "pre-wrap"}}>
					<code>
						{JSON.stringify(data)}
					</code>
				</pre>
			</h3>
		</>
	)
}
~~~

### Custom Hook.

El ***Custom Hook*** recibe un parámetro definido como ***url*** para realizar el ***fetch***, retornando un objeto al ***componente*** que tiene los `states` de `data, isPending, error`.

~~~jsx
//Importacion de hooks base useState y useEffect para Custom Hook
import {useState, useEffect} from "react";

//Funcion de hook recibiendo de parametro la url para fetch
export const useFetch = (url) => {

	//Definición de states con useState

	//Estado para recibir los datos
	const [data, setData] = useState(null)

	//Estado para identificar estado de fetch (pendiente o listo)
	const [isPending, setIsPending] = useState(true)

	//Estado para recibir errores
	const [error, setError] = useState(null)

	//useEffect para petición fetch
	useEffect(() => {

		//Funcion async getData para ejecutar el fetch, recibiendo de parametro url
		const getData = async (url) => {

			//funcion try
			try {

				//Peticion fetch
				let res = await fetch(url);

				//Si res.ok es false
				if (!res.ok) {

					//Creacion de error y envio de objeto y atributos para el catch
					throw {
						err:true,
						status:res.status,
						statusText: !res.statusText ? "Ocurrio un error" : res.statusText,
					}
				}

				//Conversion de respuesta a JSON
				let data = await res.json();

				//uso de hooks para cambiar states
				setIsPending(false);
				setData(data);
				setError({err:false});

			//funcion catch para errores
			} catch (err) {

				//uso de hooks para cambiar states
				setIsPending(true);
				setError(err);
			}
		};

		//Ejecución de funcion getData y envio de parametro
		getData(url);

	}, [url]);

	//Finalmente el Custom Hook retorna un objeto con atributos: data, isPending, error (que son los valores de los states)
	return {data, isPending, error}
}
~~~

---
### Aplicación de Custom Hook.

Intenta crear otro componente igual al anterior, pero cambiando de ***url*** a:

~~~
let url = "https://jsonplaceholder.typicode.com/users";
~~~

***Nota:*** Esta es una ***url*** a  otra ***API***, sin embargo, debería funcionar independientemente de esto.

Esto significa que crear un ***custom hook*** permite reutilizar código (con `useState y useEffect`) para ***componentes***.