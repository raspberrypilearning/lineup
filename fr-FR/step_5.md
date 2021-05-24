## Estampiller une ligne

Jusqu'à présent, tu as dix valeurs dans chacune des deux listes. Maintenant estampille certains costumes aux coordonnées de la scène stockées dans les listes.

--- task ---

Ajoute l'extension **Stylo** à ton projet.

[[[generic-scratch3-add-pen-extension]]]

--- /task ---

--- task ---

Crée un nouveau bloc et appelle-le `estampiller les sprites`{:class="block3myblocks"}. Ce bloc a besoin de deux nombres d'entrées nommés `lignes`{:class="block3myblocks"} et `colonnes`{:class="block3myblocks"} comme l'autre bloc personnalisé.

```blocks3
define estampiller les sprites (lignes) (colonnes)
```

--- /task ---

--- task ---

Crée une nouvelle variable appelée `index`{:class="block3variables"} avec laquelle tu pourras suivre la position dans les listes que ton programme est en train de lire. Pour commencer, définis `index`{:class="block3variables"} à `1`{:class="block3variables"} pour récupérer le premier élément de chaque liste.

```blocks3
define estampiller les sprites (lignes) (colonnes)
+ set [index v] to [1]
```

--- /task ---

--- task ---

Le bloc `estampiller les sprites`{:class="block3myblocks"} doit estampiller un sprite pour chaque paire de coordonnées dans la liste. Pour cela, le bloc a besoin d'une boucle `répéter`{:class="block3variables"} qui s'exécute une fois pour chaque colonne.

```blocks3
define estampiller les sprites (lignes) (colonnes)
set [index v] to [1]
+ repeat (colonnes :: custom-arg)
```

--- /task ---

--- task ---

Dans la boucle `répéter`{:class="block3variables"} :

- Déplace le sprite à la position `index`{:class="block3variables"} dans les listes `positions_x`{:class="block3variables"} et `positions_y`{:class="block3variables"}
- `Estampille`{:class="block3extensions"} le sprite
- Change l'`index`{:class="block3variables"} par `1`{:class="block3variables"}

--- hints ---
 --- hint ---

Dans la boucle `répéter`{:class="block3variables"}, ajoute un bloc `aller à x: y:`{:class="block3motion"}. La position `x`{:class="block3motion"} dans ce bloc doit être réglée sur l'`index`{:class="block3variables"} de `positions_x`{:class="block3variables"} et la position `y`{:class="block3motion"} doit être définie sur l'`index`{:class="block3variables"} de `positions_y`{:class="block3variables"}. Ajoute ensuite du code pour `estampiller`{:class="block3extensions"} le sprite. Enfin, ajoute du code pour augmenter l'`index`{:class="block3variables"} de 1.

--- /hint --- --- hint ---

Voici les blocs dont tu as besoin :

```blocks3
define estampiller les sprites (lignes) (colonnes)
set [index v] to [1]
repeat (colonnes :: custom-arg)
end

change [index v] by (1)
(index) 
(index) 
go to x: () y: ()
(item ()of [positions_y v])
(item ()of [positions_x v])
stamp
```

--- /hint --- --- hint ---

Voici le script terminé pour le bloc `estampiller les sprites`{:class="block3myblocks"} :

```blocks3
define estampiller les sprites (lignes) (colonnes)
set [index v] to [1]
repeat (colonnes :: custom-arg)
+ go to x: (item (index) of [positions_x v]) y: (item (index) of [positions_y v]
+ stamp
+ change [index v] by (1)
```

--- /hint ------ /hints --- --- /task ---

--- task ---

Ajoute un bloc `effacer tout`{:class="block3extensions"} en dessous du bloc `quand le drapeau vert est cliqué`{:class="block3control"} pour effacer la scène chaque fois que le jeu commence. Ajoute ensuite le bloc `estampiller les sprites`{:class="block3myblocks"} en bas du script `quand le drapeau vert est cliqué`{:class="block3control"} pour tester ton nouveau code.

```blocks3
when flag clicked
erase all
générer les positions (1) (10) ::custom
estampiller les sprites (1) (10) ::custom
```

--- /task ---

--- task ---

Clique sur le drapeau vert. Tu devrais voir quelque chose comme ça, selon les costumes que ton sprite a :

![sprites estampillés](images/stamped_sprites.png)

--- /task ---