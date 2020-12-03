## Sella una fila

Hasta ahora tienes diez valores en cada una de las dos listas. Ahora sella algunos disfraces en las coordenadas del escenario almacenadas en las listas.

\--- task \---

Añade la extensión **Lapicero** a tu proyecto.

[[[generic-scratch3-add-pen-extension]]]

\--- /task \---

\--- task \---

Crea un nuevo bloque y llámalo `sellar objetos`{:class="block3myblocks"}. Este bloque necesita dos entradas numéricas llamadas `filas`{:class="block3myblocks"} y `columnas`{:class="block3myblocks"} al igual que el otro bloque personalizado.

```blocks3
define stamp sprites (rows) (columns)
```

\--- /task \---

\--- task \---

Crea una nueva variable llamada `indice`{:class="block3variables"} con la cual rastrear la posición en las listas que tu programa está leyendo. Para empezar, establece `indice`{:class="block3variables"} a `1`{:class="block3variables"} para obtener el primer elemento de cada lista.

```blocks3
define stamp sprites (rows) (columns)
+ set [index v] to [1]
```

\--- /task \---

\--- task \---

El bloque `sellar objetos`{:class="block3myblocks"} debe sellar un objeto para cada par de coordenadas en la lista. Para hacer esto, el bloque necesita un bucle `repetir`{:class="block3variables"} que se ejecute una vez por cada columna.

```blocks3
define stamp sprites (rows) (columns)
set [index v] to [1]
+ repeat (columns :: custom-arg)
```

\--- /task \---

\--- task \---

Dentro del bucle `repetir`{:class="block3variables"}:

- Mueve el objeto a la posición `indice`{:class="block3variables"} en las listas `x_posiciones`{:class="block3variables"} y `y_posiciones`{:class="block3variables"}
- `Sellar`{:class="block3extensions"} el objeto
- Cambiar el `indice`{:class="block3variables"} en `1`{:class="block3variables"}

\--- hints \--- \--- hint \---

Dentro del bucle `repetir`{:class="block3variables"}, añade un bloque `ir a x: y:`{:class="block3motion"}. La posición `x`{:class="block3motion"} en este bloque debe establecerse en el `indice`{:class="block3variables"} de `x_posiciones`{:class="block3variables"} y la posición `y`{:class="block3motion"} debe establecerse en el `indice`{:class="block3variables"} de `y_posiciones`{:class="block3variables"}. Luego añade código para `sellar`{:class="block3extensions"} el objeto. Finalmente, añade código para aumentar el `indice`{:class="block3variables"} en 1.

\--- /hint \--- \--- hint \---

Aquí están los bloques que necesitas:

```blocks3
define stamp sprites (rows) (columns)
set [index v] to [1]
repeat (columns :: custom-arg)
end

change [index v] by (1)
(index) 
(index) 
go to x: () y: ()
(item ()of [y_positions v])
(item ()of [x_positions v])
stamp
```

\--- /hint \--- \--- hint \---

Este es el script completado para el bloque `sellar objetos`{:class="block3myblocks"}:

```blocks3
define stamp sprites (rows) (columns)
set [index v] to [1]
repeat (columns :: custom-arg)
+ go to x: (item (index) of [x_positions v]) y: (item (index) of [y_positions v]
+ stamp
+ change [index v] by (1)
```

\--- /hint \--- \--- /hints \--- \--- /task \---

\--- task \---

Añade un bloque `borrar todo`{:class="block3extensions"} debajo del bloque `al presionar la bandera`{:class="block3control"} para limpiar el escenario cada vez que comienza el juego. Luego añade el bloque `sellar objetos`{:class="block3myblocks"} en la parte inferior del script `al presionar la bandera`{:class="block3control"} para que puedas probar tu nuevo código.

```blocks3
when flag clicked
erase all
generate positions (1) (10) ::custom
stamp sprite (1) (10) ::custom
```

\--- /task \---

\--- task \---

Haz clic en la bandera verde. Deberías ver algo como esto, dependiendo de los disfraces que tenga tu objeto:

![objetos sellados](images/stamped_sprites.png)

\--- /task \---