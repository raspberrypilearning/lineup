## Maak een raster

Je gaat een raster met gestempelde uiterlijken maken:

![stempels in raster](images/stamp_grid.png)

Om dit te doen, moet je de coördinaten `x`{:class="block3motion"} en `y`{:class="block3motion"} kennen van waar elk stempel moet worden geplaatst.

--- task ---

Maak eerst een nieuw blok met de naam `genereer posities`{:class="block3myblocks"}. Het blok moet twee parameters voor 'getalinvoer' hebben. Noem de twee parameters `rijen`{:class="block3myblocks"} en `kolommen`{:class="block3myblocks"}.

De waarden van deze parameters bepalen hoeveel rijen en kolommen je raster heeft.

[[[generic-scratch3-make-block]]]

```blocks3
define generate positions (rijen)(kolommen)
```

--- /task ---

--- task ---

Maak twee lijsten en noem er één `x_posities`{:class="block3variables"} en de andere `y_posities`{:class="block3variables"}. In deze lijsten worden de coördinaten `x`{:class="block3motion"} en `y`{:class="block3motion"} voor de stempels opgeslagen.

--- /task ---

--- task ---

Binnen jouw `genereer posities`{:class="block3myblocks"} blok, voeg blokken toe om alle items van beide lijsten te verwijderen, zodat elke keer dat het spel start, de lijsten leeg zijn.

```blocks3
define generate positions (rijen)(kolommen)
+ verwijder [alle v] van [y_posities v]
+ verwijder [alle v] van [x_posities v]
```

--- /task ---

--- task ---

Maak vervolgens twee variabelen en noem er één `x_pos`{:class="block3variables"} en de andere `y_pos`{:class="block3variables"}.

--- /task ---

De lijst `x_posities`{:class="block3variables"} moet in totaal tien getallen bevatten, en deze moeten beginnen bij `-200`{:class="block3variables"} en gaan tot `200`{:class="block3variables"}.

Voorlopig kan de lijst `y_posities`{:class="block3variables"} gewoon tien keer het getal `-150`{:class="block3variables"} bevatten, zodat het raster slechts één rij heeft.

--- task ---

Begin door code toe te voegen aan het `genereer posities`{:class="block3myblocks"} blok om de variabele `y_pos`{:class="block3variables"} in te stellen op `-150`{:class="block3variables"} en de `x_pos`{:class="block3variables"} in te stellen op `-200`{:class="block3variables"}. Dit is de locatie van de eerste gestempelde sprite.

```blocks3
define generate positions (rijen)(kolommen)
verwijder [alle v] van [y_posities v]
verwijder [alle v] van [x_posities v]
+ maak [y_pos v] [-150]
+ maak [x_pos v] [-200]
```

--- /task ---

--- task ---

Voeg vervolgens een lus `herhaal`{:class="block3control"} toe om coördinaten in de lijsten te plaatsen.

De lus `herhaal`{:class="block3control"} moet éénmaal worden uitgevoerd voor elke kolom die het raster moet hebben.

Het `genereer posities`{:class="block3myblocks"} blok neemt `kolommen`{:class="block3myblocks"} als invoer, dus je kunt `kolommen`{:class="block3myblocks"} gebruiken voor de `herhaal`{:class="block3control"} lus.

```blocks3
define generate positions (rijen)(kolommen)
verwijder [alle v] van [y_posities v]
verwijder [alle v] van [x_posities v]
maak [y_pos v] [-150]
maak [x_pos v] [-200]
+ herhaal (kolommen :: custom-arg)
```

--- /task ---

Voeg in de `herhaal`{:class="block3control"} lus de waarden van `x_pos`{:class="block3variables"} en `y_pos`{:class="block3variables"} toe aan de lijsten. Dan moet je de waarde van `x_pos`{:class="block3variables"} een beetje verhogen. Met hoeveel moet de waarde van `x_pos`{:class="block3variables"} toenemen?

Zo kom je erachter:

- `x_pos`{:class="block3variables"} begint met de waarde `-200`{:class="block3variables"}
- De laatste keer dat de `herhaal`{:class="block3control"} lus wordt uitgevoerd, `x_pos`{:class="block3variables"} moet de waarde `200`{:class="block3variables"} bereiken
- Dat is een totale toename van `400`{:class="block3variables"}
- De eerste waarde `x_pos`{:class="block3variables"} is voor de eerste kolom op het raster en hoeveel kolommen er zijn, wordt bepaald door de invoer van `kolommen`{:class="block3myblocks"}

Dus nadat de eerste `x_pos`{:class="block3variables"} waarde is toegevoegd, moet elke keer rond de lus de waarde van `x_pos`{:class="block3variables"} toenemen met `400 / (kolommen - 1)`{:class="block3operators"}

--- task ---

Voeg de code toe die alle `x_pos`{:class="block3variables"} en `y_pos`{:class="block3variables"} toevoegt aan de `x_posities`{:class="block3variables"} en `y_posities`{:class="block3variables"} lijsten.

--- hints ---
 --- hint ---

Binnen de lus moet je `x_pos`{:class="block3variables"} toevoegen aan de lijst `x_posities`{:class="block3variables"} en de `y_pos`{:class="block3variables"} toevoegen aan de `y_posities`{:class="block3variables"} lijst. Vervolgens moet de variabele `x_pos`{:class="block3variables"} telkens met `400 / (kolommen -1)`{:class="block3operators"} verhoogd worden, telkens wanneer de lus wordt herhaald.

--- /hint --- --- hint ---

Dit toont de extra blokken die je aan het script moet toevoegen.

```blocks3
define generate positions (rijen)(kolommen)
verwijder [alle v] van [y_posities v]
verwijder [alle v] van [x_posities v]
maak [y_pos v] [-150]
maak [x_pos v] [-200]
herhaal ( kolommen :: custom-arg)
einde

(x_pos)
(y_pos)

voeg () toe aan [x_posities v]

voeg () toe aan [y_posities v]

verander [x_pos v] met ()
(kolommen :: custom
() / () 
() - ()
```

--- /hint --- --- hint ---

Hier is het voltooide script voor het `genereer posities`{:class="block3myblocks"} blok:

```blocks3
define generate positions (rijen)(kolommen)
verwijder [alle v] van [y_posities v]
verwijder [alle v] van [x_posities v]
maak [y_pos v] [-150]
maak [x_pos v] [-200]
herhaal ( kolommen :: custom-arg)
+ voeg (x_pos) toe aan [x_posities v]
+ voeg (y_pos) toe aan [y_posities v]
+ verander [x_pos v] met ((400) / ((kolommen :: custom-arg) - (1)
```

--- /hint ------ /hints --- --- /task ---