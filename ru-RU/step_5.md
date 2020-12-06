## Штамп строки

На данный момент у тебя есть десять значений в каждом из двух списков. Теперь пропечатай некоторые костюмы на координатах Сцены, сохраненных в списках.

\--- task \---

Добавь расширение **Перо** в твой проект.

[[[generic-scratch3-add-pen-extension]]]

\--- /task \---

\--- task \---

Создай новый пользовательский блок и назови его `печатать спрайты`{:class="block3myblocks"}. Этому блоку нужно добавить два числовых ввода с именами `строки`{:class="block3myblocks"} и `столбцы`{:class="block3myblocks"}, как и предыдущему пользовательскому блоку.

```blocks3
define stamp sprites (rows) (columns)
```

\--- /task \---

\--- task \---

Создай новую переменную с именем `индекс`{:class="block3variables"}, с помощью которой можно отслеживать позицию в списках, которые читает ваша программа. Для начала установи `индексу`{:class="block3variables"} значение `1`{:class="block3variables"}, чтобы получить первый элемент каждого списка.

```blocks3
define stamp sprites (rows) (columns)
+ set [index v] to [1]
```

\--- /task \---

\--- task \---

Блок `печатать спрайты`{:class="blockmyblocks"} должен печатать спрайт для каждой пары координат в списке. Для этого блоку нужен цикл `повторить`{:class="block3variables"}, который запускается один раз для каждого столбца.

```blocks3
define stamp sprites (rows) (columns)
set [index v] to [1]
+ repeat (columns :: custom-arg)
```

\--- /task \---

\--- task \---

В пределах цикла `печатать`{:class="block3variables"}:

- Перемести спрайт в позицию `индекс`{:class="block3variables"} в списки `x_позиции`{:class="block3variables"} и `y_позиции`{:class="block3variables"}
- `Печатай`{:class="block3extensions"} спрайт
- Измени `индекс`{:class="block3variables"} на `1`{:class="block3variables"}

\--- hints \--- \--- hint \---

В пределах цикла `повторить`{:class="block3variables"} добавь блок `перейти к x: y: `{:class="block3motion"}. Позиция `х`{:class="block3motion"} в этом блоке должна быть определена в `индекс`{:class="block3variables"} из `x_позиций`{:class="block3variables"} и `y`{:class="block3motion"} позиция должна быть установлена в `индекс`{:class="block3variables"} из `y_позиции`{:class="block3variables"}. Затем добавь код в спрайт `печатать`{:class="block3extensions"}. Наконец, добавь код для увеличения `индекса`{:class="block3variables"} на 1.

\--- /hint \--- \--- hint \---

Вот блоки, которые тебе понадобятся:

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

Вот завершенный скрипт для блока `печатать спрайты`{:class="block3myblocks"}:

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

Добавь блок `стереть все`{:class="block3extensions"} чуть ниже блока `когда флаг нажат`{:class="block3control"}, чтобы чистить сцену при каждом запуске игры. Затем добавь блок `печатать спрайты`{:class="block3myblocks"} в нижней часть скрипта `когда флаг нажат`{:class="block3control"}, чтобы можно было проверить свой новый код.

```blocks3
when flag clicked
erase all
generate positions (1) (10) ::custom
stamp sprite (1) (10) ::custom
```

\--- /task \---

\--- task \---

Нажми на зеленый флаг. Ты должен увидеть что-то вроде этого, в зависимости от костюмов твоего спрайта:

![отпечатанные спрайты](images/stamped_sprites.png)

\--- /task \---