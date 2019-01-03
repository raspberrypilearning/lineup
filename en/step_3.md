## Create a grid

You are going to create a grid of stamped costumes:

![stamps in grid](images/stamp_grid.png)
	
To do this you need to know the `x`{:class="block3motion"} and `y`{:class="block3motion"} coordinates of where each stamp should be placed.

--- task ---
First, create a new block called `generate positions`{:class="block3myblocks"}. The block needs to have two 'number input' parameters. Call the two parameters `rows`{:class="block3myblocks"} and `columns`{:class="block3myblocks"}.

The values of these parameters will decide how many rows and columns your grid has.

[[[generic-scratch3-make-block]]]

![blocks_1545309745_352534](images/blocks_1545309745_352534.png)
--- /task ---

--- task ---
Create two lists, and call one of them `x_positions`{:class="block3variables"} and the other `y_positions`{:class="block3variables"}. These lists are for storing the `x`{:class="block3motion"} and `y`{:class="block3motion"} coordinates for the stamps.
--- /task ---

--- task ---
Inside your `generate positions`{:class="block3myblocks"} block, add blocks to delete all the items from both lists, so that each time the game starts, the lists are empty.

![blocks_1545309747_3178313](images/blocks_1545309747_3178313.png)
--- /task ---

--- task ---
Next, create two variables, and call one of them `x_pos`{:class="block3variables"} and the other `y_pos`{:class="block3variables"}.
--- /task ---

The `x_positions`{:class="block3variables"} list should contain ten numbers in total, and these should start at `-200`{:class="block3variables"} and go up to `200`{:class="block3variables"}.

For now, the `y_positions`{:class="block3variables"} list can just contain the number `-150`{:class="block3variables"} ten times, so that the grid only has one row.

--- task ---
Start by adding code to the `generate positions`{:class="block3myblocks"} block to set the `y_pos`{:class="block3variables"} variable to `-150`{:class="block3variables"} and the `x_pos`{:class="block3variables"} variable to `-200`{:class="block3variables"}. This is the location of the first stamped sprite.

![blocks_1545309748_4476635](images/blocks_1545309748_4476635.png)
--- /task ---

--- task ---
Next, add a `repeat`{:class="block3control"} loop to put coordinates into the lists.

The `repeat`{:class="block3control"} loop should run once for every column you want the grid to have.

The `generate positions`{:class="block3myblocks"} block takes `columns`{:class="block3myblocks"} as an input, so you can use `columns`{:class="block3myblocks"} for the `repeat`{:class="block3control"} loop.

![blocks_1545309749_585056](images/blocks_1545309749_585056.png)
--- /task ---
	
Within the `repeat`{:class="block3control"} loop, add the values of `x_pos`{:class="block3variables"} and `y_pos`{:class="block3variables"} into the lists. Then you need to increase the value of `x_pos`{:class="block3variables"} by a little. How much should the value of `x_pos`{:class="block3variables"} increase by?

This is how to figure it out:
  - `x_pos`{:class="block3variables"} starts out with the value `-200`{:class="block3variables"}
  - The final time the loop `repeat`{:class="block3control"} runs, `x_pos`{:class="block3variables"} should reach the value `200`{:class="block3variables"}
  - That's a total increase of `400`{:class="block3variables"}
  - The first `x_pos`{:class="block3variables"} value is for the first column on the grid, and how many columns there are is determined by the `columns`{:class="block3myblocks"} input

So after the first `x_pos`{:class="block3variables"} value is added, each time around the loop, the value of `x_pos`{:class="block3variables"} should increase by `400 / (columns - 1)`{:class="block3operators"}

--- task ---
Add in the code that will add all the `x_pos`{:class="block3variables"} and `y_pos`{:class="block3variables"} values into the `x_positions`{:class="block3variables"} and `y_positions`{:class="block3variables"} lists.
	
--- hints --- --- hint ---
Within the loop, you need to add `x_pos`{:class="block3variables"} to the `x_positions`{:class="block3variables"} list, and add the `y_pos`{:class="block3variables"} to the `y_positions`{:class="block3variables"} list.
Then `x_pos`{:class="block3variables"} variable needs to increase by `400 / (columns -1)`{:class="block3operators"} each time the loop repeats.
--- /hint --- --- hint ---
This shows the additional blocks you need to add into your script.

![blocks_1545309750_735553](images/blocks_1545309750_735553.png)
--- /hint --- --- hint ---

- Here is the completed script for the `generate positions`{:class="block3myblocks"} block:
![blocks_1545309751_9591546](images/blocks_1545309751_9591546.png)
--- /hint --- --- /hints ---
--- /task ---
