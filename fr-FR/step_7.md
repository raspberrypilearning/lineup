## Ajouter des lignes

Maintenant que tu as le code pour créer une seule ligne de costumes estampillés, tu dois ajouter du code pour créer plus de lignes.

Va à ton bloc `générer les positions`{:class="block3myblocks"}.

```blocks3
define générer les positions (lignes)(colonnes)
delete all of [positions_y v]
delete all of [positions_x v]
set [pos_y v] to [-150]
set [pos_x v] to [-200]
repeat (colonnes :: custom-arg)
add (pos_x) to [positions_x v]
add (pos_y) to [positions_y v]
change [pos_x v] by (((400) / (colonnes)) - (1))
```

--- task ---

Ajoute une autre boucle `répéter`{:class="block3control"} qui exécute le nombre de fois que tu donnes au bloc `générer les positions`{:class="block3myblocks"} en tant que `lignes`{:class="block3myblocks"}. Place la boucle `répéter`{:class="block3control"} dans ton script comme montré ici :

```blocks3
define générer les positions (lignes)(colonnes)
delete all of [positions_y v]
delete all of [positions_x v]
set [pos_y v] to [-150]
+repeat (lignes :: custom-arg)
set [pos_x v] to [-200]
repeat (colonnes :: custom-arg)
add (pos_x) to [positions_x v]
add (pos_y) to [positions_y v]
change [pos_x v] by (((400) / (colonnes :: custom-arg)) - (1))
end
end
```

--- /task ---

Ensuite, tu dois augmenter la valeur de `pos_y`{:class="block3variables"} à chaque fois que la boucle `répéter (lignes)`{:class="block3control"} s'exécute.

Fais pareil pour augmenter la valeur de `pos_x`{:class="block3variables"} dans la boucle `répéter (colonnes)`{:class="block3control"}.

--- task ---

À la fin du code à l'intérieur de la boucle `répéter (lignes)`{:class="block3control"}, `pos_y`{:class="block3variables"} devrait augmenter jusqu'à `150`{:class="block3variables"}, qui est `300`{:class="block3variables"} plus loin de sa valeur de départ de `-150`{:class="block3variables"}. Cela doit se produire pour chaque lignes de tampons.

```blocks3
define générer les positions (lignes)(colonnes)
delete all of [positions_y v]
delete all of [positions_x v]
set [pos_y v] to [-150]
repeat (lignes :: custom-arg)
set [pos_x v] to [-200]
repeat (colonnes :: custom-arg)
add (pos_x) to [positions_x v]
add (pos_y) to [positions_y v]
change [pos_x v] by (((400) / (colonnes :: custom-arg)) - (1))
end
+change [pos_y v] by (((300) / (lignes :: custom-arg)) - (1))
end
```

--- /task ---

--- task ---

Assure-toi de donner le nombre de `lignes`{:class="block3myblocks"} comme entrée à tes blocs.

```blocks3
when flag clicked
erase all
générer les positions (4) (10) ::custom
estampiller les sprites(4) (10) ::custom
```

--- /task ---

--- task ---

Exécute ton code maintenant.

![désordre de tampons](images/mess_stamps.png)

Tu n'auras pas de grille de tampons.

C'est parce que, pour l'instant, le bloc `estampiller`{:class="block3myblocks"} ne fonctionne que pour le nombre total de colonnes.

--- /task ---

--- task ---

Change ton script `estampiller`{:class="block3myblocks"} pour qu'il `répète`{:class="block3control"} assez de fois pour estampiller la grille complète de sprites.

--- hints ---
 --- hint ---

Le nombre total de tampons dont tu as besoin est le nombre que tu donnes comme `colonnes`{:class="block3myblocks"} multiplié par le nombre que tu donnes comme `lignes`{:class="block3myblocks"}

--- /hint --- --- hint ---

Utilise ce bloc supplémentaire :

```blocks3
((lignes ::custom) * (colonnes ::custom))
```

--- /hint --- --- hint ---

Voici le script `estampiller`{:class="block3myblocks"} terminé :

```blocks3
define estampiller les sprites (lignes) (colonnes)
set size to (40) %
+ repeat ((lignes :: custom-arg) * (colonnes :: custom-arg))
set [index v] to (pick random (1) to (length of [positions_x v]))
go to x: (item (index) of [positions_x v]) y: (item (index) of [positions_y v]
delete (index) of [positions_x v]
delete (index) of [positions_y v]
stamp
next costume
```

--- /hint ------ /hints ---

![grille ordonnée](images/nice_grid.png)

--- /task ---