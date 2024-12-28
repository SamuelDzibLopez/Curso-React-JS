# 03. REACT Project Structure.

Una vez creado ***nuestro proyecto***, entendamos que contiene:

---
## ¿Qué incluye `create-react-app`?

Un proyecto creado con ***create-react-app***, además de ***React***, incluye librerías como:

- _**Webpack**_: que se encarga de procesar y empaquetar nuestro código _JavaScript_ (con sus dependencias), archivos _CSS_ y otros archivos estáticos como imágenes, vectores, fuentes, etc.
- _**Babel**_: que nos permite usar nuevas características de _ECMAScript_.
- _**PostCSS**_ que es una librería para el procesamiento de _CSS_.
- _**Jest**_ que es una librería para _testing_.
- etc.

Uno podría configurar un proyecto de ***React*** manualmente e incluir cada una de estas librerías, pero es bastante engorroso, ***create-react-app*** nos hace la vida más fácil.

---
### Estructura de directorio

***create-react-app*** crea la siguiente estructura de archivos y carpetas:

```
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
```

Los dos archivos más importantes son:

- _**public/index.html**_ - la plantilla _HTML_ de la aplicación.
- _**src/index.js**_ - el punto de entrada _JavaScript_ de la aplicación.

Puedes eliminar o renombrar otros archivos según tus necesidades.

Dentro de _**src**_ se incluyen todos los archivos _JavaScript_ y _CSS_ de tu aplicación.

También es recomendable incluir otros archivos estáticos como imágenes y fuentes en esta carpeta. Puedes crear subcarpetas para organizar mejor los archivos.

En _**public**_ van todos los archivos estáticos que necesites incluir en la plantilla _**public/index.html**_.

Puedes crear otras carpetas además de _**src**_ y _**public**_. Estas carpetas no van a ser incluídas en el paquete de distribución.

---
### _Scripts_

En la carpeta del proyecto puedes ejecutar los siguientes comandos:

- _**npm start**_ - inicia el servidor de desarrollo y abre un navegador con la aplicación.
- _**npm test**_ - ejecuta las pruebas.
- _**npm run build**_ - empaqueta la aplicación para producción en la carpeta _**build**_.
- _**npm run eject**_ - permite cambiar manualmente las librerías y configuración que utiliza _create-react-app_ por defecto. Ten cuidado con este comando, una vez que se expulsa la configuración inicial **no hay vuelta atrás**.

---
### _Hot reloading_

Una de las funcionalidades más importantes de los proyectos creados con _create-react-app_ es la capacidad de hacer cambios en vivo sin necesidad de reiniciar el servidor. Si haces un cambio en algún archivo en _**src**_ o _**public**_ el navegador se refresca automáticamente.

---
## JSX

Es una extensión de la sintaxis de ***JavaScript*** que produce elementos de ***React***.

Se puede usar:

- Dentro de estructuras de control como ***if*** y ***for***.
- Asignarlo a ***variables***.
- Aceptarlo como argumento o retorno en ***funciones***.
- Expresiones ***JavaScript***.

Veamos un ejemplo tomado del código que genera ***create-react-app***:

```jsx
<div className="App">
  <header className="App-header">
    <img src="{logo}" className="App-logo" alt="logo" />
    <h1 className="App-title">Welcome to React</h1>
  </header>
  <p className="App-intro">
    To get started, edit <code>src/App.js</code> and save to reload.
  </p>
</div>
```

_**JSX**_ es similar a ***HTML*** pero con algunas diferencias importantes:

Algunas reglas importantes:

- Toda etiqueta debe cerrarse por ejemplo `<br>` debera cerrarse a `<br />`.
- Los componentes deben devolver un sólo elemento padre.
- Algunos atributos _HTML_ cambian como:
    - _**class**_ por _**className**_.
    - _**for**_ por _**htmlFor**_.
- Los atributos de un elemento _JSX_ pueden aceptar valores de tipo _String_ entrecomillados o expresiones _JavaScript_ entre llaves, por ejemplo:
    - `<img alt="Avatar" src={user.avatarURL} />`