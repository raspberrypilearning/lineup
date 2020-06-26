## Δημιούργησε μια κάναβο

Πρόκειται να δημιουργήσεις μια κάναβο, δηλαδή ένα νοητό πλέγμα από ενδυμασίες που έχουν τοποθετηθεί σαν σφραγίδες στη σκηνή:

![σφραγίδες σε πλέγμα](images/stamp_grid.png)

Για να το κάνεις αυτό, πρέπει να γνωρίζεις τις συντεταγμένες `x`{:class="block3motion"} και `y`{:class= "block3motion"} των σημείων όπου πρέπει να τοποθετεί κάθε σφραγίδα.

\--- task \---

Αρχικά, δημιούργησε ένα νέο μπλοκ που ονομάζεται `δημιουργία θέσεων`{:class="block3myblocks"}. Το μπλοκ πρέπει να παίρνει δύο αριθμούς ως παραμέτρους εισόδου. Ονόμασε τις δύο παραμέτρους `γραμμές`{:class="block3myblocks"} και `στήλες`{:class="block3myblocks"}.

Οι τιμές αυτών των παραμέτρων θα καθορίζουν πόσες γραμμές και στήλες έχει η κάναβός σου.

[[[generic-scratch3-make-block]]]

```blocks3
define generate positions (rows)(columns)
```

\--- /task \---

\--- task \---

Δημιούργησε δύο λίστες και ονόμασε την πρώτη `θέσεις_x`{:class="block3variables"} και τη δεύτερη `θέσεις_y`{:class="block3variables"}. Αυτές οι λίστες προορίζονται για την αποθήκευση των συντεταγμένων `x`{:class="block3motion"} και `y`{:class="block3motion"} για τις σφραγίδες.

\--- /task \---

\--- task \---

Μέσα στην εντολή `δημιουργία θέσεων`{:class="block3myblocks"}, πρόσθεσε μπλοκ για να διαγράψεις όλα τα στοιχεία και από τις δύο λίστες, έτσι ώστε κάθε φορά που ξεκινά το παιχνίδι, οι λίστες να είναι κενές.

```blocks3
define generate positions (rows)(columns)
+ delete [all v] of [y_positions v]
+ delete [all v] of [x_positions v]
```

\--- /task \---

\--- task \---

Έπειτα δημιούργησε δύο μεταβλητές `θέση_x`{:class="block3variables"} και `θέση_y`{:class="block3variables"}.

\--- /task \---

Η λίστα `θέσεις_x`{:class="block3variables"} πρέπει να περιέχει συνολικά δέκα αριθμούς και αυτοί θα πρέπει να ξεκινούν από `-200`{:class="block3variables"} και φτάνουν ως και `200`{:class="block3variables"}.

Προς το παρόν, η λίστα `θέσεις_y`{:class="block3variables"} μπορεί να περιέχει τον αριθμό `-150`{:class="block3variables"} δέκα φορές, έτσι ώστε το πλέγμα να έχει μόνο μία γραμμή.

\--- task \---

Άρχισε προσθέτοντας κώδικα στο μπλοκ `δημιουργία θέσεων`{:class="block3myblocks"} για να ορίσει τη μεταβλητή `θέση_y`{:class="block3variables"} σε `-150`{:class="block3variables"} και τη μεταβλητή `θέση_x` {:class="block3variables"} σε `-200`{:class="block3variables"}. Αυτή είναι η θέση της σφραγίδας που θα τοποθετήσει το πρώτο αντικείμενο στη σκηνή.

```blocks3
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
+ set [y_pos v] to [-150]
+ set [x_pos v] to [-200]
```

\--- /task \---

\--- task \---

Στη συνέχεια, πρόσθεσε ένα βρόχο `επανάλαβε`{:class="block3control"} για να τοποθετεί τις συντεταγμένες στις δύο λίστες.

Ο βρόχος `επανάλαβε`{:class="block3control"} πρέπει να εκτελείται μία φορά για κάθε στήλη που θες να έχει το πλέγμα.

Η εντολή `δημιουργία θέσεων`{:class="block3myblocks"} παίρνει `στήλες`{:class="block3myblocks"} ως είσοδο, ώστε να μπορείς να χρησιμοποιείς τις `στήλες`{:class="block3myblocks"} για στο βρόχο `επανάλαβε`{:class="block3control"}.

```blocks3
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
set [x_pos v] to [-200]
+ repeat (columns :: custom-arg)
```

\--- /task \---

Εντός της `επανάλαβε`{:class="block3control"}, πρόσθεσε τις τιμές `θέση_x`{:class="block3variables"} και `θέση_y`{:class="block3variables"} στις αντίστοιχες λίστες. Στη συνέχεια, πρέπει να αυξήσεις λίγο την τιμή `θέση_x`{:class="block3variables"}. Πόσο θα πρέπει να είναι η αύξηση της τιμής `θέση_x`{:class="block3variables"};

Έτσι μπορείς να το βρεις:

- Η `θέση_x`{:class="block3variables"} ξεκινά με την τιμή `-200`{:class="block3variables"}
- Την τελευταία φορά που τρέχει ο βρόχος `επανάλαβε`{:class="block3control"}, η `θέση_x`{:class="block3variables"} πρέπει να φτάσει την τιμή `200`{:class="block3variables"}
- Αυτό είναι δηλαδή μια συνολική αύξηση κατά `400`{:class="block3variables"}
- Η πρώτη τιμή της `θέση_x`{:class="block3variables"} είναι για την πρώτη στήλη στο πλέγμα, ενώ ο αριθμός των στηλών καθορίζεται από την παράμετρο εισόδου `στήλες`{:class="block3myblocks"}

Έτσι, μετά την πρώτη προσθήκη της `θέση_x`{:class="block3variables"}, κάθε φορά στο βρόχο, η τιμή της `θέση_x`{:class="block3variables"} θα πρέπει να αυξηθεί κατά `400 / (στήλες - 1)`{:class="block3operators"}

\--- task \---

Βάλε στον κώδικα που θα προσθέτει όλες τιμές των `θέση_x` {:class = "block3variables"} και `θέση_y`{:class="block3variables"} στις λίστες `θέσεις_x`{:class="block3variables"} και `θέσεις_y`{:class="block3variables"}.

\--- hints \--- \--- hint \---

Μέσα στο βρόχο, πρέπει να προσθέσεις τη `θέση_x`{:class="block3variables"} στη λίστα `θέσεις_x`{:class="block3variables"} και τη `θέση_y`{:class="block3variables"} στη λίστα `θέσεις_y`{:class="block3variables"}. Στη συνέχεια η μεταβλητή `θέση_x`{:class="block3variables"} πρέπει να αυξάνεται κατά `400/(στήλες -1)`{:class="block3operators"} κάθε φορά που ο βρόχος επαναλαμβάνεται.

\--- /hint \--- \--- hint \---

Εδώ βλέπεις τα μπλοκ που πρέπει να προσθέσεις στο πρόγραμμά σου.

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

Εδώ είναι το ολοκληρωμένο πρόγραμμα για το μπλοκ `δημιουργία θέσεων`{:class="block3myblocks"}:

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