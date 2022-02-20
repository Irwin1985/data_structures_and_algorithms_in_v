## Ordenamiento por selección

Es un algoritmo de ordenamiento que requiere O(n2) operaciones para ordenar una lista de n elementos.

Su funcionamiento es el siguiente:

- Buscar el mínimo elemento de la lista
- Intercambiarlo con el primero
- Buscar el siguiente mínimo en el resto de la lista
- Intercambiarlo con el segundo

Y en general:

- Buscar el mínimo elemento dentre una posición i el final de la lista
- Intercambiar el mínimo con el elemento de la posición i


```V
module main

fn main() {
	mut list := [65, 15, 25, 35, 85, 55, 45, 75, 95]
	println(selection_sort(mut list))
}

fn selection_sort(mut array []int) []int {
	for i := 0; i < array.len - 1; i++ {
		mut lowest_number_index := i
		for j := i + 1; j < array.len; j++ {
			if array[j] < array[lowest_number_index] {
				lowest_number_index = j
			}
		}
		if lowest_number_index != i {
			temp := array[i]
			array[i], array[lowest_number_index] = array[lowest_number_index], temp
		}
	}
	return array
}
```