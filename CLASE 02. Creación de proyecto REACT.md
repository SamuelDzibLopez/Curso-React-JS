# 02. REACT Project Creation.

Para crear un proyecto de ***React*** podemos seguir los simples pasos:

---
## 1. Verificación de instalación de `npm` y `node.js`.

Para poder crear un proyecto de ***React***, necesitamos tener instalado: 

1. El ***entorno de ejecución de JavaScript***: 

	`node.js`

2. El ***sistema de gestión de paquetes***:

	`npm`

Para verificar la instalación, abre el símbolo del sistema o PowerShell y escriba:

~~~
node -v
npm -v
~~~

***Nota:*** Si no se encuentra instalado, puede descargarlo desde la pagina oficial la [página oficial de Node.js](https://nodejs.org/).

---
## 2. Creación de proyecto de `React`.

Aunque existen varias formas de empezar con ***React***, una manera sencilla y eficiente es con _**[create-react-app](https://create-react-app.dev/)**_, una aplicación de consola que nos va a permitir crear aplicaciones ***React*** con cero configuración, lo que nos permitirá centrarnos en los más importante: **Programar en _React_**.

Para crear una aplicación utilizamos el comando ***npx create-react-app*** seguido del nombre que le quieras dar a tu aplicación. 

~~~
npx create-react-app <nombre-proyecto>
~~~

Por ejemplo:

~~~
npx create-react-app curso-react
~~~

***Nota:*** Esto puede demorar unos minutos.

***¡Listo!***, hemos creado un proyecto de ***React***.

---
## 3. Abrir proyecto de `React`.

Una vez creado nuestro proyecto accedemos a el:

~~~
cd <nombre-proyecto>
~~~

E nuestro caso:

~~~
cd curso-react
~~~

***Nota:*** Esto ingresará al directorio.

---
## 4. Iniciar proyecto en `desarrollo`.

Dentro del ***directorio*** del ***proyecto***, para inicializar el ***proyecto*** con ayuda del comando:

~~~
npm start
~~~

***Nota:*** El último comando ejecuta el servidor de desarrollo y abre un navegador con una pantalla de bienvenida.

¡Felicidades!, has creado tu primera aplicación con ***React***.