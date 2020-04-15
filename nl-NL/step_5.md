## Stempel een rij

Tot nu toe heb je tien waarden in elk van de twee lijsten. Stempel nu enkele uiterlijken bij de speelveld coördinaten die in de lijsten zijn opgeslagen.

--- task ---

Voeg de **Pen** extensie toe aan je project.

[[[generic-scratch3-add-pen-extension]]]

--- /task ---

--- task ---

Maak een nieuw blok en noem het `stempel sprites`{:class="block3myblocks"}. Dit blok heeft twee invoeren nodig met de naam `rijen`{:class="block3myblocks"} en `kolommen`{:class="block3myblocks"} net als het andere aangepaste blok.

```blocks3
defineer stempel sprites (rijen) (kolommen)
```

--- /task ---

--- task ---

Maak een nieuwe variabele met de naam `index`{:class="block3variables"} waarmee je de positie kunt volgen in de lijsten die je programma aan het lezen is. Stel om te beginnen `index`{:class="block3variables"} in op `1`{:class="block3variables"} om het eerste item van elke lijst op te halen.

```blocks3
definieer stempel sprites (rijen) (kolommen)
+ maak [index v] [1]
```

--- /task ---

--- task ---

Het blok `stempel sprites`{:class="block3myblocks"} moet een sprite stempelen voor elk paar coördinaten in de lijst. Om dit te doen, heeft het blok een `herhaal`{:class="block3variables"} lus nodig die éénmaal voor elke kolom wordt uitgevoerd.

```blocks3
definieer stempel sprites (rijen) (kolommen)
maak [index v] [1]
+ herhaal (kolommen :: custom-arg)
```

--- /task ---

--- task ---

Binnen de lus `herhaal`{:class="block3variables"}:

- Verplaats de sprite naar de `index`{:class="block3variables"} positie in de `x_posities`{:class="block3variables"} en `y_posities`{:class="block3variables"}
- `Stempel`{:class="block3extensions"} de sprite
- Verander `index`{:class="block3variables"} met `1`{:class="block3variables"}

--- hints ---
 --- hint ---

Voeg in de lus `herhaal`{:class="block3variables"} een `ga naar x: y:`{:class="block3motion"} blok toe. De positie `x`{:class="block3motion"} in dit blok moet worden ingesteld op de `index`{:class="block3variables"} van `x_posities`{:class="block3variables"} en de `y`{:class="block3motion"} positie moet worden ingesteld op `index`{:class="block3variables"} van `y_posities`{:class="block3variables"}. Voeg vervolgens code toe aan `stempel sprites`{:class="block3extensions"}. Voeg ten slotte code toe om `index`{:class="block3variables"} met 1 te verhogen.

--- /hint --- --- hint ---

Dit zijn de blokken die je nodig hebt:

```blocks3
definieer stempel sprites (rijen) (kolommen)
maak [index v] [1]
herhaal (kolommen :: custom-arg)
einde

verander [index v] met (1)
(index) 
(index) 
ga naar x: () y: ()
(item () van [y_posities v])
(item () van [x_posities v])
stempel
```

--- /hint --- --- hint ---

Hier is het voltooide script voor het `stempel sprites`{:class="block3myblocks"} blok:

```blocks3
definieer stempel sprites (rijen) (kolommen)
maak [index v] [1]
herhaal (kolommen :: custom-arg)
+ ga naar x: (item (index) van [x_posities v]) y: (item (index ) van [y_posities v]
+ stempel
+ verander [index v] met (1)
```

--- /hint ------ /hints --- --- /task ---

--- task ---

Voeg een `wis alles`{:class="block3extensions"} blok onder het `wanneer op de groene vlag wordt geklikt`{:class="block3control"} blok om het speelveld te wissen telkens wanneer het spel start. Voeg vervolgens het `stempel sprites`{:class="block3myblocks"} blok onder aan het `wanneer op de groene vlag wordt geklikt`{:class="block3control"} script toe, zodat je je nieuwe code kunt testen.

```blocks3
wanneer op de groene vlag wordt geklikt
wis alles
genereer posities (1) (10) ::custom
stempel sprites (1) (10) ::custom
```

--- /task ---

--- task ---

Klik op de groene vlag. Je zou zoiets moeten zien, afhankelijk van de uiterlijken die je sprite heeft:

![gestempelde sprites](images/stamped_sprites.png)

--- /task ---