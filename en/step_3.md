## Making a grid

You are going to produce a grid of stamped costumes, just like this one:

![stamps in grid](images/stamp_grid.png)
	
To do this you will need to know the `x` and `y` coordinates of where each stamp is going to be placed.

--- task ---
To begin with you'll need to create a new block called `generate positions`{:class="blockmoreblocks"} for your sprite. The block will need to have two 'number input' parameters. Call the two parameters `rows`{:class="blockmoreblocks"} and `columns`{:class="blockmoreblocks"}.

The values of these parameters will set how many rows and columns your grid of sprites will have.

[[[generic-scratch-make-block]]]

```blocks
define generate positions (rows)(columns)
```
--- /task ---

--- task ---
Create two lists. One will be called `x_positions`{:class="blockdata"}, and the other will be called `y_positions`{:class="blockdata"}.
--- /task ---

--- task ---
Underneath your `generate positions`{:class="blockmoreblocks"} block, add blocks to delete all the items from both lists, so that each time the game is played, the lists are empty and new.

```blocks
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
```
--- /task ---

--- task ---
Next you will need to create two new variables. Call these `x_pos`{:class="blockdata"} and `y_pos`{:class="blockdata"}.
--- /task ---

The idea to begin with is to add positions into the `x_positions`{:class="blockdata"} list. There will be ten positions in total, starting at `-200`{:class="blockdata"} and going up to `200`{:class="blockdata"}.

The `y_positions`{:class="blockdata"} list can just contain 10 values, all at `-150`{:class="blockdata"}, as we're only doing one row for no.

--- task ---
Start by setting the `y_pos`{:class="blockdata"} and `x_pos`{:class="blockdata"} variables to `-150`{:class="blockdata"} and `-200`{:class="blockdata"}. This will be the location of the first image.

```blocks
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
set [x_pos v] to [-200]
```
--- /task ---

--- task ---
Next, add a `repeat`{:class="blockcontrol"} loop to add some coordinates to the lists.

How many times should the loop repeat?

In this case it is ten times. This is one time for each column in the grid. As you've set up the custom block to take `columns`{:class="blockmoreblocks"} as a parameter, you can use this value.

```blocks
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
set [x_pos v] to [-200]
repeat (columns)
```
--- /task ---
	
Within the loop, you'll need to add the values of `x_pos`{:class="blockdata"} and `y_pos`{:class="blockdata"} into the lists. Then you'll need to increase the value of `x_pos`{:class="blockdata"} by a little.

So how much should `x_pos`{:class="blockdata"} be increased by each time? As you know you want `x_pos`{:class="blockdata"} to reach `200`{:class="blockdata"}, that's a total increase of `400`{:class="blockdata"}. This needs to be done nine times, after the initial value has been added, which is `columns - 1`{:class="blockoperators"}

So the increase on `x_pos`{:class="blockdata"}, each time around the loop should be `400 / (columns - 1)`{:class="blockoperators"}

--- task ---
Add in the code that will add the `x_pos`{:class="blockdata"} and `y_pos`{:class="blockdata"} values into the `x_positions`{:class="blockdata"} and `y_positions`{:class="blockdata"} lists.

	
--- hints --- --- hint ---
Within the loop, you need to add `x_pos`{:class="blockdata"} to the `x_positions`{:class="blockdata"} list, and add the `y_pos`{:class="blockdata"} to the `y_positions`{:class="blockdata"} list.
Then `x_pos`{:class="blockdata"} needs to be increased by `400 / (columns -1)`{:class="blockoperators"}
--- /hint --- --- hint ---
This shows the additional blocks you need to add into your script.

```blocks
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
set [x_pos v] to [-200]
repeat (columns)
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
--- /hint --- --- hint ---

- Here is the completed script
```blocks
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
set [x_pos v] to [-200]
repeat (columns)
add (x_pos) to [x_positions v]
add (y_pos) to [y_positions v]
change [x_pos v] by (((400) / (columns)) - (1))
```
--- /hint --- --- /hints ---
--- /task ---



