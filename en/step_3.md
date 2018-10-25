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

[[[generic-scratch-make-list]]]
--- /task ---

--- task ---
Underneath your `generate positions`{:class="blockmoreblocks"} block, add blocks to delete all the items from both lists, so taht each time the game is played, the lists are empty and new.

```blocks
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
```
--- /task ---

--- task ---
Next you will need to create two new variables. Call these `x_pos`{:class="blockdata"} and `y_pos`{:class="blockdata"}.
--- /task ---

If you look at the two lists side by side, as shown in the table below, you will see that the first item in the list will be coordinates for the bottom left-hand corner of the stage. The next one will be a little bit to the right, and so on as `x_positions`{:class="blockdata"} gets larger.

|index|y_positions|x_positions|
|-----|-----------|-----------|
|1    |-150       |-200       |
|2    |-150       |-155       |
|3    |-150       |-111       |
|4    |-150       |-66        |
|5    |-150       |-22        |
|6    |-150       |22         |
|7    |-150       |66         |
|8    |-150       |111        |
|9    |-150       |155        |
|10   |-150       |200        |


The table shows the coordinates of the *first* row of images. They could be added to the lists manually, but that would take a little too much time. It's easier to do it with a loop.

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
Now you need a loop to add some coordinates to the lists.

How many times should the loop repeat?

In this case it is ten - one time for each column in the grid. As you've set up the custom block to take `columns`{:class="blockmoreblocks"} as a parameter, you can use this value.

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

The first value you add is `-200`{:class="blockdata"} and the next is approximately `-155`{:class="blockdata"}. The value keeps on getting larger, up until you reach `200`{:class="blockdata"}.

So how can you do you know how much to add? 

As you want a total of ten values in the list, and the first is already set to `200`, you need an additional nine values. This is the value of `columns`{:class="blockmoreblocks"} minus one, so `columns - 1`{:class="blockoperators"}. 

You want to go from `-200`{:class="blockdata"} yp to to `200`{:class="blockdata"}, so that is an increase of `400`{:class="blockdata"} to the `x_pos`{:class="blockdata"}.

This means you want to add `400 / (columns - 1)`{:class="blockoperators"} each time the loop comes around.

--- task ---
Here's some code to get you started, and you can use the hints below if you need more help.

```blocks
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
set [x_pos v] to [-200]
repeat (columns)
add () to [x_positions v]
add () to [y_positions v]
change [x_pos v] by ((() / ()) - ())
```
	
--- hints --- --- hint ---
- Start by adding the variable values into the lists.
```blocks
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
set [x_pos v] to [-200]
repeat (columns)
add (x_pos) to [x_positions v]
add (y_pos) to [y_positions v]
change [x_pos v] by ((() / ()) - ())
```
--- /hint --- --- hint ---
- Now use the `columns` parameter to calculate the number of repeats.
```blocks
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
set [x_pos v] to [-200]
repeat (columns)
add (x_pos) to [x_positions v]
add (y_pos) to [y_positions v]
change [x_pos v] by ((() / (columns)) - ())
```
--- /hint --- --- hint ---
- Lastly you can add in `400` to the calculation, so it calculates the increase in `x_pos` each time.
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



