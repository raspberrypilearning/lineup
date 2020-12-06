## Создай сетку

Мы создадим сетку отпечатанных костюмов:

![штампы в сетке](images/stamp_grid.png)

Для этого тебе нужно знать `х`{:class="block3motion"} и `y`{:class="block3motion"} координаты места, где должна быть размещена каждая печать.

\--- task \---

Сначала создай новый блок с именем `генерировать позиции`{:class="block3myblocks"}. Блок должен иметь два параметра «числовых входных» параметров. Назови эти два параметра `строки`{:class="block3myblocks"} и `столбцы`{:class="block3myblocks"}.

Значения этих параметров будут определять количество строк и столбцов в твоей сетке.

[[[generic-scratch3-make-block]]]

```blocks3
define generate positions (rows)(columns)
```

\--- /task \---

\--- task \---

Создай два новых списка с именами `x_позиции`{:class="block3variables"} и `y_позиции`{:class="block3variables"}. Эти списки нужны для хранения `x`{:class="block3motion"} и `y`{:class="block3motion"} координат штампов.

\--- /task \---

\--- task \---

Добавь блоку `генерировать позиции`{:class="block3myblocks"} блоки, удаляющие все элементы из обоих списков, чтобы при каждом запуске игры списки были пустыми.

```blocks3
define generate positions (rows)(columns)
+ delete [all v] of [y_positions v]
+ delete [all v] of [x_positions v]
```

\--- /task \---

\--- task \---

Далее создай две переменные с именами `x_поз`{:class="block3variables"} и `y_поз`{:class="block3variables"}.

\--- /task \---

Список `x_позиции`{:class="block3variables"} должен содержать десять чисел, и они должны начинаться с `-200`{:class="block3variables"} и заканчиваться `200`{:class="block3variables"}.

На данный момент, список `y_positions`{:class="block3variables"} может содержать число `-150`{:class="block3variables"} десять раз, чтобы сетка имела только одну строку.

\--- task \---

Начни с того, что добавь код в блок `генерировать позиции`{:class="block3myblocks"}, чтобы установить переменной `y_поз`{:class="block3variables"} значение `-150`{:class="block3variables"} и переменной`x_поз`{:class="block3variables"} значение `-200`{:class="block3variables"}. Это место расположения первого штампа спрайта.

```blocks3
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
+ set [y_pos v] to [-150]
+ set [x_pos v] to [-200]
```

\--- /task \---

\--- task \---

Затем добавь цикл `повторить`{:class="block3control"}, чтобы определить координаты в списки.

Цикл `повторить`{:class="block3control"} должен выполняться один раз для каждого столбца в сетке.

Блок `генерировать позиции`{:class="block3myblocks"} принимает `столбцы`{:class="block3myblocks"} в качестве входных данных, поэтому ты можеш использовать `столбцы`{:class="block3myblocks"} для цикла `повторить`{:class="block3control"}.

```blocks3
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
set [x_pos v] to [-200]
+ repeat (columns :: custom-arg)
```

\--- /task \---

В пределах цикла `повторить`{:class="block3control"}, добавь значения `x_поз`{:class="block3variables"} и `y_поз`{:class="block3variables"} в списки. Затем тебе нужно немного увеличить значение ` x_поз`{:class="block3variables"}. На сколько стоит увеличить значение `x_поз`{:class="block3variables"}?

Вот как мы это рассчитаем:

- `x_поз`{:class="block3variables"} начинается со значения `-200`{:class= "block3variables"}
- Когда цикл `повторить`{:class="block3control"} выполняется в последний раз, `x_поз`{:class="block3variables"} должно достичь значения `200`{:class="block3variables"}
- То есть всего увеличивается на `400`{:class="block3variables"}
- Первое значение ` x_поз`{:class="block3variables"} предназначено для первого столбца в сетке, а количество столбцов определяется значением `столбцы`{:class="block3myblocks"}

Итак, после добавления первого значения `x_поз`{:class = "block3variables"}, при каждом цикле значение `x_поз`{:class="block3variables"} должно увеличиться на `400 / (столбцы - 1)`{:class="block3operators"}

\--- task \---

Добавь код, который добавит все значения `x_поз`{:class="block3variables"} и `y_поз`{:class="block3variables"} в списки `x_позиции`{:class="block3variables"} и `y_позиции`{:class="block3variables"}.

\--- hints \--- \--- hint \---

В цикле тебе нужно добавить `x_поз`{:class="block3variables"} в список `x_позиции`{:class="block3variables"} и добавить `y_поз`{:class="block3variables"} в список `y_позиции`{:class="block3variables"}. Тогда переменная `x_поз`{:class="block3variables"} должна быть увеличена на `400 / (столбцы -1)`{:class="block3operators"} каждый раз, когда цикл повторяется.

\--- /hint \--- \--- hint \---

Здесь показаны дополнительные блоки, которые тебе нужно добавить в скрипт.

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

Вот завершенный скрипт для блока`генерировать позиции`{:class="block3myblocks"}:

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