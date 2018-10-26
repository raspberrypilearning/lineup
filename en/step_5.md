s## Stamping a row
- So far you have ten values in the two lists. Let's stamp some costumes at the stage positions given in the list.

--- task ---
Create a new block and call it `stamp sprites`. It needs two parameters as well, both of which should be number inputs and named `row` and `columns` just like the last ones.

```blocks
define stamp sprites (rows) (columns)
```
--- /task ---

--- task ---
Create a new variable called `index`. You can use this to track which position in the list you are reading. Set it to `1`.

```blocks
define stamp sprites (rows) (columns)
set [index v] to [1]
```
--- /task ---

--- task ---

Now you're going to stamp a sprite for each set of coordinates in the list. This will require a loop that will repeat once for each column.

```blocks
define stamp sprites (rows) (columns)
set [index v] to [1]
repeat (columns)
```
--- /task ---	

--- task ---
Within the loop, move your sprite to the first position in the list, stamp it, then increase the `index` by 1.

```blocks
define stamp sprites (rows) (columns)
set [index v] to [1]
repeat (columns)
go to x: (item (index) of [x_positions v]) y: (item (index) of [y_positions v]
stamp
change [index v] by (1)
```

--- /task ---

--- task ---
Next you need to call this block as well. You should also add a `clear` block to your starting script so that it clears the stage each time.

```blocks
when flag clicked
clear
generate positions (1) (10) ::custom
stamp sprite (1) (10) ::custom
```
--- /task ---	

--- task ---
When you click the green flag, you should see something like this:

![stamped sprites](images/stamped_sprites.png)
--- /task ---

