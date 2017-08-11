## Adding rows

- Now that you've written the code to generate a single row, you need to add in more rows.

- Go back to your `generate positons` block.

	![gen positions](images/script_19.svg)

- Now you need another loop that will repeat the same number of times as the number of rows you need. Place it into your script as shown below.

	![repeat for rows](images/script_20.svg)

- Next you need to increase the value of `y_pos`. This will increase up to a maximim of `150`, which is `300` away from it's starting value of `-150`. This needs to happen for each row your create.
