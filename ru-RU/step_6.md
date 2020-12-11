## Измени костюмы

В настоящий момент твоя программа снова и снова печатает один и тот же костюм спрайта, а размер костюма слишком велик.

--- task ---

Добавь код блоку `печатать спрайты`{:class="block3myblocks"}, который сделает спрайт подходящего размера, до того, как начнется цикл`повторить`{:class="block3control"}. Добавь блок в цикл, чтобы переключить `следующий костюм`{:class="block3looks"} после блока `печать`{:class="block3extensions"}.

```blocks3
define печатать спрайты (строки) (столбцы)
set size to (40) %
set [индекс v] to [1]
repeat (столбцы :: custom-arg)
go to x: (item (индекс) of [x_позиции v]) y: (item (индекс) of [y_позиции v]
stamp
next costume
change [индекс v] by (1)
```

--- /task ---

Когда ты запустишь скрипт сейчас, то увидишь что-то вроде этого:

![измененные_спрайты](images/changed_sprites.png)

Твоя программа переключает все костюмы по порядку. Чтобы каждый костюм не появлялся в одном и том же месте при каждом запуске программы, ты должен отпечатать спрайт в случайных местах на сетке.

Для этого тебе нужно следовать этому **алгоритму**:

1. `Повторить`{:class="block3control"}, пока список не станет пустым
2. Установить `индексу`{:class="block3variables"} `случайное`{:class="block3operators"} число между `1` и длиной списка
3. Перемести спрайт, как ты делал раньше
4. Удали элемент в позиции `индекс`{:class="block3variables"} из списка `y_позиции`{:class="block3variables"}
5. Удали элемент в позиции `индекс`{:class="block3variables"} из списка `x_позиции`{:class="block3variables"}

--- task ---

Добавь код, чтобы отпечатать спрайт в случайных местах на сетке.

--- hints ---
 --- hint ---

Удали `установить индекс в 1`{:class="block3variables"} до цикла `повторить`{:class="block3control"}.

Затем в цикле `установить индекс в`{:class="block3variables"} `случайное`{:class="block3operators"} число от `1` до `длина x_позиции`{:class="block3variables"}.

Затем `удали`{:class="block3variables"} элемент в позиции `индекс`{:class="block3variables"} из обоих списков `x_позиции`{:class="block3variables"} и `y_позиции`{:class="block3variables"}.

--- /hint --- --- hint ---

Вот дополнительные блоки кода, которые тебе нужны:

```blocks3
define печатать спрайты (строки) (столбцы)
set size to (40) %
- set [индекс v] to [1]
repeat (столбцы :: custom-arg)
go to x: (item (индекс) of [x_позиции v]) y: (item (индекс) of [y_позиции v]
stamp
next costume
- change [индекс v] by (1)
end

set [индекс v] to ()
(pick random () to ()
length of [x_позиции v]
delete () of [x_позиции v]

delete () of [y_позиции v]
(индекс)
(индекс)
```

--- /hint --- --- hint ---

Так должен выглядеть твой код:

```blocks3
define печатать спрайты (строки) (столбцы)
set size to (40) %
- set [индекс v] to [1]
repeat (столбцы :: custom-arg)
+ set [индекс v] to (pick random (1) to (length of [x_позиции v]))
go to x: (item (индекс) of [x_позиции v]) y: (item (индекс) of [y_позиции v]
+ delete (индекс) of [x_позиции v]
+ delete (индекс) of [y_позиции v]
stamp
next costume
- change [индекс v] by (1)
```

--- /hint ------ /hints --- --- /task ---