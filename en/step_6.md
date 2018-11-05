## Stamping a row
- So far you have ten values in the two lists. Let's stamp some costumes at the stage positions given in the list.

- Create a new block and call it `stamp sprites`. It needs two parameters as well, both of which should be number inputs and named `row` and `columns` just like the last ones.

	![new block](images/script_10.png)

- Create a new variable called `index`. You can use this to track which position in the list you are reading. Set it to `1`.

	![index](images/script_11.png)

- Now you're going to stamp a sprite for each set of coordinates in the list. This will require a loop that will repeat once for each column.

	![repeat it](images/script_12.png)
	
- Within the loop, move your sprite to the first position in the list, stamp it, then increase the `index` by 1.

	![stamp loop](images/script_13.png)

- Next you need to call this block as well. You should also add a `clear` block to you starting script so that it clears the stage each time.

	![stamp it](images/script_14.png)
	
- When you click the green flag, you should see something like this:

	![stamped sprites](images/stamped_sprites.png)
