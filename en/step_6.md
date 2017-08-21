## Stamping a row
- So far you have ten values in the two lists. Let's stamp some costumes to the positions in the list.

- Create a new block and call it `stamp sprites`. It needs two parameters as well, both number inputs and set to `row` and `columns` just like the last one.

	![new block](images/script_10.svg)

- Now create a new variable called `index`. You can use this to track which position in the list you are reading from. Set it to `1`.

	![index](images/script_11.svg)

- Now, you're going to stamp a sprite for each set of coordinates in the list. This will require a loop, that will repeat once for each column.

	![repeat it](images/script_12.svg)
	
- Next, within the loop, you can move your sprite to the first position in the list, stamp the sprite, then increase the `index` by 1.

	![stamp loop](images/script_13.svg)

- Next you need to call this block as well. You should add a `clear` block to you starting script so that it clears the stage each time.

	![stamp it](images/script_14.svg)
	
- When you click the green flag, you should see something like this:

	![stamped sprites](images/stamped_sprites.png)
