## Ajouter des lignes

Maintenant que tu as le code pour créer une seule ligne de costumes estampillés, tu dois ajouter du code pour créer plus de lignes.

Va à ton bloc `générer les positions`{:class="block3myblocks"}.

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

Ajoute une autre boucle `répéter`{:class="block3control"} qui exécute le nombre de fois que tu donnes au bloc `générer les positions`{:class="block3myblocks"} en tant que `lignes`{:class="block3myblocks"}. Place la boucle `répéter`{:class="block3control"} dans ton script comme montré ici :

```blocks3
définir générer les positions (lignes)(colonnes)
supprimer [tout v] de [positions_y v]
supprimer [tout v] de [positions_x v]
mettre [pos_y v] à [-150]
+répéter (lignes :: custom-arg)
mettre [pos_x v] à [-200]
répéter (colonnes :: custom-arg)
ajouter (pos_x) à [positions_x v]
ajouter (pos_y) à [positions_y v]
ajouter (((400) / (colonnes :: custom-arg)) - (1)) à [pos_x v]
fin
fin
```

\--- /task \---

Ensuite, tu dois augmenter la valeur de `pos_y`{:class="block3variables"} à chaque fois que la boucle `répéter (lignes)`{:class="block3control"} s'exécute.

Fais pareil pour augmenter la valeur de `pos_x`{:class="block3variables"} dans la boucle `répéter (colonnes)`{:class="block3control"}.

\--- task \---

À la fin du code à l'intérieur de la boucle `répéter (lignes)`{:class="block3control"}, `pos_y`{:class="block3variables"} devrait augmenter jusqu'à `150`{:class="block3variables"}, qui est `300`{:class="block3variables"} plus loin de sa valeur de départ de `-150`{:class="block3variables"}. Cela doit se produire pour chaque lignes de tampons.

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

Assure-toi de donner le nombre de `lignes`{:class="block3myblocks"} comme entrée à tes blocs.

```blocks3
when flag clicked
erase all
generate positions (4) (10) ::custom
stamp sprite (4) (10) ::custom
```

\--- /task \---

\--- task \---

Exécute ton code maintenant.

![désordre de tampons](images/mess_stamps.png)

Tu n'auras pas de grille de tampons.

C'est parce que, pour l'instant, le bloc `estampiller`{:class="block3myblocks"} ne fonctionne que pour le nombre total de colonnes.

\--- /task \---

\--- task \---

Change ton script `estampiller`{:class="block3myblocks"} pour qu'il `répète`{:class="block3control"} assez de fois pour estampiller la grille complète de sprites.

\--- hints \--- \--- hint \---

Le nombre total de tampons dont tu as besoin est le nombre que tu donnes comme `colonnes`{:class="block3myblocks"} multiplié par le nombre que tu donnes comme `lignes`{:class="block3myblocks"}

\--- /hint \--- \--- hint \---

Utilise ce bloc supplémentaire :

```blocks3
((rows ::custom) * (columns ::custom))
```

\--- /hint \--- \--- hint \---

Voici le script `estampiller`{:class="block3myblocks"} terminé :

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

![grille ordonnée](images/nice_grid.png)

\--- /task \---