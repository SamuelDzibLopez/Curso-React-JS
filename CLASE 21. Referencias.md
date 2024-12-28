# 21. References.

Las referencias son la manera por la cual ***react.js*** nos permite controlar un elemento que ya ha sido cargado al ***DOM***.

	Explicación de Ejemplo:

	Supongamos que tenemos un menú tipo "Hamburguesa" (Menu para moviles) en nuestra aplicación, el cual se visualiza y cierra cada que se da click a un boton. Podriamos manejar dicha funcionalidad utilizando "States", pero no seria lo mas optimo, debido que a cada cierre y apertura del botón se realizaria un renderizado e inserción en el DOM.

	Una solución para ello, seria el uso de referencias con ayuda de REACT.

La diferencia entre ***referencias*** y ***estado*** es que esté ultimo realiza un nuevo renderizado, mientras que las ***referencias*** permiten modificar elementos del ***DOM*** sin cargar de nuevo el código de componentes.

---
## Cuando utilizar referencias

Existen uno cuantos buenos casos de uso para ***referencias***:

	- Controlar enfoques, selección de texto; o reproducción de medios.
	- Actuvas animaciones imperativas.
	- Integracion con bibliotecas DOM de terceros.

Evita utilizar ***referencias*** en cualquier cosa que pueda ser hecha declarativamente.

	Por ejemplo, en lugar de exponer métodos open() y close() en un componente Dialog para una propiedad isOpen a este en su lugar.

---
## Referencias y Vanila JS.

Las ***referencias*** en ***REACT*** vienen a ser lo que en ***vanila JS*** son los ***métodos*** nativos, tales como `getElementById` o `addEventListener`.

Pero ***REACT*** nos da las ***referencias*** para hacer de una manera más corta y entendible nuestro código, sin la necesidad de utilizar esos métodos complejos.

---
### Ejemplo utilizando Vanila JS.

Si, ***REACT*** soporta los ***métodos*** convencionales de ***JS***, por lo que podrían ser utilizados sin problema alguno, pongamos un ejemplo:

Creemos un ***menú*** básico y manipulémoslo con ***JS puro***:

~~~jsx
//Importación de libreria de react 
import React from "react";

//Funcion de conponente
export default function Referencias () {

	//Arrow function de evento onClick de boton de menu
	const handleToogleMenu = (e) => {

		//Captura de elemento nav
		const $menu = document.getElementById("menu");

		//Si el texto dentro del boton es "Menú"
		if (e.target.textContent === "Menú") {

			//Cambiar texto a "Cerrar"
			e.target.textContent = "Cerrar";

			//Visualizar nav
			$menu.style.display = "block";

		//Si no es el texto
		} else {

			//Cambiar texto a "Menú"
			e.target.textContent = "Menú";

			//Ocultar nav
			$menu.style.display = "none";
		}
	}

	//Renderizado
	return (
		<>
			<h2>Referencias</h2>
			<button id="menu-btn" onClick={handleToogleMenu}>Menú</button>
			 <nav id="menu" style={{display: "none"}}>
				<a href="#">Sección 1</a>
				<br/>
				<a href="#">Sección 2</a>
				<br/>
				<a href="#">Sección 3</a>
				<br/>
				<a href="#">Sección 4</a>
				<br/>
				<a href="#">Sección 5</a>
				<br/>
			</nav>  
		</>
	)
}
~~~

***Nota:*** Como puedes visualizar, el ***código anterior*** tiene su lógica codificada utilizando métodos puros, y aun así funciona.

Sin embargo, existe la manera de ***REACT*** y las ***referencias***.

---
### Ejemplo utilizando Referencias de REACT.

~~~jsx
//Importación de libreria de react 
import React, {useRef} from "react";

//Funcion de conponente
export default function Referencias () {

	//Creacion de referencias
	let refMenuBtn = useRef();
	let refMenu = useRef();

	//Impresion de referencias
	console.log(refMenuBtn);
	console.log(refMenu);

	//El atributo .current de una referencia contiene el elemento del DOM al que se le asigne
	console.log(refMenuBtn.current);
	console.log(refMenu.current);

	//Arrow function de evento onClick de boton
	const handleToogleMenu = (e) => {

		//Si el ,text content del elemento de refMenuBtn es "Menú"
		if (refMenuBtn.current.textContent === "Menú") {

			//Cambio de textContent utilizando referencias
			refMenuBtn.current.textContent = "Cerrar";
			refMenu.current.style.display = "block";

		//Si no
		} else {

			//Cambio de textContent utilizando referencias
			refMenuBtn.current.textContent = "Menú";
			refMenu.current.style.display = "none";
		}
	}

	//Renderizado
	return (
		<>
			<h2>Referencias</h2>
			<button ref={refMenuBtn} onClick={handleToogleMenu}>Menú</button>
			 <nav ref={refMenu} style={{display: "none"}}>
				<a href="#">Sección 1</a>
				<br/>
				<a href="#">Sección 2</a>
				<br/>
				<a href="#">Sección 3</a>
				<br/>
				<a href="#">Sección 4</a>
				<br/>
				<a href="#">Sección 5</a>
				<br/>
			</nav>  
		</>
	)
}
~~~

***Nota:*** En este ejemplo de código, con ayuda de las referencias, no necesitamos utilizar métodos como `getElementById` o `addEventListener`, mi atributo `id`, basta con crear ***referencias*** y asignarlas en el elemento ***JSX***.

---
### Observaciones de las referencias.

Algunos datos a tomar en cuenta al utilizar ***referencias***.

---
### Current y Target

`current` es similar en ***REACT***  a `target` vanila JS.

	- current representa el elemento HTML (JSX) del DOM asignado a la referencia.
	- target representa el elemento HTML (en JS puro) que ejecuta el evento (e).
	- e o event es el objeto con información del evento ejecutado.

---
### useRef.

Cuando queremos utilizar ***referencias*** en ***componentes funcionales*** utilizamos el ***Hook*** `useRef`:

~~~ jsx
//Importación de useRef
import React, {useRef} from "react";
~~~

~~~jsx
//Creacion de referencia y asignación a variable
let refMenuBtn = useRef();
~~~

~~~jsx
//Asignacion de ref a elemento JSX
<button ref={refMenuBtn} onClick={handleToogleMenu}>Menú</button>
~~~

---
### CreateRef.

Sin embargo, cuando queremos utilizar ***referencias*** en ***componentes de clase*** utilizamos ``createRef`:

~~~ jsx
//Importación de createRef
import React, {createRef} from "react";
~~~

~~~jsx
//Creacion de referencia y asignación a variable
let refMenuBtn = createRef();
~~~

~~~jsx
//Asignacion de ref a elemento JSX
<button ref={refMenuBtn} onClick={handleToogleMenu}>Menú</button>
~~~

---
### Referencias de valores.

Las ***referencias*** no solo tienen que guardar elementos ***JSX*** también pueden servir para guardar valores:

~~~jsx
import { useRef } from 'react';

export default function Counter() {
	let ref = useRef(0);

	function handleClick() {
		ref.current = ref.current + 1;
		alert('¡Hiciste clic ' + ref.current + ' veces!');
	}

	return (
		<button onClick={handleClick}>
			¡Hazme clic!
		</button>
	);
}
~~~

---
### Documentación.

Enlace a la documentación de ***REACT***:

	https://es.react.dev/learn/escape-hatches