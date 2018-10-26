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

To do this, you'll need to follow the following **algorithm**:
  1. Set `index`{:class="blockdata"} to a random number between `1` and the length of a list
  2. Move the sprite as you did before
  3. Delete the `index`{:class="blockdata"} position from the `y_positions`{:class="blockdata"} list
  4. Delete the `index`{:class="blockdata"} position from the `x_positions`{:class="blockdata"} list
  
--- task ---

Now add code to make the sprite's costume randomly placed in the grid.

--- hints --- --- hint ---
Remove the `set index to 1`{:class="blockdata"} from before the loop. Then within the loop, `set index to `{:class="blockdata"} a `random`{:class="blockoperators"} number between 1 and the `length of x_positions`{:class="blockdata"}.
Then `delete`{:class="blockdata"} the `index`{:class="blockdata"} from both the `x_positions`{:class="blockdata"} and `y_positions`{:class="blockdata"} lists.
--- /hint --- --- hint ---

- Here's the additional blocks you need.
```blocks
define stamp sprites (rows) (columns)
set size to (40) %
- set [index v] to [1]
repeat (columns)
go to x: (item (index) of [x_positions v]) y: (item (index) of [y_positions v]
stamp
next costume
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

- Here is your completed script showing how to delete the items from the list:

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
```
--- /hint --- --- /hints ---
--- /task ---
