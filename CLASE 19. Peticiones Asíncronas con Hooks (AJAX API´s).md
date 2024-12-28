# 19. Asynchronous Requests with Hooks (AJAX API's).

Con ayuda de los ***Hooks*** podemos realizar peticiones asincronas (con ***vanila JS*** ), y llamdos a servicios, esto utilizando los ***hooks*** de ***useState*** y ***useEffect***.

Veamos un ejemplo:

~~~jsx
//Importacion de React, useState y useEffect
import React, { useState, useEffect } from 'react';

//Componente hijo (tarjeta de pokemon)
function Pokemon(props) {
    return(
        <figure>
            <img src={props.avatar} alt={props.name}/>
            <figcaption>{props.name}</figcaption>
        </figure>
    );
}

//Componente padre
export default function AjaxHooks () {

    //Creacion de stado pokemon con useState (un array para guerdar el fetch de datos de la API)

    const [pokemons, setPokemons] = useState([])

    //uso de useEffect para presentar el montaje del componente
    useEffect(() => {
        let url = "https://pokeapi.co/api/v2/pokemon/";

        //fetch a la API (vanila JS)
        fetch(url)
            .then((res) => res.json())
            .then((json) => {
                json.results.forEach((el) =>{
                    fetch(el.url)
                        .then((res) => res.json())
                        .then((json) => {
                            let pokemon = {
                                id: json.id,
                                name: json.name,
                                avatar: json.sprites.front_default,
                            };

                            setPokemons((pokemons) => [...pokemons, pokemon]);
                        })
                })
            })
    },[]);

    return(
        <>
            <h2>Peticiones asincronas en Hooks</h2>
            {pokemons.length === 0 ? (<h3>Cargando...</h3>):(
                pokemons.map((el) => (
                    <Pokemon key={el.id} name={el.name} avatar={el.avatar}/>
                ))
            )}
        </>
    )
}
~~~

***Nota:*** Este es un pequeño código de una petición asíncrona con ***fetch*** a la ***API*** de ***Pokémon***.

