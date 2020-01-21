## पंक्ति पर मोहर लगाएँ

अब तक आपके पास दोनों सूचियों में दस-दस मान हैं। अब सूचियों में संगृहीत स्टेज निर्देशांकों में कुछ परिधानों पर मोहर लगाएँ।

\--- task \---

अपने प्रोजेक्ट में **Pen** एक्सटेंशन जोड़ें।

[[[generic-scratch3-add-pen-extension]]]

\--- /task \---

\--- task \---

Create a new block and call it `stamp sprites`{:class="block3myblocks"}. This block needs two number inputs named `row`{:class="block3myblocks"} and `columns`{:class="block3myblocks"} just like the other custom block.

```blocks3
define stamp sprites (rows) (columns)
```

\--- /task \---

\--- task \---

Create a new variable called `index`{:class="block3variables"} with which to track the position in the lists that your program is reading. To begin with, set `index`{:class="block3variables"} to `1`{:class="block3variables"} to fetch the first item of each list.

```blocks3
define stamp sprites (rows) (columns)
+ set [index v] to [1]
```

\--- /task \---

\--- task \---

The `stamp sprites`{:class="block3myblocks"} block should stamp a sprite for each pair of coordinates in the list. To do this, the block needs a `repeat`{:class="block3variables"} loop that runs once for each column.

```blocks3
define stamp sprites (rows) (columns)
set [index v] to [1]
+ repeat (columns :: custom-arg)
```

\--- /task \---

\--- task \---

Within the `repeat`{:class="block3variables"} loop:

- स्प्राइट को `x_positions`{:class="block3variables"} और `y_positions`{:class="block3variables"} सूचियों में `index`{:class="block3variables"} स्थिति में ले जाएँ
- स्प्राइट पर `Stamp`{:class="block3extensions"} का उपयोग करें
- `index`{:class="block3variables"} को `1`{:class="block3variables"} से बदलें

\--- hints \--- \--- hint \---

Within the `repeat`{:class="block3variables"} loop, add a `go to x: y:`{:class="block3motion"} block. The `x`{:class="block3motion"} position in this block should be set to the `index`{:class="block3variables"} of `x_positions`{:class="block3variables"} and the `y`{:class="block3motion"} position should be set to the `index`{:class="block3variables"} of `y_positions`{:class="block3variables"}. Then add code to `stamp`{:class="block3extensions"} the sprite. Finally, add code to increase `index`{:class="block3variables"} by 1.

\--- /hint \--- \--- hint \---

Here are the blocks you need:

```blocks3
define stamp sprites (rows) (columns)
set [index v] to [1]
repeat (columns :: custom-arg)
end

change [index v] by (1)
(index) 
(index) 
go to x: () y: ()
(item ()of [y_positions v])
(item ()of [x_positions v])
stamp
```

\--- /hint \--- \--- hint \---

Here is the completed script for the `stamp sprites`{:class="block3myblocks"} block:

```blocks3
define stamp sprites (rows) (columns)
set [index v] to [1]
repeat (columns :: custom-arg)
+ go to x: (item (index) of [x_positions v]) y: (item (index) of [y_positions v]
+ stamp
+ change [index v] by (1)
```

\--- /hint \--- \--- /hints \--- \--- /task \---

\--- task \---

Add a `erase all`{:class="block3extensions"} block below the `when flag clicked`{:class="block3control"} block to clear the Stage each time the game starts. Then add the `stamp sprites`{:class="block3myblocks"} block at the bottom of the `when flag clicked`{:class="block3control"} script so you can test your new code.

```blocks3
when flag clicked
erase all
generate positions (1) (10) ::custom
stamp sprite (1) (10) ::custom
```

\--- /task \---

\--- task \---

Click the green flag. You should see something like this, depending on the costumes your sprite has:

![stamped sprites](images/stamped_sprites.png)

\--- /task \---