## Добавь строки

Теперь, когда у тебя есть код для создания одной строки отпечатанных костюмов, ты должен добавить код для создания большего количества строк.

Перейди к блоку `генерировать позиции`{:class="block3myblocks"}.

```blocks3
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
set [x_pos v] to [-200]
repeat (columns :: custom-arg)
add (x_pos) to [x_positions v]
add (y_pos) to [y_positions v]
change [x_pos v] by (((400) / (columns)) - (1))
```

\--- task \---

Добавьте еще один цикл `повторить`{:class="block3control"}, который запускается то количество раз, которое ты определяешь в блоке `генерировать позиции`{:class="block3myblocks"} в виде `строк`{:class="block3myblocks"}. Помести цикл `повторить`{:class="block3control"} в твой скрипт, как показано здесь:

```blocks3
определить generate positions (строки :: custom-arg) (столбцы :: custom-arg)
удалить [all v] из [y_позиции v]
удалить [all v] из [x_позиции v]
задать [y_поз v] значение [-150]
+повторить (строки :: custom-arg) раз 
  задать [x_поз v] значение [-200]
  повторить (столбцы :: custom-arg) раз 
    добавить (x_поз) к [x_позиции v]
    добавить (y_поз) к [y_позиции v]
    изменить [x_поз v] на (((400) / (столбцы :: custom-arg)) - (1))
  end
end
```

\--- /task \---

Далее нужно увеличить значение `y_поз`{:class="block3variables"} каждый раз, когда запускается цикл `повторить (строки)`{:class="block3control"}.

Сделай это по аналогии с увеличением значения `x_поз`{:class="block3variables"} в цикле `повторить (столбцы)`{:class="block3control"}.

\--- task \---

В конце кода внутри цикла `повторить (строки)`{:class ="block3control"} `y_поз`{:class="block3variables"} должно увеличиться до `150`{:class="block3variables"}, что отличается на `300`{:class="block3variables"} от начального значения `-150`{:class="block3variables"}. Это нужно повторить для каждого ряда.

```blocks3
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
repeat (rows :: custom-arg)
set [x_pos v] to [-200]
repeat (columns :: custom-arg)
add (x_pos) to [x_positions v]
add (y_pos) to [y_positions v]
change [x_pos v] by (((400) / (columns :: custom-arg)) - (1))
end
+change [y_pos v] by (((300) / (rows :: custom-arg)) - (1))
end
```

\--- /task \---

\--- task \---

Убедись, что ты указал количество `строк`{:class="block3myblocks"} как входные данные для блоков.

```blocks3
when flag clicked
erase all
generate positions (4) (10) ::custom
stamp sprite (4) (10) ::custom
```

\--- /task \---

\--- task \---

Запусти свой код.

![беспорядок штампов](images/mess_stamps.png)

Ты не получишь аккуратную сетку печати.

Это потому, что сейчас блок `печатать спрайт`{:class="block3myblocks"} запускается только для общего числа столбцов.

\--- /task \---

\--- task \---

Измени свой скрипт `печатать спрайты`{:class="block3myblocks"}, так чтобы он `повторялся`{:class="block3control"} достаточно раз для печати полной сетки спрайтов.

\--- hints \--- \--- hint \---

Общее количество штампов, которое тебе нужно, это число, которое ты передаешь в `столбцы`{:class="block3myblocks"}, умноженное на число, которое ты передаешь в `строках`{:class="block3myblocks"}

\--- /hint \--- \--- hint \---

Используй этот дополнительный блок:

```blocks3
((rows ::custom) * (columns ::custom))
```

\--- /hint \--- \--- hint \---

Вот завершенный скрипт `печатать спрайты`{:class="block3myblocks"}:

```blocks3
define stamp sprites (rows) (columns)
set size to (40) %
+ repeat ((rows :: custom-arg) * (columns :: custom-arg))
set [index v] to (pick random (1) to (length of [x_positions v]))
go to x: (item (index) of [x_positions v]) y: (item (index) of [y_positions v]
delete (index) of [x_positions v]
delete (index) of [y_positions v]
stamp
next costume
```

\--- /hint \--- \--- /hints \---

![упорядоченная сетка](images/nice_grid.png)

\--- /task \---