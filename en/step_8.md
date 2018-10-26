## Placing your sprite

- Now it's time to position your sprite amongst the stamps. You'll notice at the moment that your sprite will overlap one of the stamps.

![overlap](images/overlap.png)

--- task ---
So this doesn't happen, you can just make your stamp loop run one time less: `(rows * columns) - 1`{:class="blockoperators"}

```blocks
define stamp sprites (rows) (columns)
set size to (40) %
+repeat (((rows) * (columns)) - (1))
set [index v] to (pick random (1) to (length of [x_positions v]))
go to x: (item (index) of [x_positions v]) y: (item (index) of [y_positions v]
delete (index) of [x_positions v]
delete (index) of [y_positions v]
stamp
next costume
```
--- /task ---

If you run the script now, then your sprite still overlaps with a stamp, but there should be a hole in your grid of stamps. If you look have your `x_positions`{:class="blockdata"} and `y_positions`{:class="blockdata"} list, then you'll also see that there is one coordinate position left.

--- task ---
To finish off this part the game, you'll need to continue the **green flag** section of the scripts.

```blocks
when flag clicked
clear
generate positions (4) (10) ::custom
stamp sprites (4) (10) ::custom
```

Here's what it needs to do:
  1. Send your sprite to `x:0 y:0`
  2. Bring the sprite to the front and set its size to 100%
  3. Say `Find me` for two seconds
  4. Move back one layer
  5. Set the sprite's size to 40%
  6. Move to the last remaining position in the lists

--- no-print ---
Here's an animation showing what should happen
![animation](images/demo_1.gif)
--- no-print ---

See if you can do this independently, and use the hints below if you need more help.

--- hints --- --- hint ---
- The first part is fairly simple:
```blocks
when flag clicked
clear
generate positions (4) (10) ::custom
stamp sprites (4) (10) ::custom
+go to x: (0) y: (0)
+go to front
+set size to (100) %
+say [Find me] for (2) secs
+go back (1) layers
+set size to (40) %
```
--- /hint --- --- hint ---
- To move your sprite to the correct location, you can use this code:
```blocks
when flag clicked
clear
generate positions (4) (10) ::custom
stamp sprites (4) (10) ::custom
go to x: (0) y: (0)
go to front
set size to (100) %
say [Find me] for (2) secs
go back (1) layers
set size to (40) %
+ go to x: (item (1 v) of [x_positions v]) y: (item (1 v) of [y_positions v])
```
--- /hint --- --- /hints ---

--- /task ---

  
