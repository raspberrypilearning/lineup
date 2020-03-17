## Verander de uiterlijken

Op dit moment stempelt je programma steeds hetzelfde sprite uiterlijk en is het uiterlijk te groot.

\--- task \---

Voeg code toe aan het `stempel sprites`{:class="block3myblocks"} blok om de sprite een geschikte grootte te geven voordat de `herhaal`{:class="block3control"} lus start. Voeg een blok in de lus toe om naar het volgende `uiterlijk`{:class="block3looks"} te schakelen na het `stempel`{:class="block3extensions"} blok.

```blocks3
definiëer stempels (rijen) (kolommen)
maak grootte (40) %
maak [index v] [1]
herhaal (kolommen :: custom-arg)
ga naar x: (item (index) van [x_posities v] ) y: (item (index) van [y_posities v]
stempel
volgend uiterlijk
verander [index v] met (1)
```

\--- /task \---

Wanneer je het script nu uitvoert, zou je zoiets moeten zien:

![veranderde sprites](images/changed_sprites.png)

Je programma doorloopt alle uiterlijken op volgorde. Om ervoor te zorgen dat elk uiterlijk niet op dezelfde plaats verschijnt telkens wanneer het programma wordt uitgevoerd, moet je de sprite op willekeurige plaatsen in het raster stempelen.

Om dit te doen, moet je dit **algoritme** volgen:

1. `Herhaal`{:class="block3control"} totdat de lijst leeg is
2. Stel `index`{:class="block3variables"} in op een `willekeurig`{:class="block3operators"} getal tussen `1` en de lengte van een lijst
3. Verplaats de sprite zoals eerder
4. Verwijder het item op positie `index`{:class="block3variables"} uit de lijst `y_posities`{:class="block3variables"}
5. Verwijder het item op positie `index`{:class="block3variables"} uit de lijst `x_posities`{:class="block3variables"}

\--- task \---

Voeg code toe om de sprite op willekeurige plaatsen in het raster te stempelen.

\--- hints \--- \--- hint \---

Verwijder de `maak index 1`{:class="block3variables"} van vóór de `herhaal`{:class="block3control"} lus.

Stel vervolgens binnen de lus `de index in op`{:class="block3variables"} een `willekeurig`{:class="block3operators"} getal tussen `1` en de `lengte van x_posities`{:class="block3variables"}.

`Verwijder`{:class="block3variables"} vervolgens het item op de `index`{:class="block3variables"} uit zowel de `x_posities`{:class="block3variables"} als `y_posities`{:class=" block3variables"} lijsten.

\--- /hint \--- \--- hint \---

Dit zijn de extra blokken die je nodig hebt:

```blocks3
definieer stempel sprites (rijen) (kolommen)
maak grootte (40) %
- maak [index v] [1]
herhaal (kolommen :: custom-arg)
ga naar x: (item (index) van [x_posities v ]) y: (item (index) van [y_posities v]
stempel
volgend uiterlijk
- verander [index v] met (1)
einde

maak [index v] ()
(willekeurig getal tussen () en ()
lengte van [x_posities v]
verwijder () van [x_posities v]

verwijder () van [y_posities v]
(index)
(index)
```

\--- /hint \--- \--- hint \---

Dit is hoe je code eruit zou moeten zien:

```blocks3
definieer stempel sprites (rijen) (kolommen)
maak grootte (40) %
- maak [index v] [1]
herhaal (kolommen :: custom-arg)
+ maak [index v] (willekeurig getal tussen (1) en (lengte van [x_posities v]))
ga naar x: (item (index) van [x_posities v]) y: (item (index) van [y_posities v]
+ verwijder (index) van [x_posities v]
+ verwijder (index) van [y_posities v]
stempel
volgend uiterlijk
- verander [index v] met (1)
```

\--- /hint \--- \--- /hints \--- \--- /task \---