## Changing the costumes

--- task ---
Change the stamp each time and make it a more appropriate size when it is placed on the stage.

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

When you run the script, you should see something like this:

![changed_sprites](images/changed_sprites.png)
	
At the moment, your program cycles through all the costumes in order. This isn't a problem, so long as you place the sprite in a random location each time.

- To do this, you'll need to follow the following **algorithm**:
  1. Set `index`{:class="blockdata"} to a random number between `1` and the length of a list
  2. Move the sprite as you did before
  3. Delete the `index`{:class="blockdata"} position from the `y_positions`{:class="blockdata"} list
  4. Delete the `index`{:class="blockdata"} position from the `x_positions`{:class="blockdata"} list
  
--- task ---
Now add code to make the sprite's costume randomly placed in the grid.
--- hints --- --- hint ---
- Here's how you can pick a random number from within the list:
```blocks
pick random (1) to (length of [x_positions v])
```
--- /hint --- --- hint ---
- Here's how to pick a random item from the list:
```blocks
define stamp sprites (rows) (columns)
set size to (40) %
- set [index v] to [1]
repeat (columns)
+ set [index v] to (pick random (1) to (length of [x_positions v]))
go to x: (item (index) of [x_positions v]) y: (item (index) of [y_positions v]
stamp
next costume
- change [index v] by (1)
```
--- /hint --- --- hint ---
- Here is your completed script showing how to delete the items from the list:
```blocks
define stamp sprites (rows) (columns)
set size to (40) %
repeat (columns)
set [index v] to (pick random (1) to (length of [x_positions v]))
go to x: (item (index) of [x_positions v]) y: (item (index) of [y_positions v]
+ delete (index) of [x_positions v]
+ delete (index) of [y_positions v]
stamp
next costume
```
--- /hint --- --- /hints ---
--- /task ---
