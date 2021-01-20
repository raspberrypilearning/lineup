## Añade filas

Ahora que tienes el código para crear una sola fila de disfraces sellados, debes añadir código para crear más filas.

Ve a tu bloque `generar posiciones`{:class="block3myblocks"}.

```blocks3
define generar posiciones (filas)(columnas)
delete [all v] of [y_posiciones v]
delete [all v] of [x_posiciones v]
set [y_pos v] to [-150]
set [x_pos v] to [-200]
repeat (columnas :: custom-arg)
add (x_pos) to [x_posiciones v]
add (y_pos) to [y_posiciones v]
change [x_pos v] by (((400) / (columnas)) - (1))
```

--- task ---

Añade otro bucle `repetir`{:class="block3control"} que se ejecute el numero de veces que le proporcionas al bloque `generar posiciones`{:class="block3myblocks"} como la entrada de `filas`{:class="block3myblocks"}. Coloca el bucle `repetir`{:class="block3control"} en tu script como se muestra aquí:

```blocks3
definir generar posiciones (filas) (columnas)
eliminar [todos v] de [y_posiciones v]
eliminar [todos v] de [x_posiciones v]
establecer [y_pos v] a [-150]
+ repetir (filas :: custom-arg)
establecer [x_pos v] a [-200]
repetir (columnas :: custom-arg)
añadir (x_pos) a [x_posiciones v]
añadir (y_pos) a [y_posiciones v]
cambiar [x_pos v] en (((400) / (columnas :: custom-arg)) - (1))
fin
fin
```

--- /task ---

A continuación debes aumentar el valor de `y_pos`{:class="block3variables"} cada vez que se ejecuta el bucle `repetir (filas)`{:class="block3control"}.

Haz esto en una forma similar a como incrementas el valor de `x_pos`{:class="block3variables"} en el bucle `repetir (columnas)`{:class="block3control"}.

--- task ---

Al final del código dentro del bucle `repetir (filas)`{:class="block3control"}, `y_pos`{:class="block3variables"} debería aumentar hasta `150`{:class="block3variables"}, lo cual está `300`{:class="block3variables"} lejos de su valor inicial de `-150`{:class="block3variables"}. Esto debe suceder por cada fila de sellos.

```blocks3
define generar posiciones (filas)(columnas)
delete [all v] of [y_posiciones v]
delete [all v] of [x_posiciones v]
set [y_pos v] to [-150]
repeat (filas :: custom-arg)
set [x_pos v] to [-200]
repeat (columnas :: custom-arg)
add (x_pos) to [x_posiciones v]
add (y_pos) to [y_posiciones v]
change [x_pos v] by (((400) / (columnas :: custom-arg)) - (1))
end
+change [y_pos v] by (((300) / (filas :: custom-arg)) - (1))
end
```

--- /task ---

--- task ---

Asegúrate de dar el número de `filas`{:class="block3myblocks"} como entrada a tus bloques.

```blocks3
when flag clicked
erase all
generar posiciones (4) (10) ::custom
sellar objetos(4) (10) ::custom
```

--- /task ---

--- task ---

Ejecuta tu código ahora.

![desorden de sellos](images/mess_stamps.png)

No obtendrás una cuadrícula de sellos ordenada.

Esto se debe a que, ahora mismo, el bloque `sellar objetos`{:class="block3myblocks"} sólo se ejecuta para el número total de columnas.

--- /task ---

--- task ---

Cambia tu script de `sellar objetos`{:class="block3myblocks"} para que `se repita`{:class="block3control"} suficientes veces para estampar la cuadrícula completa de objetos.

--- hints ---
 --- hint ---

El número total de sellos que necesitas es el número que das como `columnas`{:class="block3myblocks"} multiplicado por el número que das como `filas`{:class="block3myblocks"}

--- /hint --- --- hint ---

Utiliza este bloque adicional:

```blocks3
((filas ::custom) * (columnas ::custom))
```

--- /hint --- --- hint ---

Aquí está el script terminado de `sellar objetos`{:class="block3myblocks"}:

```blocks3
define sellar objetos (filas) (columnas)
set size to (40) %
+ repeat ((filas :: custom-arg) * (columnas :: custom-arg))
set [indice v] to (pick random (1) to (length of [x_posiciones v]))
go to x: (item (indice) of [x_posiciones v]) y: (item (indice) of [y_posiciones v]
delete (indice) of [x_posiciones v]
delete (indice) of [y_posiciones v]
stamp
next costume
```

--- /hint ------ /hints ---

![cuadrícula ordenada](images/nice_grid.png)

--- /task ---