## Variables

Lo que hay que entender acerca de las variables es que son `nombres` o `aliases` que representan un valor _(data)_ en la memoria del ordenador, por lo tanto las variables son *contenedores de datos.* 

Ejemplo:

`y := x + 2`

## Tipos de Datos

Las variables pueden contener cualquier tipo de dato como números, conjunto de caracteres, números con decimales, o simplemente ceros y unos. Un tipo de dato es un conjunto de datos con valores predefinidos, por ejemplo: *integer, float, string, etc.*

La memoria del ordenador está llena de ceros y unos, si queremos resolver un problema en específico nos resultaría bastante difícil hacerlo solo con ceros y unos; para eso existen los *lenguajes de programación*, ellos nos facilitan la escritura de código a través de *tipos de datos*. Por ejemplo un entero _(int)_ toma 2 *bytes* _(aunque depende del compilador)_, un `float` toma 4 *bytes*, etc. Esto quiere decir que en la memoria estamos reservando 2 bytes y lo llamamos `int`, de la misma forma reservamos 4 bytes y los llamamos `float`. Por lo tanto un tipo de dato reduce bastante el esfuerzo de tener que trabajar con bytes crudos en la memoria.

La mayoría de los lenguajes de programación ofrecen 2 categorías para los tipos de datos:

- Tipos de datos Primitivos
- Tipos de datos definidos por el usuario

<h5>Tipos de datos Primitivos</h5>

Son los tipos de datos definidos por el sistema y pueden ser `int` *(8, 16, 32, 64)* y `float` *(32, 64)*. El número de bits asignados para cada tipo primitivo dependerá del lenguaje de programación, el compilador y el sistema operativo, esto quiere decir que para el mismo tipo de dato primitivo pueden haber diferentes tamaños en diferentes lenguajes de programación.



<h5>Tipos de datos definidos por el usuario</h5>

Cuando los tipos de datos primitivos no son suficientes para llevar a cabo una tarea, el usuario puede optar por crear sus propios tipos de datos siempre y cuando el lenguaje de programación lo permita. Un ejemplo de estos tipos son las estructuras `struct` en V. 

```V
struct User {
	id 		int
	name 	string
	login 	string
	active 	bool	
}
```

## Estructura de Datos

Una vez que tenemos los datos en variables, necesitaremos algún mecanismo para manipular esos datos y resolver nuestro problema. Las estructuras de datos son una forma particular de almacenar y organizar los datos en el ordenador con la finalidad de ser manipulados de forma eficiente. Una estructura de datos entonces es como un formato que debemos seguir para organizar y almacenar los datos. Las estructuras de datos más conocidas son los *arrays, listas enlazadas, pilas, colas, árboles, grafos, etc.*

Dependiendo del tipo de organización de los elementos, las estructuras de datos se clasifican en 2 tipos:

- Estructuras de datos lineales: los elementos son accedidos siguiendo un orden secuencial pero no es obligatorio almacenarlos de la misma forma, Ejemplo:  _pilas, colas, listas enlazadas_
- Estructuras de datos no lineales: los elementos son acceditos y almacenados de forma *no lineal*, ejemplo: *árboles y grafos.*


## Tipos de datos abstractos (ADTs)

Los tipos de datos primitivos ya vienen con un comportamiento por defecto, es decir, se pueden realizar operaciones sobre ellos de forma nativa, por ejemplo operaciones aritméticas sobre tipos numéricos. Por otro lado, los tipos de datos definidos por el usuario necesitan su definición y su comportamiento, es decir, el tipo de operaciones que esos tipos pueden soportar.

Para simplificar el proceso de resolución de problemas, tanto las operaciones _(comportamiento)_ como las definiciones se pueden combinar y formar lo que se conoce como *Tipo de dato abstracto*.

Un tipo de dato abstracto consta de 2 partes:

1. Declaración de la data
2. Declaración de las operaciones que soporta esa data

Los ADT más comúnes son las listas enlazadas, pilas, colas, árboles binarios, diccionarios, grafos, etc. Por ejemplo: una pila usa el mecanismo LIFO _(Last-In-First-Out)_ para almacenar los datos. El último elemento insertado en la pila será el primero en salir o ser eliminado. Las operaciones comúnes de una pila son: crear la pila, agregar un elemento en la pila (push), eliminar un elemento de la pila (pop), solitar el elemento posicionado en la cima de la pila (peek), buscar un elemento en la pila.

Al definir el comportamiento de un ADT no hay que preocuparse mucho por los detalles de su implementación, ellos tendrán lugar solo cuando querramos usarlos. Hay muchos tipos de ADT's y cada uno es eficiente en la tarea para la cual fueron diseñados.


## Qué es un Algoritmo

Para entender mejor el concepto, vamos a considerar el siguiente problema: 

Necesitamos preparar un omelette y para ello debemos seguir los siguientes pasos:

1. Conseguir un sartén
2. Conseguir aceite
	a. Tenemos aceite en la cocina?
		- Sí: poner el aceite en la sartén
		- No: quieres comprar aceite?
			- Sí: ir a la tienda a por aceite.
			- No: deja todo y vete a dormir.
3. Encender la cocina, etc...

