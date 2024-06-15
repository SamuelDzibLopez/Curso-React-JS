# 4. Componentes.

### Creación de un componente.

Un componente es una pieza de UI, que una vez creada (codificada), puede ser usada múltiples veces sin la necesidad de volver a crear.

Dentro de la carpeta de un proyecto de react, dentro de ***src***, podemos crear una carpeta ***components***, donde almacenar todos nuestros componentes que vayamos creando. 

Como buena practica, un componente suele ser creado usando el UpperCameCase:

~~~
Component
~~~
### Importar  REACT en un componente.

**Nota:**
Es importante siempre importar la librería de REACT en los componentes.

De la siguiente manera:

~~~
import React from "react";
~~~
### Diferentes maneras de crear un componente.

Existen diferentes maneras de crear componentes.

- **Componente** basado en ***Clases*
- **Componente** basado en **Funciones declaradas**
- **Componente** basado en funciones **expresadas**

A continuación, un ejemplo de cada uno de ellos:
##### Componente basado en clases:

Se trata de un ***objeto*** declarado por medio de una clase ***Component*** de ***react***.

~~~
import React, { Component } from "react";

class Componente extends Component {
	render() {
	return <h2>{this.props.msg}</h2>
	}
}

export default Componente;

/*
Este es un componente basado en clases
*/
~~~

Consta de la función base ***render***, para retornar contenido (en este caso, JSX).

Para finalizar un ***export default*** del componente. 
##### Componente basado en funciones declaradas:

Se trata de una ***función*** de tipo declarada que retorna texto de tipo ***JSX***. 

~~~
import React, { Component } from "react";

function Componente2 (props) {
	return <h2>{props.msg}</h2>
}

export default Componente2;

/*
Este es un componente basado en una funcion declarada
*/
~~~

Al terminar la función, usamos un ***export default*** para exportar el componente
##### Componente basado en funciones expresadas:

Esta forma de creación de un componente usar una ***función expresada*** en una ***constante***, acompañada de una ***arrow function***.

~~~
import React, { Component } from "react";

const Componente3 = props => <h2>{props.msg}</h2>;

export default Componente3;
~~~

Como toda ***arrow function***, esta no necesita llaves, y por ultimo, exporta el componente con un ***export default***

### Usar un componente en un archivo externo.

Los componentes son piezas que, muy a menudo encajan o van dentro de otras piezas, por ello, es necesario importarlos o llamarlos en otros componentes o archivos.  

Para importar un componente, primero definimos con un export:

~~~
import Componente from "./components/Componente";
~~~

una vez ya importado el componente, podremos usarlo dentro del archivo.

Para hacer uso de este, llamamos al componente, tal como llamaríamos una ***etiqueta HTML**.

~~~
<Componente
	msg = "¡Hola!, Soy un componente de clase."
/>
~~~

El nombre del componente, es el mismo a utilizar a como se declaro al ser creado.

***Nota:***
Podemos enviar ***parámetros*** a un componente para ser utilizado por este. próximamente se explicará.

