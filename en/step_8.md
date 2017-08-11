## Adding rows

- Now that you've written the code to generate a single row, you need to add in more rows.

- Go back to your `generate positions` block.

	![gen positions](images/script_19.svg)

- Now you need another loop that will repeat the same number of times as the number of rows you need. Place it into your script as shown below.

	![repeat for rows](images/script_20.svg)

- Next you need to increase the value of `y_pos`. This will increase up to a maximum of `150`, which is `300` away from it's starting value of `-150`. This needs to happen for each row your create.

	![increase y](images/script_21.svg)
	
- Then you need to make sure you're passing in the number of `rows` as a parameter to your blocks.

	![parameters](images/script_22.svg)
	
- If you run your code now, you won't get a neat grid of stamps.

	![mess of stamps](images/mess_stamps.png)
	
- This is because your `stamp sprite` block is only repeating for the total number of columns. It needs to repeat for the product of the number of columns and the number of rows (`columns * rows`)

	![ordered grid](images/script_23.svg)
	![ordered grid](images/nice_grid.png)
