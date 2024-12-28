# 17. Hook useEffect.

	useEffect permite reprensetar el ciclo de vida de un componente funcional.

	- componentDidMount() (montaje)
	- componentDidUpdate() (actualización)
	- componentWillUnmount() (desmontaje)

Podemos utilizar tantos `useEffect` como necesitemos.

## Importar useEffect

Para importar el ***Hook*** de `useEffect` utilizamos la desestructuración:

~~~jsx
import React, {useState, useEffect} from "react";`
~~~

***Nota:*** El `useState` es utilizado para estado, casi siempre los 2 ***hooks*** van de la mano.

## Utilizar useEffect

El uso de `useEffect` es similar a una ***collback***

Su sintaxis en un componente:

~~~jsx
import React, {useState, useEffect} from "react";

export default function ScrollHooks() {

	useEffect(() => {
		//Aqui va codigo para la fase de montaje o actualizacion 
	});

	return(
		<>
			{/*Aqui va el codigo JSX a renderizar*/}
		</>
	)
}
~~~

## Ejemplo simple

A continuación, un código simple de uso de `useEffect`:

~~~jsx
import React, {useState, useEffect} from "react";

export default function ScrollHooks() {
	useEffect(() => {
		console.log("fase de Actualizacion");
	});
	return(
		<>
			<h2>Hooks - useEffect y ciclo de vida</h2>
		</>
	)
}
~~~

***Nota:*** Este código imprime el consola el mensaje al momento de montar y actualizar el componente.

## Ejemplo común

Un código común de un componente:

~~~ jsx
import React, {useState, useEffect} from "react";

export default function ScrollHooks() {
	//Creacion de estado
	const [scrollY, setscrollY] = useState(0)

	//Utilizacion de useEffect
	useEffect(() => {
		console.log("fase de Actualizacion");

		//Declaración de funcion para actualizar estado (no se esta ejecutando, solo se declaro)
		const detectarScroll = () => setscrollY(window.pageYOffset)

		//Asignar a la ventana del navegador en el evento "scroll" la función actualizadora detectarScroll (vanila JS)
		window.addEventListener("scroll", detectarScroll)
	});

	return(
		<>
			<h2>Hooks - useEffect y ciclo de vida</h2>
			<p>Scroll Y del navegador {scrollY} px</p>
		</>
	)
}
~~~

***Nota:*** Este componente tiene un estado llamado ***scrollY*** que se actualiza con una función actualizadora ***setscrollY*** (esta se ejecuta en la función ***detectarScroll*** que a su vez esta asignada al evento "scroll" de la ventana del navegador)
Esto renderizara en una etiqueta p, el valor del scroll.

***Nota:*** Este `useEffect` se ejecutará cada vez que se renderice o actualice el componente, si deseamos ser mas exactos, podemos aplicar una pequeña modificación (siguiente explicación.)

## Ejemplo avanzado

Existe un ***segundo parámetro*** que puede recibir el ***hook*** `useEffect`, el cual define en que parte del ciclo de vida del componente se ejecutará:

Esto se realiza con la sintaxis:

~~~jsx
import React, {useState, useEffect} from "react";

export default function ScrollHooks() {

	useEffect(() => {
		//Aqui va codigo para la fase de montaje o actualizacion 
	}, [estadoGancho]);

	return(
		<>
			{/*Aqui va el codigo JSX a renderizar*/}
		</>
	)
}
~~~

Recibiendo un ***array***, donde dentro colocaremos los ***estados*** por los cuales se ejecutaran los `useEffet`.

Como el siguiente código ejemplo

~~~jsx
import React, {useState, useEffect} from "react";

export default function ScrollHooks() {

	//Creacion de estado
	const [scrollY, setscrollY] = useState(0)
	//Utilizacion de useEffect

    useEffect(() => {
		console.log("Moviendo el scroll");
      
		//Declaración de funcion para actualizar estado (no se esta ejecutando, solo se declaro)
		const detectarScroll = () => setscrollY(window.pageYOffset)

		//Asignar a la ventana del navegador en el evento "scroll" la función actualizadora detectarScroll
		window.addEventListener("scroll", detectarScroll)
	}, [scrollY]);
	//Cada que scrollY(Es un estado) cambie de valor

	useEffect(() => {
	    console.log("Fase de Montaje");
	}, [])
	//Solo en la fase de montaje (1 vez al principio)

	useEffect(() => {
		console.log("Fase de Actualizacion");
	})
    //Cada que el componente se actualice o renderice de nuevo

	return(
		<>
			<h2>Hooks - useEffect y ciclo de vida</h2>
			<p>Scroll Y del navegador {scrollY} px</p>
		</>
	)
}
~~~

Para entender esto tiene un pequeño `Cheat-sheet`.

	 - Cuando se define el Array y un valor dentro.

~~~jsx
	useEffect(() => {
	console.log("Esto se ejecutará cuando "estadoGancho" cambie su valor");
	}, [estadoGancho]);
~~~

***Nota:*** Al definir el ***array*** con estados dentro, el `useEffect` solo se ejecutará cada que esta variable se modifique/sobrescriba (aunque su valor modificado sea el mismo).

	- Cuando se define el Array, pero sin un valor dentro.

~~~jsx
	useEffect(() => {
	    console.log("Esto se ejecutará SOLAMENTE 1 ve, en la fase de Montaje");
	}, [])
~~~

***Nota:*** Al definir el ***array*** sin estados dentro, el `useEffect` se ejecutará solo una vez, en la fase de montaje.

	- Cuando no se define el Array.

~~~jsx
	useEffect(() => {
	    console.log("Esto se ejecutará cada que se monte o actualice el componente");
	})
~~~

***Nota:*** Al no definir el ***array***, el `useEffect` se ejecutará cada que este se renderice o actualice el componente

	- Cuando el useEffect tenga un return con una funcion (Tenga o no definido el Array).

~~~jsx
	useEffect(() => {
	//Codigo de logica
		return () => {
			console.log("fase de Desmontaje");
		}
	});
//Cuando que el componente se desmonte
~~~

***Nota:*** Cuando un `useEffect` tiene un `return` con una función, lo que se encuentre dentro de la función, se ejecutará al momento del ***Desmontaje***.

