## Qué es Reursión

Recursión es cualquier función que sea capaz de llamarse a sí misma. Una función recursiva resuelve un problema invocando a una copia de sí misma para trabajar en un problema más pequeño, a esto se le conoce como *paso de recursión* y pueden haber muchos de estos en una llamada recursiva.

Al crear funciones recursivas siempre hay que evaluar el proceso de cierre de la función, cuando la función comienza a llamarse a sí misma se conoce como `wind` y una vez que se ejecuta el código de cierre, inicia la fase `unwind` hasta llegar al bloque de código de la función que se invocó la primera vez.

## Por qué la Recursión?

Porque el código recursivo es generalmente más corto y más fácil de escribir que el código iterativo. La recursión es más útil en tareas que pueden ser definidas en subtareas similares. Por ejemplo: ordenamientos, búsquedas, y problemas transversales.

## Recursión Vs Interación

¿Cuál es mejor, la recursión o la iteración? la respuesta a esta pregunta depende de loque vayamos a realizar. 

### Recursión
- Termina cuando el caso base es alcanzado _(el código que rompe la recursividad)_
- Cada llamada recursiva requiere de espacio extra en el stack-frame _(memoria)_
- Si no controlamos el cierre, la función puede ser infinita causando un problema de memoria que resulta en un desbordamiento de memoria *stack overflow*