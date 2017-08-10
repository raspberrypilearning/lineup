## Making a grid

- In this game, your going to produce a grid of stamped costumes, just like the one below.

	![stamps in grid](images/stamp_grid.png)
	
- To do this you will need to know the `x` and `y` coordinates where each stamp is going to be placed. Have a look at the section below if you need a reminder about Scratch coordinates.

[[[generic-scratch-coordinates]]]

- To begin with you'll need to create a new **block** called `generate positions` for you spite. The block will need to have **two** `number inputs` *parameters*. Call the two parameters `rows` and `colums`.

	![generate positions block](images/generate_positions.svg)

[[[generic-scratch-make-block]]]

- Next you will need to create two lists. One will be called `x_postions` and the other will be called `y_positions`.

[[[generic-scratch-make-list]]]

- Underneath your `generate_positions` block, add blocks to delete **all** from both lists.

	![empty the lists](images/empty_lists.svg)

- Next you will need two new variables. Call these `x_pos` and `y_pos`.

[[[generic-scratch-add-variable]]]

