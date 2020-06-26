## Άλλαξε τις ενδυμασίες

Προς το παρόν, το πρόγραμμά σου σφραγίζει την ίδια ενδυμασία και το μέγεθος της είναι πολύ μεγάλο.

\--- task \---

Πρόσθεσε στην εντολή `σφράγισε αντικείμενα`{:class="block3myblocks"} ένα μπλοκ για να αλλάζει σε ένα κατάλληλο μέγεθος αντικειμένου πριν μπει στο βρόχο `επανάλαβε`{:class="block3control"}. Πρόσθεσε ένα μπλοκ μέσα στο βρόχο για να αλλάξεις στην `επόμενη ενδυμασία`{:class="block3looks"} μετά τη `σφραγίδα`{:class="block3extensions"}.

```blocks3
define stamp sprites (rows) (columns)
set size to (40) %
set [index v] to [1]
repeat (columns :: custom-arg)
go to x: (item (index) of [x_positions v]) y: (item (index) of [y_positions v]
stamp
next costume
change [index v] by (1)
```

\--- /task \---

Όταν εκτελείται το πρόγραμμα τώρα, θα πρέπει να βλέπεις κάτι τέτοιο:

![αλλαγμένα_αντικείμενα](images/changed_sprites.png)

Το πρόγραμμα εμφανίζει κυκλικά όλες τις ενδυμασίες με τη σειρά. Για να μην εμφανίζεται κάθε ενδυμασία στο ίδιο σημείο κάθε φορά που τρέχει το πρόγραμμα, θα πρέπει να σφραγίζεις το αντικείμενο σε τυχαία σημεία του πλέγματος.

Για να το κάνεις αυτό, πρέπει να ακολουθήσεις αυτόν τον **αλγόριθμο**:

1. `Επανάλαβε`{:class="block3control"} μέχρι να αδειάσει η λίστα
2. Όρισε το `ευρετήριο`{:class="block3variables"} σε `τυχαίο`{:class="block3operators"} αριθμό μεταξύ `1` και το μήκος μιας λίστας
3. Μετακίνησε το αντικείμενο όπως πριν
4. Αφαίρεσε το στοιχείο στη θέση που δείχνει το `ευρετήριο`{:class="block3variables"} από τη λίστα `θέσεις_y`{:class="block3variables"}
5. Αφαίρεσε το στοιχείο στη θέση που δείχνει το `ευρετήριο`{:class="block3variables"} από τη λίστα `θέσεις_x`{:class="block3variables"}

\--- task \---

Πρόσθεσε κώδικα για να σφραγίσεις το αντικείμενο σε τυχαία σημεία στο πλέγμα.

\--- hints \--- \--- hint \---

Αφαίρεσε το `όρισε ευρετήριο σε 1`{:class="block3variables"} πριν από την βρόχο `επανάλαβε`{:class="block3control"}.

Στη συνέχεια, μέσα στο βρόχο, `όρισε ευρετήριο σε`{:class="block3variables"} ένα `τυχαίο`{:class="block3operators"} αριθμό μεταξύ `1` και `μήκος λίστας θέσεις_x`{:class="block3variables"}.

Έπειτα `διάγραψε`{:class="block3variables"} το στοιχείο στη θέση `ευρετήριο`{:class="block3variables"} από τις λίστες `θέσεις_x`{:class="block3variables"} και `θέσεις_y`{:class="block3variables"}.

\--- /hint \--- \--- hint \---

Εδώ είναι τα επιπλέον μπλοκ που χρειάζεσαι:

```blocks3
define stamp sprites (rows) (columns)
set size to (40) %
- set [index v] to [1]
repeat (columns :: custom-arg)
go to x: (item (index) of [x_positions v]) y: (item (index) of [y_positions v]
stamp
next costume
- change [index v] by (1)
end

set [index v] to ()
(pick random () to ()
length of [x_positions v]
delete () of [x_positions v]

delete () of [y_positions v]
(index)
(index)
```

\--- /hint \--- \--- hint \---

Έτσι πρέπει να μοιάζει ο κώδικας:

```blocks3
define stamp sprites (rows) (columns)
set size to (40) %
- set [index v] to [1]
repeat (columns :: custom-arg)
+ set [index v] to (pick random (1) to (length of [x_positions v]))
go to x: (item (index) of [x_positions v]) y: (item (index) of [y_positions v]
+ delete (index) of [x_positions v]
+ delete (index) of [y_positions v]
stamp
next costume
- change [index v] by (1)
```

\--- /hint \--- \--- /hints \--- \--- /task \---