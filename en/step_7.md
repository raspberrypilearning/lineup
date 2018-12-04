## Add rows

Now that you have the code to create a single row of stamped costumes, you should add code to create more rows.

Go to your `generate positions`{:class="blockmoreblocks"} block.

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
--- task ---
Add another `repeat`{:class="blockcontrol"} loop that runs the number of times you give to the `generate positions`{:class="blockmoreblocks"} block as the `rows`{:class="blockmoreblocks"} input. Place the `repeat`{:class="blockcontrol"} loop into your script as shown here:

```blocks
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
+repeat (rows)
set [x_pos v] to [-200]
repeat (columns)
add (x_pos) to [x_positions v]
add (y_pos) to [y_positions v]
change [x_pos v] by (((400) / (columns)) - (1))
end
end
```
--- /task ---

Next you need to increase the value of `y_pos`{:class="blockdata"} each time the `repeat (rows)`{:class="blockcontrol"} loop runs.

You do this in a similar manner to how you increase the value of `x_pos`{:class="blockdata"} in the `repeat (columns)`{:class="blockcontrol"} loop.

--- task ---
At the end of the code inside the `repeat (rows)`{:class="blockcontrol"} loop, `y_pos`{:class="blockdata"} should increase up to `150`{:class="blockdata"}, which is `300`{:class="blockdata"} away from its starting value of `-150`{:class="blockdata"}. This needs to happen for each row of stamps.

```blocks
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
repeat (rows)
set [x_pos v] to [-200]
repeat (columns)
add (x_pos) to [x_positions v]
add (y_pos) to [y_positions v]
change [x_pos v] by (((400) / (columns)) - (1))
end
+change [y_pos v] by (((300) / (rows)) - (1))
end
```
--- /task ---

--- task ---
Make sure you give the number of `rows`{:class="blockmoreblocks"} as an input to your blocks.

```blocks
when flag clicked
clear
generate positions (4) (10) ::custom
stamp sprite (4) (10) ::custom
```
--- /task ---
	
--- task ---
Run your code now.

![mess of stamps](images/mess_stamps.png)
	
You won't get a neat grid of stamps.

This is because, right now, the `stamp sprite`{:class="blockmoreblocks"} block only runs for the total number of columns.
--- /task ---

--- task ---

Change your `stamp sprites`{:class="blockmoreblocks"} script so that it `repeats`{:class="blockcontrol"} enough times to stamp the complete grid of sprites.

--- hints --- --- hint ---
The total number of stamps you need is the number you give as `columns`{:class="blockmoreblocks"} multiplied by the number you give as `rows`{:class="blockmoreblocks"}
--- /hint --- --- hint ---
Use this additional block:
```blocks
((rows ::custom) * (columns ::custom))
```
--- /hint --- --- hint ---
Here's the completed `stamp sprites`{:class="blockmoreblocks"} script:
```blocks
define stamp sprites (rows) (columns)
set size to (40) %
+ repeat ((rows) * (columns))
set [index v] to (pick random (1) to (length of [x_positions v]))
go to x: (item (index) of [x_positions v]) y: (item (index) of [y_positions v]
delete (index) of [x_positions v]
delete (index) of [y_positions v]
stamp
next costume
```
--- /hint --- --- /hints ---

![ordered grid](images/nice_grid.png)
--- /task ---
