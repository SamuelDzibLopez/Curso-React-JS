# 24. Styled Components.

	https://styled-components.com/

La ***librería*** de ***Styled components*** permite poder ingresar estilizado ***CSS*** a nuestros componentes. permitiendo utilizar una manera diferentes la integración de ***estilos*** en proyectos de ***REACT***.

---
## Instalación.

Para realizar la instalación se ejecuta el comando:

~~~
npm install styled-components
~~~

***Nota:*** Al terminar la ***instalación***, podremos visualizar en nuestro archivo `package.json` la versión de la instalación.

Algo similar a:

~~~
"styled-components": "^6.1.13",
~~~

De esta manera, podremos corroborar la instalación en nuestro proyecto.

***Nota:*** Si estas utilizando ***VSC*** puedes instalar también la extensión llamada `styled-components-snippets` para una mejor visualización en el código.

---
## Utilización básica.

Como se utiliza de manera simple y basica la libreria `Styled Components`.

---
### Importación:

Para utilizar la ***librería*** de `Styled Components` en nuestro ***componente***, debemos importar la librería.

~~~jsx
import styled from "styled-components";
~~~

Con este ***elemento*** podremos crear nuestros estilos para los ***elementos JSX*** renderizados.

---
### Definición de estilos:

Para crear un estilo para un ***elemento JSX***:

~~~jsx
const MyH3 = styled.h3`
	padding: 2rem;
	text-aling: center;
	background-color: #db7093;
	transition: all .5s ease-out;

	&:hover {
		background-color: #db709380;
	}
`;
~~~

***Nota:*** Se crea una ***variable*** llamada `MyH3` que contiene los estilos ***CSS*** definidos, con ayuda de  `styled`, el cual se renderizará como un `<h3></h3>`.

`&:hover` Permite definir la ***pseudo-clase*** `hover`.

---
### Definición de elementos: 

Y en el ***return*** debería colocarse un ***elemento*** como el siguiente:

~~~jsx
<MyH3>Hola soy un h3 estilizado con Styled Components</MyH3>
~~~

***Nota:*** Como en la definición de ***estilos*** fue definido como un `<h3></h3>` al renderizarse, el `<MyH3>` permitirá obtener todos lo ***atributos CSS*** definidos en la ***variable*** `const MyH3`.

---
### Ejemplo de código completo.

A continuación, el ***código completo*** del ***ejemplo*** explicado:

~~~jsx
//importacion de libreria react
import React from "react";

//Importacion de libreria styled-components
import styled from "styled-components";

//Funcion de componente
export default function ComponentesEstilizados () {

	//Definicion de variable MyH3 para crear H3s y definiendo sus estilos CSS
	const MyH3 = styled.h3`
		padding: 2rem;
		text-aling: center;
		background-color: #db7093;
		transition: all .5s ease-out;

		&:hover {
			background-color: #db709380;
		}
	`;

	//Renderizado
	return (
		<>
			<h2>Styled Components</h2>

			<MyH3>Hola soy un h3 estilizado con Styled Components</MyH3>
		</>
	)
}
~~~

---
## `Styled Components` con variables, funciones y props.

Debido a que ***Styled Components*** es en sí, codificado en ***JS***, podemos utilizar ***variables***, ***funciones*** y ***props***, veamos como:

---
### `Styled Components` con variables.

Para utilizar variables en los ***estilos*** podemos realizar la siguiente manera:

~~~jsx
//importacion de libreria react
import React from "react";

//importacion de libreria Styled-Components
import styled from "styled-components";

//Funcion de componente
export default function ComponentesEstilizados () {

	//Variables a utilizar para estilos CSS
	let mainColor = "#db7093";
	let mainAlphaColor80 = "#db709380";

	//Definicion de variable MyH3 para crear H3s y definiendo sus estilos CSS
	const MyH3 = styled.h3`
		padding: 2rem;
		text-aling: center;
		background-color: ${mainColor};
		transition: all 0.5s ease-out;

		&:hover {
			background-color: ${mainAlphaColor80};
		}
	`;

	//Renderizado
	return (
		<>
			<h2>Styled Components</h2>

			<MyH3>Hola soy un segundo h3 estilizado con Styled Components</MyH3>
		</>
	)
}
~~~

***Nota:*** Como el los ***estilos CSS*** son definidos con ***templates strings*** en lenguaje ***JS*** podemos utilizar el formato `${}` para utilizar ***variables***.

---
### `Styled Components` con funciones.

También podemos utilizar ***funciones*** para poder ingresar ***atributos CSS***.

~~~jsx
//importacion de libreria react
import React from "react";

//importacion de libreria styled-components
import styled from "styled-components";

//Funcion de componente
export default function ComponentesEstilizados () {

	//Variables a utilizar para estilos CSS
	let mainColor = "#db7093";
	let mainAlphaColor80 = "#db709380";

	//Arrow function para devolver atributo CSS de transition, recibiendo parametro de tiempo
	const setTransitiontime = (time) => `all ${time} ease-out`;

	//Definicion de variable MyH3 para crear H3s y definiendo sus estilos CSS (llamado a funcion "setTransitiontime" con parametro)
	const MyH3 = styled.h3`
		padding: 2rem;
		text-aling: center;
		background-color: ${mainColor};
		transition: ${setTransitiontime("1s")};

		&:hover {
			background-color: ${mainAlphaColor80};
		}
	`;

	//Renderizado
	return (
		<>
			<h2>Styled Components</h2>

			<MyH3>Hola soy un segundo h3 estilizado con Styled Components</MyH3>
		</>
	)
}
~~~

***Nota:*** Recordemos que las ***arrow funtions*** devuelven contenido de forma implícita (sin necesidad del ***return***).

---
### `Styled Components` con props.

También podemos recibir y enviar ***propiedades (props)*** a los estilos ***CSS*** por medio de nuestro ***elemento JSX***.

Veamos un ejemplo:

~~~jsx
//importacion de libreria react
import React from "react";

//importacion de libreria styled-components
import styled from "styled-components";

//Funcion de componente
export default function ComponentesEstilizados () {

	//Variables para estilos CSS
	let mainColor = "#db7093";
	let mainAlphaColor80 = "#db709380";

	//Funcion para estilos CSS
	const setTransitiontime = (time) => `all ${time} ease-out`;

	//Estilos CSS con props
	//(Color) Linea 1. recibiendo props sin desescructurar.
	//(Color) Linea 2. recibiendo props desescructurando.
	//(Color) Linea 3. recibiendo props desescructurando y con operador ternario.  
	const MyH3 = styled.h3`
		padding: 2rem;
		text-aling: center;
		color: ${props => props.color};
		color: ${({color}) => color};
		color: ${({color}) => color || "#000"};
		background-color: ${mainColor};
		transition: ${setTransitiontime("1s")};

		&:hover {
			background-color: ${mainAlphaColor80};
		}
	`;

	//Renderizado (pasando props por medio de elemento JSX)
	return (
		<>
			<h2>Styled Components</h2>

			<MyH3 color="#61dafb">Hola soy un segundo h3 estilizado con Styled Components</MyH3>
		</>
	)
}
~~~

***Nota:*** Con el ***operador ternario***, permite definir que si no es enviado el atributo color, el valor por default será `#000`, ***¡INTENTA ELIMINAR EL ATRIBUTO COLOR DEL ELEMENTO!.

---
## `Styled Components` con props booleans.

Si las ***props*** que enviamos son de tipo ***boolean*** podemos realizar una condicional para utilizarse en caso de cumplirse o no.

Un ejemplo:

~~~jsx
//importacion de libreria react
import React from "react";

//importacion de libreria styled-components
import styled, {css} from "styled-components";

//Funcion de componente
export default function ComponentesEstilizados () {

	//Variables para estilos CSS
	let mainColor = "#db7093";
	let mainAlphaColor80 = "#db709380";
	const setTransitiontime = (time) => `all ${time} ease-out`;

	//Estilos CSS con props
	const MyH3 = styled.h3`
		padding: 2rem;
		text-aling: center;
		color: ${props => props.color};
		color: ${({color}) => color};
		color: ${({color}) => color || "#000"};
		background-color: ${mainColor};
		transition: ${setTransitiontime("1s")};

		${(props) => props.isButton && css`
			margin: auto;
			max-width: 50%;
			border-radius: 0.25rem;
			cursor: pointer;
		`}

		&:hover {
			background-color: ${mainAlphaColor80};
		}
	`;

	//Renderizado
	return (
		<>
			<h2>Styled Components</h2>

			<MyH3 isButton>Soy un h3 estilizado como un botón</MyH3>
		</>
	)
}
~~~

***Nota:*** Existen pequeños cambios para esto, fijémonos:
#### Importación de módulo css.

~~~jsx
//importacion de libreria styled-components
import styled, {css} from "styled-components";
~~~

	- Importación de módulo css de styled-components, util para mas adelante en la condición.
#### Condicional para atributo y estilos CSS.

~~~jsx
${(props) => props.isButton && css`
	margin: auto;
	max-width: 50%;
	border-radius: 0.25rem;
	cursor: pointer;
`}
~~~

	- Condicional para aplicar estilos CSS si el atributo es true o false (existe o no existe).
#### Envió de prop boolean.

~~~jsx
<MyH3 isButton>Soy un h3 estilizado como un botón</MyH3>
~~~

	- Envio de propiedad estilo boolean.

***Nota:*** Al igual que las propiedades comunes, si estas propiedades no son enviadas, gracias a la validación creada, no aplica los estilos.

***¡INTENTA MODIFICANDO EL ENVIO DE LA PROP BOOLEAN!***

---
## `Styled Components` con animaciones.

`Styled Components` también permite crear animaciones.
#### Importación de módulo ``keyframes``.

Para ello, debemos importar un módulo llamado `keyframes`.

~~~jsx
import styled, {css, keyframes} from "styled-components";
~~~
#### Definición de variable para `keyframe` CSS.

Para ser utilizado para crear una animación desde una variable:

~~~jsx
	const fadeIn = keyframes`
		0% {
			opacity: 0;
		}

		100% {
			opacity: 1;
		}
	`;
~~~
#### Asignación de variable a estilos CSS.

Y definirse en el estilo CSS:

~~~jsx
animation: ${fadeIn} 2s ease-out;
~~~

#### Código completo de ejemplo.

A continuación, el código completo del ejemplo:

~~~jsx
//Importacion de libreria react
import React from "react";

//importacion de modulos utiles
import styled, {css, keyframes} from "styled-components";

//Funcion de componente
export default function ComponentesEstilizados () {

	//Variable utiles para estilos
	let mainColor = "#db7093";
	let mainAlphaColor80 = "#db709380";
	const setTransitiontime = (time) => `all ${time} ease-out`;

	//Variable de keyframe (animacion)
	const fadeIn = keyframes`
		0% {
			opacity: 0;
		}

		100% {
			opacity: 1;
		}
	`;

	//Definicion de estilos CSS
	const MyH3 = styled.h3`
		padding: 2rem;
		text-aling: center;
		color: ${({color}) => color || "#000"};
		background-color: ${mainColor};
		transition: ${setTransitiontime("1s")};
		animation: ${fadeIn} 2s ease-out;

		&:hover {
			background-color: ${mainAlphaColor80};
		}
	`;

	//Renderizado
	return (
		<>
			<h2>Styled Components</h2>

			<MyH3>Hola soy un h3 estilizado con Styled Components</MyH3>
		</>
	)
}
~~~

***Nota:*** La animación se ejecuta al inicio del renderizado en el DOM del elemento.

---
## `Styled Components` con temas.

Los ***Styled Components*** también permiten crear ***estilos CSS*** a manera de temas, tales como ``dark/light``, esto mediante otro módulo llamado `ThemeProvider`. Veamos como funciona:

Utilicemos de ejemplo un nuevo componente:

~~~jsx
//Importacion de libreria react
import React from "react";

//Importacion de libreria styled component y modulos styled y ThemeProvider
import styled, {ThemeProvider} from "styled-components";

//Funcion de componente
export default function ComponentesEstilizados () {

	//objeto JS para tema light
	const light = {
		color: "#222",
		bgColor: "#DDD"
	}

	//objeto JS para tema dark
	const dark = {
		color: "#DDD",
		bgColor: "#222"
	}

	//objeto con los estilos CSS para el elemento Box, definido como un <div> al renderizarse (recibiendo theme entre las props dentro de las funciones)
	const Box = styled.div`
		padding: 1rem;
		margin: 1rem;
		color: ${({theme}) => theme.color};
		background-color: ${({theme}) => theme.bgColor};
	`;

	//Renderizado
	return (
		<>
			<h2>Styled Components</h2>

			<ThemeProvider theme={light}>
				<Box>Soy una caja light</Box>
			</ThemeProvider>

			<ThemeProvider theme={dark}>
				<Box>Soy una caja dark</Box>
			</ThemeProvider>
		</>
	)
}
~~~

***Nota:*** El elemento `ThemeProvider` se utiliza solamente para envolver el contenido que tendrá el ***tema*** enviado desde el atributo `theme`.

En si, el elemento renderizado será el `Box`, el cual esta definido como un `div`.

---
## `Styled Components` con temas y herencia.

Los ***Styled Components*** también permiten realizar herencia de otros ***elementos*** y ***variables CSS*** definidas, veamos un ejemplo:

~~~jsx
//Importacion de libreria react
import React from "react";

//Importacion de libreria styled-components y modulos styled y ThemeProvider
import styled, {ThemeProvider} from "styled-components";

//Funcion de componente
export default function ComponentesEstilizados () {

	//objeto JS para tema light
	const light = {
		color: "#222",
		bgColor: "#DDD"
	}

	//objeto JS para tema dark
	const dark = {
		color: "#DDD",
		bgColor: "#222"
	}

		//objeto con los estilos CSS para el elemento Box, definido como un <div> al renderizarse (recibiendo theme entre las props dentro de las funciones)
	const Box = styled.div`
		padding: 1rem;
		margin: 1rem;
		color: ${({theme}) => theme.color};
		background-color: ${({theme}) => theme.bgColor};
	`;

	//Objeto hijo con herencia de estilos CSS de elemento Box
	const BoxRounded = styled(Box)`
		border-radius: 1rem;
	`;

	//renderizado
	return (
		<>
			<h2>Styled Components</h2>

			<ThemeProvider theme={light}>
				<Box>Soy una caja light</Box>
				<BoxRounded>Soy una caja redondeada light</BoxRounded>
			</ThemeProvider>

			<ThemeProvider theme={dark}>
				<Box>Soy una caja dark</Box>
				<BoxRounded>Soy una caja redondeada dark</BoxRounded>
			</ThemeProvider>
		</>
	)
}
~~~

***Nota:*** El elemento `BoxRounded` hereda todos los ***atributos*** y ***estilos CSS*** de `Box`, gracias a la línea `const BoxRounded = styled(Box)`.

---
## `Styled Components` con estilos globales.

Los `Styled Components` también permiten definir en nuestro proyecto ***estilos globales***, con ayuda del módulo `createGlobalStyle`.

Permitiendo definir estilos globales que afecten a todo nuestro proyecto:

#### 1. Importación de módulo `createGlobalStyle`.

Como primer paso, debemos importar el modulo `createGlobalStyle`, dentro del componente a usar:

~~~jsx
//Importacion de libreria styled components
import styled, {ThemeProvider, createGlobalStyle} from "styled-components";
~~~

#### 2. Creación de variable para estilos globales.

Se definen en una ***variable JS***  los estilo globales que deseamos integrar al proyecto, para ser llamadas en el siguiente paso.

~~~jsx
	//Creacion de estilos globales del proyecto
	const GlobalStyle = createGlobalStyle`
		h2 {
			padding: 2rem;
			background-color: #fff;
			color: #61dafb;
			text-transform: uppercase;
		}
	`;
~~~

***Nota:*** Utilizamos el ***modulo*** `createGlobalStyle` para este paso.
#### 3. Llamado a componente de contenido de estilos globales.

Como ultimo paso, dentro del ***return*** del renderizado, llamamos el ***componente*** definido para integrar los estilos globales.

~~~jsx
<GlobalStyle/>
~~~

***Nota:*** El componente se llama `GlobalStyle` debido a que en el paso 2 (Creación de variable para estilos globales) la variable fue definida con ese mismo nombre.

#### Visualización de código completo de ejemplo.

Veamos el código del ejemplo de manera completa:

~~~jsx
//Importacion de libreria react
import React from "react";

//Importacion de libreria styled components
import styled, {ThemeProvider, createGlobalStyle} from "styled-components";

//Funcion de componente
export default function ComponentesEstilizados () {

	//Tema light
	const light = {
		color: "#222",
		bgColor: "#DDD"
	}

	//Tema dark
	const dark = {
		color: "#DDD",
		bgColor: "#222"
	}

	//Creacion de estilos para elemento box que sera un div
	const Box = styled.div`
		padding: 1rem;
		margin: 1rem;
		color: ${({theme}) => theme.color};
		background-color: ${({theme}) => theme.bgColor};
	`;

	//Creacion de estilos extra ademas de los heredados  
	const BoxRounded = styled(Box)`
		border-radius: 1rem;
	`;

	//Creacion de estilos globales del proyecto
	const GlobalStyle = createGlobalStyle`
		h2 {
			padding: 2rem;
			background-color: #fff;
			color: #61dafb;
			text-transform: uppercase;
		}
	`;

	//Renderizado
	return (
		<>
			<GlobalStyle/>
			<h2>Styled Components</h2>

			<ThemeProvider theme={light}>
				<Box>Soy una caja light</Box>
				<BoxRounded>Soy una caja redondeada light</BoxRounded>
			</ThemeProvider>

			<ThemeProvider theme={dark}>
				<Box>Soy una caja dark</Box>
				<BoxRounded>Soy una caja redondeada dark</BoxRounded>
			</ThemeProvider>
		</>
	)
}
~~~

***Nota:*** Los estilos globales se aplican a todo el ***proyecto***, no importa desde que componente sean invocados, sin embargo, este por estándar suele ser llamado en el `index.js`.

