## Ordenamiento en Burbuja


 Es un algoritmo sencillo que funciona revisando cada elemento de la lista que va a ser ordenada con el siguiente, 
 intercambiándolos de posición si están en el orden equivocado. Es necesario revisar varias veces toda la lista hasta
 que no se necesiten más intercambios, lo cual significa que la lista está ordenada.


```V
module main

fn main() {
	mut list := [65, 55, 45, 35, 25, 15, 10]
	println(bubble_sort(mut list))
}

fn bubble_sort(mut list []int) []int {
	mut unsorted_until_index := list.len - 1
	mut sorted := false

	for !sorted {
		sorted = true
		for i in 0..unsorted_until_index {
			if list[i] > list[i+1] {
				list[i], list[i+1] = list[i+1], list[i]
				sorted = false
			}
		}
		unsorted_until_index -= 1
	}

	return list
}
```