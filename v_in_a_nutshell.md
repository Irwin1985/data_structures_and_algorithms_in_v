## Características de V

- Sintaxis similar a C/Go
- Compilación a código nativo
- V no tiene clases, en su lugar usa estructuras con métodos
- V usa interfaces
- V no implementa herencia, en su lugar permite structuras embebidas
- Las funciones en V son ciudadanas de primera clase
- Las funciones pueden retornar múltiples valores
- V posee Closures _(aunque no están disponibles para Windows)_
- V soporta concurrencia
- Simplicidad: el lenguaje se puede aprender en menos de una hora.
- Compilación Rápida
- Alto rendimiento: tan rápido como C _(de hecho V compila a C en su backend)_
- Seguridad: no hay datos nulos, no hay variables globales ni comportamientos indefinidos, es inmutable por defecto.
- Transpilación de C a V
- Gestión de memoria innovadora
- Librerías gráficas para distintas plataformas
- Web framework incluído
- ORM incluído

## Sintaxis Básica

```V
module main
fn main() {
  message := say_hello("Irwin")
  println(message)
}

fn say_hello(name string) string {
  return "Hola $name"
}
```

## Módulos
- La declaración de un módulo debe escribirse al inicio del código fuente.
- El módulo `main` es el módulo del ejecutable principal.
- Convención de ficheros: path/module donde el último nombre siempre es el nombre del módulo.
- Por defecto los tipos son privados, para hacerlos públicos hay que usar explícitamente `pub` delante del tipo.

## Operadores

<h5>Operadores Aritméticos</h5>

- `+` suma
- `-` resta
- `*` multiplicación
- `/` división

<h5>Operadores de comparación</h5>

- `==` igual
- `!=` distinto
- `<` menor que
- `>` mayor que
- `<=` menor igual que
- `>=` mayor igual que

<h5>Operadores Lógicos</h5>

- `&&` conjunción AND
- `||` disyunción OR


<h5>Otros Operadores</h5>

- `&` crear un objeto en el Heap en lugar de la pila.
- `<<` agregar un elemento a un array


## Funciones

<h5>Una función simple</h5>
<code>fn function_name() { /* body */ }</code>

<h5>Función con parámetros</h5>
<code>fn function_name(param1 string, param2 int) { /* body */ }</code>

<h5>Declaración del tipo de retorno</h5>

```V
fn function_name() int {
  return 19
}
```

<h5>Renornos múltiples</h5>

```V
fn return_multiple() (int, string) {
	return 19, "string value"
}
```

<h5>Funciones como Valores y Closures</h5>

```V
fn main() {
  // asignar una función a una variable
  sub := fn(a int, b int) int {
    return a - b
  }
  // usar la variable para invocar la función
  println(sub(6, 3))
}

// Closures (ámbito léxico): funciones que pueden acceder a las variables que están
// definidas en la función padre que ha definido la función Closure (se entiende?)
// ADVERTENCIA: las funciones Closures no están disponibles aún para Windows :(
fn scope() func() int {
  outer_var := 2
  foo := fn() int { return outer_var }
  return foo
}

fn another_scope() func() int {
  // no compilará porque outer_var y foo no están definidas en este ámbito.
  outer_var = 999
  return foo
}
```

## Funciones Variadicas

```V
fn main() {
  println(adder(1, 2, 3)) // 6
  println(adder(9, 9)) // 18
  nums := [10, 20, 30]
  println(adder(...nums)) // 60
}

// al usar ... después del nombre del último parámetros estamos indicando
// que tomará 0 o más parámetros del mismo tipo.
fn adder(args ...int) int {
  mut total := 0
  for a in args { // itera sobre todos los argumentos sin importal el número de ellos.
  total += a
  }
  return total
}
```

## Declaraciones de Variables

```V
// las variables solo se declaran dentro de funciones.
// solo hay una forma de declarar variables.
fn main() {
  foo := 'foo' // string
  bar := 20 // int
  // variables mutables
  foo := 'foo'
  foo = 'bar'
}
```

## Arrays, Slices y Rangos

<h5>Arrays</h5>

```V
fn main() {
  mut a := []int{len: 10} // define un array int de 10 elementos.
  a[5] = 19 // asigna el valor 19 al elemento 5 del array.
  i := a[5] // lee el elemento 5 del array
  // declarar e inicializar un array
  b := [5, 10, 15] // lo mismo que b := []int{len:3}
}
```

## Slices

```V
fn main() {
  a := [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
  println(a[..2]) // obtiene los 2 primeros elementos
  println(a[4..6]) // obtiene 2 elementos contanto a partir del índice 4
  println(a[..5]) // obtiene 5 elementos partiendo desde el primero
  println(a[..]) // obtiene todos los elementos
}
```

## Operaciones sobre Arrays

```V
fn main() {
  a := [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
  println(a.len) // imprime la longitud del array
  
  // iterar sobre los índices y valores del array
  for i, v in a {
    println("a[$i] = $v")
  }
  
  // iterar solamente sobre los valores
  for v in a {
    println(v)
  }
  
  // si solo necesitas el índice
  for i, _ in a {
    println(i) // solo el índice del array
  }
}
```

## Built-In Types

- bool
- string
- int8, int16, int, int64
- uint16, uint, uint64
- byte // alias para uint8
- rune // alias para int32 y representa un caracter unicode.
- f32, f64

## Estructuras de Control

<h5>If</h5>

```V
fn main() {
  x := 10
  // Básico
  if x > 0 {
    println("Mayor que cero")
  } else {
    println("Menor que cero")
  }
  day := "Monday"
  // Múltiples ramas
  if day == "Sunday" || day == "Saturday" {
    println("descansa")
  } else if day == "Monday" {
    println("A trabajar...")
  } else {
    println("Mitad de semana...")
  }
}
```

<h5>Loops</h5>

```V
fn main() {
  // hay solo una forma de iterar y es con for pero tiene muchas variantes
  // Array for
  numbers := [1, 2, 3, 4, 5]
  for num in numbers {
    println(num)
  }
  
  // Rangos
  for i in 0 .. 5 {
    println(i)
  }
  
  // for condicionado
  mut sum := 0
  mut i := 0
  for i <= 100 {
    sum += i
    i += 1
  }
  println(sum) // 5050
  
  // For solo: necesita sentencia break para romper el for.
  mut num := 0
  for {
    num += 2
    if num >= 10 {
      break
    }
  }
  println(num) // 10
  
  // For estilo C
  for i := 0; i < 10; i += 2 {
    if i == 6 {
      continue
    }
    println(i)
  }
}
```

<h5>Match</h5>

```V
fn main() {
  os := 'windows'
  match os {
  'darwin' {
    println('es un Mac')
  }
  'linux' {
    println('es linux')
  }
  else {
    println('es windows')
  }
  }
}
```


<h5>Maps o Diccionarios</h5>

```V
fn main() {
  // versión 1
  mut nums := map[string]int{}
  nums['uno'] = 1
  nums['dos'] = 2
  
  // versión 2
  mut pares := {
    'dos': 2
    'cuatro': 4
    'seis': 6
  }
  
  // leer una key
  println(nums['uno']) // 1
  
  // si una key no existe se retorna el valor por defecto según el tipo
  println(nums['ocho']) // devuelve cero porque el mapa es de int
  
  // usar un bloque or para las keys inexistentes
  print(nums['ocho'] or { panic('key no encontrada') })
}
```

<h5>Estructuras</h5>

```V
struct Edge {
  from int
  to int
}

fn (e Edge) str() string {
  return "Edge($e.from, $e.to)"
}

fn main() {
	e1 := Edge{1, 2}
    e2 := Edge{
      from: 1
      to: 2
    }
    // invocar el método str()
    println(e.str())
}
```