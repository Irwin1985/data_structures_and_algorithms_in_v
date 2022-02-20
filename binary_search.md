## Implementación de una búsqueda binaria


 Una búsqueda binaria es una estrategia de búsqueda que se utiliza para encontrar elementos dentro
 de una lista al reducir constantemente la cantidad de datos a buscar y, por lo tanto, aumentar la
 velocidad a la que se encuentra el término de búsqueda. Para utilizar un algoritmo de búsqueda
 binaria, la lista que se va a operar ya debe haber sigo ordenada.

 
```V
module main

fn main() {
	array := [1, 2, 9, 20, 31, 45, 63, 70, 100]
	println(binary_search(array, 120))
}

fn binary_search(array []int, search_value int) bool {
	mut low := 0
	mut high := array.len - 1

	for low <= high {
		median := (low + high) / 2
		if array[median] < search_value {
			low = median + 1
		} else {
			high = median - 1
		}
	}

	if low == array.len || array[low] != search_value {
		return false
	}
	return true	
}
```