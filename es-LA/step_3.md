## Crea una cuadrícula

Vas a crear una cuadrícula de sellos de disfraces:

![sellos en la cuadrícula](images/stamp_grid.png)

Para hacer esto necesitas saber las coordenadas `x`{:class="block3motion"} y `y`{:class="block3motion"} de dónde se debe colocar cada sello.

\--- task \---

Primero, crea un nuevo bloque llamado `generar posiciones`{:class="block3myblocks"}. El bloque necesita tener dos parámetros de 'entrada de números'. Llama a los dos parámetros `filas`{:class="block3myblocks"} y `columnas`{:class="block3myblocks"}.

Los valores de estos parámetros decidirán cuántas filas y columnas tiene tu cuadrícula.

[[[generic-scratch3-make-block]]]

```blocks3
define generate positions (rows)(columns)
```

\--- /task \---

\--- task \---

Crea dos listas y nombra a una de ellas `x_posiciones`{:class="block3variables"} y a la otra `y_posiciones`{:class="block3variables"}. Estas listas son para almacenar las coordenadas `x`{:class="block3motion"} y `y`{:class="block3motion"} para los sellos.

\--- /task \---

\--- task \---

Dentro de tu bloque `generar posiciones`{:class="block3myblocks"}, añade bloques para eliminar todos los elementos de ambas listas, de modo que cada vez que el juego comience, las listas están vacías.

```blocks3
define generate positions (rows)(columns)
+ delete [all v] of [y_positions v]
+ delete [all v] of [x_positions v]
```

\--- /task \---

\--- task \---

A continuación, crea dos variables y llama a una de ellas `x_pos`{:class="block3variables"} y a la otra `y_pos`{:class="block3variables"}.

\--- /task \---

La lista `x_posiciones `{:class="block3variables"} debe contener diez números en total, y estos deben comenzar en `-200`{:class="block3variables"} y llegar hasta `200`{:class="block3variables"}.

Por ahora, la lista `y_posiciones`{:class="block3variables"} sólo puede contener el número `-150`{:class="block3variables"} diez veces, para que la cuadrícula sólo tenga una fila.

\--- task \---

Empieza añadiendo código al bloque `generar posiciones`{:class="block3myblocks"} para establecer la variable `y_pos`{:class="block3variables"} a `-150`{:class="block3variables"} y la variable `x_pos`{:class="block3variables"} a `-200`{:class="block3variables"}. Esta es la ubicación del primer objeto sellado.

```blocks3
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
+ set [y_pos v] to [-150]
+ set [x_pos v] to [-200]
```

\--- /task \---

\--- task \---

A continuación, añade un bucle `repetir`{:class="block3control"} para colocar las coordenadas en las listas.

El bucle `repetir`{:class="block3control"} debe ejecutarse una vez por cada columna que quieras que tenga la cuadrícula.

El bloque `generar posiciones`{:class="block3myblocks"} toma `columnas`{:class="block3myblocks"} como entrada, así que puedes usar `columnas`{:class="block3myblocks"} para el bucle `repetir`{:class="block3control"}.

```blocks3
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
set [x_pos v] to [-200]
+ repeat (columns :: custom-arg)
```

\--- /task \---

Dentro del bucle `repetir`{:class="block3control"}, añade los valores de `x_pos`{:class="block3variables"} y `y_pos`{:class="block3variables"} a las listas. Luego necesitas aumentar un poco el valor de `x_pos`{:class="block3variables"}. ¿En cuánto debería aumentar el valor de `x_pos`{:class="block3variables"}?

Esta es la forma de averiguarlo:

- `x_pos`{:class="block3variables"} comienza con el valor `-200`{:class="block3variables"}
- La última vez que se ejecuta el bucle `repetir`{:class="block3control"}, `x_pos`{:class="block3variables"} debería alcanzar el valor `200`{:class="block3variables"}
- Eso es un aumento total de `400`{:class="block3variables"}
- El primer valor `x_pos`{:class="block3variables"} es para la primera columna de la cuadrícula, y la cantidad de columnas que hay está determinada por la entrada de `columnas`{:class="block3myblocks"}

Así que después de que se agrega el primer valor `x_pos`{:class="block3variables"}, en cada repetición del bucle, el valor de `x_pos`{:class="block3variables"} debe aumentar en `400 / (columns - 1)`{:class="block3operators"}

\--- task \---

Añade el código que agregará todos los valores `x_pos`{:class="block3variables"} y `y_pos`{:class="block3variables"} a las listas `x_posiciones`{:class="block3variables"} y `y_posiciones`{:class="block3variables"}.

\--- hints \--- \--- hint \---

Dentro del bucle, tienes que añadir `x_pos`{:class="block3variables"} a la lista `x_posiciones`{:class="block3variables"}, y añadir `y_pos`{:class="block3variables"} a la lista `y_posiciones`{:class="block3variables"}. Luego, la variable `x_pos`{:class="block3variables"} debe aumentar en `400 / (columns -1)`{:class="block3operators"} cada vez que el bucle se repite.

\--- /hint \--- \--- hint \---

Esto muestra los bloques adicionales que necesitas añadir a tu script.

```blocks3
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
set [x_pos v] to [-200]
repeat (columns :: custom-arg)
end

(x_pos)
(y_pos)

add () to [x_positions v]

add () to [y_positions v]

change [x_pos v] by ()
(columns ::custom
() / () 
() - ()
```

\--- /hint \--- \--- hint \---

Este es el script completado para el bloque `generar posiciones`{:class="block3myblocks"}:

```blocks3
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
set [x_pos v] to [-200]
repeat (columns :: custom-arg)
+ add (x_pos) to [x_positions v]
+ add (y_pos) to [y_positions v]
+ change [x_pos v] by ((400) / ((columns :: custom-arg) - (1)
```

\--- /hint \--- \--- /hints \--- \--- /task \---