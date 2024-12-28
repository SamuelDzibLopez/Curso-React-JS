# 18. Hook useEffect 2.

En esta clase vamos a realizar ejercicios para poder entender mejor el uso de `useEffect` y las diferentes fases.
## Ejercicio 1. Reloj con Hooks.

El siguiente código es un reloj contador que puede ser ocultado o visible mediante sus 2 botones:

~~~jsx
//Importaciónes de React, useState y useEffect
import React, {useState, useEffect} from "react";

//Definicion de componente hijo
function Reloj({hora}) {
	return (
		<>
			<h3>{hora}</h3>
			{console.log("Fase de Actualizacion")}
		</>
	)
}
//Podremos ver al log de actualizacion en consola

//Definicion de componente padre
export default function RelojHook () {

	//Creacion de hook state hora
	const [hora, setHora] = useState(new Date().toLocaleTimeString());

	//Creacion de hook state visible
	const [visible, setVisible] = useState(false);

	//Funcion controladora de los eventos click de botones (recibe valor para el cambio de state de visible)
	const tictac = (valor) => setVisible(valor);

	//Definición de useEfect
	useEffect(() => {

		//Definir variable tamporizador (donde se almacena el setInterval)
		let temporizador;

		//Si el state visible es true
		if (visible) {
		
			//Definimos el continua cambio del state hora (con su funcion setHora) con un setInterval (temporizador) de cada 1 segundo
			temporizador = setInterval(() => {
				setHora(new Date().toLocaleTimeString());
			}, 1000);

		//Si el state visible no es true
		} else {
			//Limpiar el setInterval que hay en temporizador
			clearInterval(temporizador);
		}

		//Return para el desmontaje
		return() => {
			console.log("Fase de Desmontaje");
			//Limpiar el setInterval que hay en temporizador
			clearInterval(temporizador);
		}
	}, [visible]);
	//El useEffect solo se ejecuta cada que el state visivle cambie de valor

	return(
		<>
			<h2>Reloj con Hooks</h2>
			{visible && <Reloj hora={hora}/>}
			{/*Si el state visible es true renderiza el componente Reloj*/}
			{/*2 botones que tienen como evento onclick ejecutar la funcion tictac pasandole como parametro un boolean (sirve para cambiar de valor el state visible)*/}
			<button onClick={() => tictac(true)}>Iniciar</button>
			<button onClick={() => tictac(false)}>Detener</button>
		</>
	);
}
~~~

***Nota:*** La fase de desmontaje puede visualizarse en el ***return*** del `useEffect`.

---

