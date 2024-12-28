# 16. Hook useState.

Gracias a la implementación de los ***hooks***, los componentes funcionales pueden tener una lógica de programación

	useState permite hacer uso del estado.

## Importar useState

La manera de importar `useState` es de la siguiente manera.

~~~jsx
import React, { useState } from "react";
~~~

***Nota:*** Utilizando la desestructuración en la librería de ***React***.

## Utilizar useState

Para hacer uso de `useState`:

~~~jsx
const [valor, setValor] =useState(0);
~~~

***Nota:*** Se utiliza la ***desestructuración de arreglos***.

`useState` utiliza 2 ***parametros***, el ***valor*** (o variable de estado) y la ***función*** para actualizarse.

	Cada estado (variable) tiene su propia funcion actualizadora.
	Por convencion se suele llamar a la funcion actualizado como set(valor o estado).

## Ejemplo simple:

Un ejemplo simple de un ***componente funcional*** utilizando `useState`.

~~~jsx
import React, {useState} from "react";

export default function Componente() {
	const [valor, setValor] = useState(0);
	return(
		<div>
		<span>el valor del componente es {valor}</span>
			<button onClick={() => setValor(valor +1)}>Aumentar valor</button>
		</div>
	)
}
~~~

***Nota:*** Este componente tiene un ***estado*** llamado ***valor*** inicializado en 0, una ***función actualizadora*** llamada ***setValor*** que al hacer *click* en el botón, su valor se actualiza en +1.

## Ejemplo común

~~~jsx
import React, {useState} from "react";

export default function ContadorHooks() {
	console.log(useState()); //Impresión de visualización de useState en consola (tiene 2 parametros, uno primitivo y otro es una funcion)

	const [contador, setContador] = useState(0);

	const sumar = () => setContador(contador+1);
	const restar = () => setContador(contador-1);

	return(
		<>
			<h2>Hooks - Use estate</h2>
			<nav>
				<button onClick={sumar}>+</button>
				<button onClick={restar}>-</button>
			</nav>
			<h3>{contador}</h3>
		</>
	)
}
~~~

***Nota:*** Este es un contador simple.

También podemos definir las ***funciones actualizadoras***, se recomienda hacerlas en formato de ***arrow functions***.

---

`useState` permite hacer nuestro código mas entendible, menos complejo y mas corto.

