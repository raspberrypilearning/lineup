## Créer une grille

Tu vas créer une grille de costumes estampillés :

![tampons dans la grille](images/stamp_grid.png)

Pour faire cela, tu dois connaître les coordonnées `x`{:class="block3motion"} et `y`{:class="block3motion"} où chaque tampon doit être placé.

\--- task \---

Tout d'abord, crée un nouveau bloc appelé `générer les positions`{:class="block3myblocks"}. Le bloc doit avoir deux paramètres d'entrée « nombre ». Appelle les deux paramètres `lignes`{:class="block3myblocks"} et `colonnes`{:class="block3myblocks"}.

Les valeurs de ces paramètres décideront du nombre de lignes et de colonnes que ta grille possède.

[[[generic-scratch3-make-block]]]

```blocks3
define generate positions (rows)(columns)
```

\--- /task \---

\--- task \---

Crée deux listes, et appelle l'une d'entre elles `positions_x`{:class="block3variables"} et l'autre `positions_y`{:class="block3variables"}. Ces listes servent à stocker les coordonnées `x`{:class="block3motion"} et `y`{:class="block3motion"} pour les tampons.

\--- /task \---

\--- task \---

Dans ton bloc `générer les positions`{:class="block3myblocks"}, ajoute des blocs pour supprimer tous les éléments des deux listes, de sorte que chaque fois que le jeu démarre, les listes sont vides.

```blocks3
define generate positions (rows)(columns)
+ delete [all v] of [y_positions v]
+ delete [all v] of [x_positions v]
```

\--- /task \---

\--- task \---

Ensuite, crée deux variables, et appelle l'une d'entre elles `pos_x`{:class="block3variables"} et l'autre `pos_y`{:class="block3variables"}.

\--- /task \---

La liste `positions_x`{:class="block3variables"} doit contenir dix nombres au total, et ceux-ci doivent commencer à `-200`{:class="block3variables"} et aller jusqu'à `200`{:class="block3variables"}.

Pour l'instant, la liste `positions_y`{:class="block3variables"} peut juste contenir le nombre `-150`{:class="block3variables"} dix fois, de sorte que la grille n'ait qu'une seule ligne.

\--- task \---

Commence par ajouter du code à la variable `générer les positions`{:class="block3myblocks"} pour définir la variable `pos_y`{:class="block3variables"} à `-150`{:class="block3variables"} et la variable `pos_x`{:class="block3variables"} à `-200`{:class="block3variables"}. C'est l'emplacement du premier sprite estampillé.

```blocks3
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
+ set [y_pos v] to [-150]
+ set [x_pos v] to [-200]
```

\--- /task \---

\--- task \---

Ensuite, ajoute une boucle `répéter`{:class="block3control"} pour mettre les coordonnées dans les listes.

La boucle `répéter`{:class="block3control"} doit s'exécuter une fois pour chaque colonne que tu veux que la grille ait.

Le bloc `générer les positions`{:class="block3myblocks"} prend `colonnes`{:class="block3myblocks"} comme entrée, donc tu peux utiliser `colonnes`{:class="block3myblocks"} pour la boucle `répéter`{:class="block3control"}.

```blocks3
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
set [x_pos v] to [-200]
+ repeat (columns :: custom-arg)
```

\--- /task \---

Dans la boucle `répéter`{:class="block3control"}, ajoute les valeurs de `pos_x`{:class="block3variables"} et `pos_y`{:class="block3variables"} dans les listes. Ensuite, tu dois augmenter un peu la valeur de `pos_x`{:class="block3variables"}. Combien devrait augmenter la valeur de `pos_x`{:class="block3variables"} ?

Voici comment faire :

- `pos_x`{:class="block3variables"} commence avec la valeur `-200`{:class="block3variables"}
- La dernière fois que la boucle `répéter`{:class="block3control"} s'exécute, `pos_x`{:class="block3variables"} devrait atteindre la valeur `200`{:class="block3variables"}
- C'est une augmentation totale de `400`{:class="block3variables"}
- La première valeur `pos_x`{: class = "block3variables"} correspond à la première colonne de la grille, et le nombre de colonnes est déterminé par l'entrée `colonnes`{:class="block3myblocks"}

Donc, après que la première valeur `pos_x`{:class="block3variables"} est ajoutée, à chaque tour de boucle, la valeur de `pos_x`{:class="block3variables"} devrait augmenter de `400 / (colonnes - 1)`{:class="block3operators"}

\--- task \---

Ajoute dans le code qui ajoutera toutes les valeurs `pos_x`{:class="block3variables"} et `pos_y`{:class="block3variables"} dans les listes `positions_x`{:class="block3variables"} et `positions_y`{:class="block3variables"}.

\--- hints \--- \--- hint \---

Dans la boucle, tu dois ajouter `pos_x`{:class="block3variables"} à la liste `positions_x`{:class="block3variables"} et ajoute la liste `pos_y`{:class="block3variables"} à la liste `positions_y`{:class="block3variables"}. Ensuite, la variable `pos_x`{:class="block3variables"} doit augmenter de `400 / (colonnes -1)`{:class="block3operators"} chaque fois que la boucle se répète.

\--- /hint \--- \--- hint \---

Cela montre les blocs supplémentaires que tu dois ajouter à ton script.

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

Voici le script terminé pour le bloc `générer les positions`{:class="block3myblocks"} :

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