## Change the costumes

At the moment, your program stamps the same sprite costume over and over, and the size of the costume is too large.

--- task ---
Add code to the `stamp sprites`{:class="blockmoreblocks"} block to make the sprite a suitable size before the `repeat`{:class="blockcontrol"} loop starts. Add a block inside the loop to switch the `next costume`{:class="blocklooks"} after the `stamp`{:class="blockpen"} block.

```blocks
define stamp sprites (rows) (columns)
set size to (40) %
set [index v] to [1]
repeat (columns)
go to x: (item (index) of [x_positions v]) y: (item (index) of [y_positions v]
stamp
next costume
change [index v] by (1)
```
--- /task ---

When you run the script now, you should see something like this:

![changed_sprites](images/changed_sprites.png)
	
Your program cycles through all the costumes in order. So that each costume does not show up in the same place every time the program runs, you should stamp the sprite in random places on the grid.

To do this, you need to follow this **algorithm**:
  1. `Repeat`{:class="blockcontrol"} until the list is empty
  1. Set `index`{:class="blockdata"} to a `random`{:class="blockoperators"} number between `1` and the length of a list
  2. Move the sprite as you did before
  3. Delete the item at the `index`{:class="blockdata"} position from the `y_positions`{:class="blockdata"} list
  4. Delete the item at the `index`{:class="blockdata"} position from the `x_positions`{:class="blockdata"} list
  
--- task ---

Add code to stamp the sprite in random places on the grid.

--- hints --- --- hint ---
Remove the `set index to 1`{:class="blockdata"} from before the `repeat`{:class="blockcontrol"} loop.

Then within the loop, `set index to `{:class="blockdata"} a `random`{:class="blockoperators"} number between `1` and the `length of x_positions`{:class="blockdata"}.

Then `delete`{:class="blockdata"} the item at the `index`{:class="blockdata"} from both the `x_positions`{:class="blockdata"} and `y_positions`{:class="blockdata"} lists.
--- /hint --- --- hint ---

Here are the additional blocks you need:
```blocks
define stamp sprites (rows) (columns)
set size to (40) %
- set [index v] to [1]
repeat (columns)
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
--- /hint --- --- hint ---

This is what your code should look like:

```blocks
define stamp sprites (rows) (columns)
set size to (40) %
- set [index v] to [1]
repeat (columns)
+ set [index v] to (pick random (1) to (length of [x_positions v]))
go to x: (item (index) of [x_positions v]) y: (item (index) of [y_positions v]
+ delete (index) of [x_positions v]
+ delete (index) of [y_positions v]
stamp
next costume
- change [index v] by (1)
```
--- /hint --- --- /hints ---
--- /task ---
