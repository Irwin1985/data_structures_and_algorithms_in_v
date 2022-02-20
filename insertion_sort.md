## Ordenamiento por inserción

Es una manera muy natural de ordenar para un ser humano, y puede usarse fácilmente para ordenar un mazo
de cartas numeradas en forma arbitraria.


```V
module main

fn main() {
	mut array := [15, 45, 25, 35, 55]
	println(insertion_sort(mut array))
}

fn insertion_sort(mut array []int) []int {
	for index in 1 .. array.len {
		temp_value := array[index]
		mut position := index - 1
		for position >= 0 {
			if array[position] > temp_value {
				array[position+1] = array[position]
				position -= 1
			} else {
				break
			}
		}
		array[position + 1] = temp_value
	}
	return array
}
```