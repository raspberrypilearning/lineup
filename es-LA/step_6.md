## Cambia los disfraces

Por el momento, tu programa sella el mismo disfraz de objeto una y otra vez, y el tamaño del disfraz es demasiado grande.

--- task ---

Añade código al bloque `sellar objetos`{:class="block3myblocks"} para dar al objeto un tamaño adecuado antes de que comience el bucle `repetir`{:class="block3control"}. Añade un bloque dentro del bucle para cambiar al `siguiente disfraz`{:class="block3looks"} después del bloque `sellar`{:class="block3extensions"}.

```blocks3
define sellar objetos (filas) (columnas)
set size to (40) %
set [indice v] to [1]
repeat (columnas :: custom-arg)
go to x: (item (indice) of [x_posiciones v]) y: (item (indice) of [y_posiciones v]
stamp
next costume
change [indice v] by (1)
```

--- /task ---

Cuando ejecutas el script ahora, deberías ver algo como esto:

![objetos_cambiados](images/changed_sprites.png)

Tu programa recorre todos los disfraces en orden. Para que cada disfraz no aparezca en el mismo lugar cada vez que se ejecuta el programa, debes sellar el objeto en lugares aleatorios de la cuadrícula.

Para hacer esto, necesitas seguir este **algoritmo**:

1. `Repetir`{:class="block3control"} hasta que la lista esté vacía
2. Establecer `indice`{:class="block3variables"} a un número `al azar`{:class="block3operators"} entre `1` y la longitud de una lista
3. Mover el objeto como lo hiciste antes
4. Eliminar el elemento en la posición `indice`{:class="block3variables"} de la lista `y_posiciones`{:class="block3variables"}
5. Eliminar el elemento en la posición `indice`{:class="block3variables"} de la lista `x_posiciones`{:class="block3variables"}

--- task ---

Añade el código para sellar el objeto en lugares aleatorios de la cuadrícula.

--- hints ---
 --- hint ---

Remueve el `establecer índice a 1`{:class="block3variables"} antes del bucle `repetir`{:class="block3control"}.

Entonces dentro del bucle, `establecer índice`{:class="block3variables"} a un número `al azar`{:class="block3operators"} entre `1` y la `longitud de x_posiciones`{:class="block3variables"}.

Luego `borrar`{:class="block3variables"} el elemento en el `índice`{:class="block3variables"} de ambas listas `x_posiciones`{:class="block3variables"} y `y_posiciones`{:class="block3variables"}.

--- /hint --- --- hint ---

Aquí están los bloques adicionales que necesitas:

```blocks3
define sellar objetos (filas) (columnas)
set size to (40) %
- set [indice v] to [1]
repeat (columnas :: custom-arg)
go to x: (item (indice) of [x_posiciones v]) y: (item (indice) of [y_posiciones v]
stamp
next costume
- change [indice v] by (1)
end

set [indice v] to ()
(pick random () to ()
length of [x_posiciones v]
delete () of [x_posiciones v]

delete () of [y_posiciones v]
(indice)
(indice)
```

--- /hint --- --- hint ---

Así es como debería verse tu código:

```blocks3
define sellar objetos (filas) (columnas)
set size to (40) %
- set [indice v] to [1]
repeat (columnas :: custom-arg)
+ set [indice v] to (pick random (1) to (length of [x_posiciones v]))
go to x: (item (indice) of [x_posiciones v]) y: (item (indice) of [y_posiciones v]
+ delete (indice) of [x_posiciones v]
+ delete (indice) of [y_posiciones v]
stamp
next costume
- change [indice v] by (1)
```

--- /hint ------ /hints --- --- /task ---