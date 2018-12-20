## Add rows

Now that you have the code to create a single row of stamped costumes, you should add code to create more rows.

Go to your `generate positions`{:class="block3myblocks"} block.

![blocks_1545309764_704934](images/blocks_1545309764_704934.png)

--- task ---
Add another `repeat`{:class="block3control"} loop that runs the number of times you give to the `generate positions`{:class="block3myblocks"} block as the `rows`{:class="block3myblocks"} input. Place the `repeat`{:class="block3control"} loop into your script as shown here:

![blocks_1545309765_8974705](images/blocks_1545309765_8974705.png)
--- /task ---

Next you need to increase the value of `y_pos`{:class="block3variables"} each time the `repeat (rows)`{:class="block3control"} loop runs.

You do this in a similar manner to how you increase the value of `x_pos`{:class="block3variables"} in the `repeat (columns)`{:class="block3control"} loop.

--- task ---
At the end of the code inside the `repeat (rows)`{:class="block3control"} loop, `y_pos`{:class="block3variables"} should increase up to `150`{:class="block3variables"}, which is `300`{:class="block3variables"} away from its starting value of `-150`{:class="block3variables"}. This needs to happen for each row of stamps.

![blocks_1545309767_1153772](images/blocks_1545309767_1153772.png)
--- /task ---

--- task ---
Make sure you give the number of `rows`{:class="block3myblocks"} as an input to your blocks.

![blocks_1545309768_3110137](images/blocks_1545309768_3110137.png)
--- /task ---
	
--- task ---
Run your code now.

![mess of stamps](images/mess_stamps.png)
	
You won't get a neat grid of stamps.

This is because, right now, the `stamp sprite`{:class="block3myblocks"} block only runs for the total number of columns.
--- /task ---

--- task ---

Change your `stamp sprites`{:class="block3myblocks"} script so that it `repeats`{:class="block3control"} enough times to stamp the complete grid of sprites.

--- hints --- --- hint ---
The total number of stamps you need is the number you give as `columns`{:class="block3myblocks"} multiplied by the number you give as `rows`{:class="block3myblocks"}
--- /hint --- --- hint ---
Use this additional block:
![blocks_1545309769_3920956](images/blocks_1545309769_3920956.png)
--- /hint --- --- hint ---
Here's the completed `stamp sprites`{:class="block3myblocks"} script:
![blocks_1545309770_515168](images/blocks_1545309770_515168.png)
--- /hint --- --- /hints ---

![ordered grid](images/nice_grid.png)
--- /task ---
