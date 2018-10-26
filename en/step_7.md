## Adding rows

Now that you've written the code to generate a single row, you need to add in more rows.

Go back to your `generate positions`{:class="blockmoreblocks"} block.

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
Now you need another loop that will repeat the same number of times as the number of rows of stamped costumes you need. Place it into your script as shown below.

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

--- task ---
- Next you need to increase the value of `y_pos`{:class="blockdata"}. This will increase up to a maximum of `150`{:class="blockdata"}, which is `300`{:class="blockdata"} away from its starting value of `-150`{:class="blockdata"}. This needs to happen for each row your create.

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
- Then you need to make sure you're passing the number of `rows`{:class="blockmoreblocks"} as a parameter to your blocks.

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

This is because your `stamp sprite`{:class="blockmoreblocks"} block is only repeating for the total number of columns.
--- /task ---

--- task ---
Alter your `stamp sprites`{:class="blockmoreblocks"} script. It needs to repeat enough times to stamp all the sprites.

--- hints --- --- hint ---
The total number of stamps you need will be the `columns`{:class="blockmoreblocks"} multiplied by the `rows`{:class="blockmoreblocks"}
--- /hint --- --- hint ---
Try using this additional block
```blocks
((rows ::custom) * (columns ::custom))
```
--- /hint --- --- hint ---
Here's the completed script:
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
