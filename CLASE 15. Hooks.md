# 15. Hooks

Los "Hooks" son **ganchos** que nos permiten enganchar mediante funciones los **estados** a los componentes que nos sean de **clases**.

Son una funcionalidad que nos permitirá enganchar mediante funciones los estados y ciclos de vida a todo tipo de componentes

	Los componentes funcionales anteriormente a los "Hooks" se les conocia como componentes contenedores o componentes tontos.

Esto debido a que no tenían una funcionalidad tan compleja como los ***componentes basados en clases***.

Esto debido a no tener y ser compatibles con las funciones de ciclo de vida:

	- render
	- componentDidMount
	- componentDidUpdate
	- componentWillUnmount
	- etc.

## Preguntas frecuentes:

1. ¿Los ***Hooks*** hacen que la aplicación sea más rápida? ***NO***.
2. ¿Los ***Hooks*** hacen algo que un Componente de Clase no pueda hacer? ***NO***
3. ¿Los Componentes de Clase van a desaparecer? ***NO***
4. ¿Mi conocimiento del estado, las propiedades y los eventos serán obsoletos ahora con los ***Hooks***? ***NO***
5. ¿Debo reescribir todas mis aplicaciones *React* ahora con ***Hooks***? ***NO***
6. ¿Debo implementar ***Hooks*** en mi próximo proyecto? ***Probablemente SI***

## Tipos de Hooks

	Basicos (en el 100% de tus proyectos)
		- useState (Manejar estado)
		- useEffect (Simular ciclo de vida)
	Avanzados (tal vez no en todos tus proyectos)
		- useContext
		- useRel
		- useReducer
		- useCallback
		- useMemo

