## Πρόσθεσε γραμμές

Τώρα που έχεις τον κώδικα για να δημιουργείς μια μοναδική γραμμή από σφραγίδες ενδυμασιών, θα πρέπει να προσθέσεις κώδικα για να δημιουργείς περισσότερες γραμμές.

Πήγαινε στην εντολή `δημιουργία_θέσεων`{:class="block3myblocks"}.

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

Πρόσθεσε ένα επιπλέον βρόχο `επανάλαβε`{:class="block3control"} που εκτελεί το μπλοκ `δημιουργία θέσεων`{:class="block3myblocks"}, όσες φορές δείχνει η μεταβλητή εισόδου `γραμμές`{:class="block3myblocks"}. Τοποθέτησε το βρόχο `επανάλαβε`{:class="block3control"} στο πρόγραμμα όπως φαίνεται εδώ:

```blocks3
ορισμός δημιουργία θέσεων (γραμμές)(στήλες)
διάγραψε [all v] από λίστα [θέσεις_y v]
διάγραψε [all v] από λίστα [θέσεις_x v]
όρισε [θέση_y v] σε [-150]
+επανάλαβε (γραμμές :: custom-arg)
όρισε [θέση_x v] σε [-200]
επανάλαβε (στήλες :: custom-arg)
πρόσθεσε (θέση_x) στη λίστα [θέσεις_x v]
πρόσθεσε (θέση_y) στη λίστα [θέσεις_y v]
άλλαξε [θέση_x v] κατά (((400) / (στήλες :: custom-arg)) - (1))
end
end
```

\--- /task \---

Στη συνέχεια πρέπει να αυξήσεις την τιμή της `θέση_y`{:class="block3variables"} κάθε φορά που εκτελείται ο βρόχος `επανάλαβε (γραμμές)`{:class="block3control"}.

Αυτό το κάνεις παρόμοια με τον τρόπο που αυξάνεις την τιμή `θέση_x`{:class="block3variables"} στο βρόχο `επανάλαβε (στήλες)`{:class="block3control"}.

\--- task \---

Στο τέλος του κώδικα εντός του βρόχου `επανάλαβε (γραμμές)`{:class="block3control"}, η `θέση_y`{:class="block3variables"} θα πρέπει να αυξάνεται ως το `150`{:class="block3variables"}, το οποίο είναι `300`{:class="block3variables"} περισσότερο από την αρχική τιμή `-150`{:class="block3variables"}. Αυτό πρέπει να συμβεί για κάθε γραμμή σφραγίδων.

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

Βεβαιώσου ότι έδωσες τον αριθμό `γραμμές`{:class="block3myblocks"} ως είσοδο στα μπλοκ σου.

```blocks3
when flag clicked
erase all
generate positions (4) (10) ::custom
stamp sprite (4) (10) ::custom
```

\--- /task \---

\--- task \---

Τρέξε τον κώδικά σου τώρα.

![χάος σφραγίδων](images/mess_stamps.png)

Θα πάρεις ένα χάος από σφραγίδες.

Αυτό συμβαίνει επειδή, αυτή τη στιγμή, το μπλοκ `σφράγισε αντικείμενα`{:class="block3myblocks"} εκτελείται μόνο για τον συνολικό αριθμό στηλών.

\--- /task \---

\--- task \---

Αλλάξτε τον κώδικα στην εντολή `σφράγισε αντικείμενα`{:class="block3myblocks"} έτσι ώστε να `επαναλαμβάνεται`{:class="block3control"} αρκετές φορές ώστε να σφραγίζει σε όλο πλέγμα των αντικειμένων.

\--- hints \--- \--- hint \---

Ο συνολικός αριθμός σφραγίδων που χρειάζεσαι είναι ο αριθμός που δίνεις ως `στήλες`{:class="block3myblocks"} πολλαπλασιασμένος με τον αριθμό που δίνεις ως `γραμμές`{:class="block3myblocks"}

\--- /hint \--- \--- hint \---

Χρησιμοποίησε αυτό το επιπλέον μπλοκ:

```blocks3
((rows ::custom) * (columns ::custom))
```

\--- /hint \--- \--- hint \---

Εδώ είναι το ολοκληρωμένο πρόγραμμα για το μπλοκ `σφράγισε αντικείμενα`{:class="block3myblocks"}:

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

![διατεταγμένο πλέγμα](images/nice_grid.png)

\--- /task \---