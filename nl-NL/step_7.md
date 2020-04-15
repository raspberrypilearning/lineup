## Rijen toevoegen

Nu je de code hebt om een enkele rij met gestempelde uiterlijken te maken, moet je code toevoegen om meer rijen te maken.

Ga naar je `genereer posities`{:class="block3myblocks"} blok.

```blocks3
define genereer posities (rijen) (kolommen)
verwijder [alle v] van [y_posities v]
verwijder [alle v] van [x_posities v]
maak [y_pos v] [-150]
maak [x_pos v] [-200]
herhaal (kolommen :: custom-arg)
voeg (x_pos) toe aan [x_posities v]
voeg (y_pos) toe aan [y_posities v]
verander [x_pos v] met (((400) / (kolommen :: custom-arg)) - (1))
```

--- task ---

Voeg nog een `herhaal`{:class="block3control"} lus toe, die het aantal keren uitvoert dat je geeft aan de `genereer posities`{:class="block3myblocks"} blok als de `rijen`{:class="block3myblocks"} invoer. Plaats de `herhaal`{:class="block3control"} lus in je script zoals hier wordt weergegeven:

```blocks3
define genereer posities (rijen) (kolommen)
delete [alle v] of [y_posities v]
delete [alle v] of [x_posities v]
set [y_pos v] to [-150]
+repeat (rijen :: custom-arg)
set [x_pos v] to [-200]
repeat (kolommen :: custom-arg)
add (x_pos) to [x_posities v]
add (y_pos) to [y_posities v]
change [x_pos v] by (((400) / (kolommen :: custom-arg)) - (1))
end
end
```

--- /task ---

Vervolgens moet je de waarde van `y_pos`{:class="block3variables"} verhogen telkens wanneer de `herhaal (rijen)`{:class="block3control"} lus wordt uitgevoerd.

Je doet dit op dezelfde manier als hoe je de waarde van `x_pos`{:class="block3variables"} verhoogt in de lus `herhaal (kolommen)`{:class="block3control"}.

--- task ---

Aan het einde van de code binnen de `herhaal (rijen)`{:class="block3control"} lus, moet de `y_pos`{:class="block3variables"} oplopen tot `150`{:class="block3variables"}, dat is `300`{:class="block3variables"} verwijderd van de startwaarde van `-150`{:class="block3variables"}. Dit moet gebeuren voor elke rij stempels.

```blocks3
define genereer posities (rijen) (kolommen)
verwijder [alle v] van [y_posities v]
verwijder [alle v] van [x_posities v]
maak [y_pos v] [-150]
herhaal (rijen: custom-arg)
maak [x_pos v] [-200]
herhaal (kolommen :: custom-arg)
voeg (x_pos) toe aan [x_posities v]
voeg (y_pos) toe aan [y_posities v]
verander [x_pos v] met (((400) / (kolommen :: custom-arg)) - (1))
einde
+ verander [y_pos v] met (((300) / (rijen :: custom-arg)) - (1))
einde
```

--- /task ---

--- task ---

Zorg ervoor dat je het aantal `rijen`{:class="block3myblocks"} opgeeft als invoer voor je blokken.

```blocks3
when flag clicked
wis alles
genereer posities (4) (10) ::custom
stempel sprite (4) (10) ::custom
```

--- /task ---

--- task ---

Voer nu de code uit.

![puinhoop van stempels](images/mess_stamps.png)

Je krijgt geen nette verzameling stempels.

Dit komt omdat het blok `stempel sprite`{:class="block3myblocks"} op dit moment alleen wordt uitgevoerd voor het totaal aantal kolommen.

--- /task ---

--- task ---

Verander de `stempel sprites`{:class="block3myblocks"} code zodat het vaak genoeg `herhaalt`{:class="block3control"} om het volledige raster van sprites te stempelen.

--- hints ---
 --- hint ---

Het totale aantal stempels dat je nodig hebt, is het aantal dat je opgeeft als `kolommen`{:class="block3myblocks"} vermenigvuldigd met het aantal dat je opgeeft als `rijen`{:class="block3myblocks"}

--- /hint --- --- hint ---

Gebruik dit extra blok:

```blocks3
((rijen ::custom) * (kolommen ::custom))
```

--- /hint --- --- hint ---

Hier is het voltooide `stempel sprites`{:class="block3myblocks"} script:

```blocks3
define stempel sprites (rijen) (kolommen)
maak grootte (40) %
+ herhaal ((rijen :: custom-arg) * (kolommen :: custom-arg))
maak [index v] (willekeurig getal tussen ( 1) en (lengte van [x_posities v]))
ga naar x: (item (index) van [x_posities v]) y: (item (index) van [y_posities v]
verwijder (index) van [x_posities v]
verwijder (index) van [y_posities v]
stempel
volgend uiterlijk
```

--- /hint ------ /hints ---

![geordend raster](images/nice_grid.png)

--- /task ---