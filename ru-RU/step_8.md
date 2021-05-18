## Скрой свой спрайт

Теперь пришло время спрятать свой спрайт среди множества штампов. На данный момент спрайт перекрывает один из штампов.

![перекрытие](images/overplap-annotated.png)

\--- task \---

Чтобы это не происходило, сделай так, чтобы твой цикл печати выполнялся на один раз меньше: `(строки * столбцы) - 1`{:class="block3operators"}

```blocks3
define stamp sprites (rows) (columns)
set size to (40) %
+repeat (((rows :: custom-arg) * (columns :: custom-arg)) - (1))
set [index v] to (pick random (1) to (length of [x_positions v]))
go to x: (item (index) of [x_positions v]) y: (item (index) of [y_positions v]
delete (index) of [x_positions v]
delete (index) of [y_positions v]
stamp
next costume
```

\--- /task \---

Если ты запустишь скрипт сейчас, то увидишь, что спрайт все еще перекрывается штампом, и в сетке есть дыра. И в списках `x_позиции`{:class="block3variables"} и `y_позиции`{:class="block3variables"} осталась одна координата.

\--- task \---

Чтобы закончить эту часть игры, перейди к разделу скриптов `когда флаг нажат`{:class="block3events"}.

```blocks3
when flag clicked
erase all
generate positions (4) (10) ::custom
stamp sprites (4) (10) ::custom
```

\--- no-print \---

Вот анимация, показывающая, что должно произойти:

![анимация](images/demo_1.gif)

\--- /no-print \---

В начале игры спрайт должен появиться в большом размере и сказать «Найди меня». Затем спрайт должен спрятаться среди штампов в оставленном тобой пустом месте.

Попробуй сам выяснить, как это сделать, и воспользуйтесь советами ниже, если понадобится помощь.

\--- hints \--- \--- hint \---

Вот, что тебе нужно сделать:

1. Отправь свой спрайт в `x:0 y:0`{:class="block3motion"}
2. Выведи спрайт `вперед`{:class="block3looks"} и установи его `размер в 100%`{:class="block3looks"}
3. `Говорить «Найди меня» в течение двух секунд`{:class= "block3looks"}
4. `Вернуться назад на один слой`{:class="block3looks"}
5. Установи `размер в 40%`{:class="block3looks"}
6. Перейди к последней оставшейся позиции в списках

\--- /hint \--- \--- hint \---

Вот дополнительные блоки кода, которые тебе нужны:

```blocks3
when flag clicked
erase all
generate positions (4) (10) ::custom
stamp sprites (4) (10) ::custom

go to x: (0) y: (0)

go [backward v] (1) layers

go to [front v] layer

set size to (100) %

set size to (40) %

say [] for (2) seconds
item (1 v) of [x_positions v]
item (1 v) of [y_positions v]
go to x: () y: ()
```

\--- /hint \--- \--- hint \---

Вот завершенный скрипт `когда флаг нажат`{:class="block3myblocks"}:

```blocks3
when flag clicked
erase all
generate positions (4) (10) ::custom
stamp sprites (4) (10) ::custom
+go to x: (0) y: (0)
+go to [front v] layer
+set size to (100) %
+say [Find me] for (2) seconds
+go [backward v] (1) layers
+set size to (40) %
+ go to x: (item (1 v) of [x_positions v]) y: (item (1 v) of [y_positions v])
```

\--- /hint \--- \--- /hints \--- \--- /task \---