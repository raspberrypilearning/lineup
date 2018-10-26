## Finishing the game

--- task ---
To finish off, you'll need to find and download an image of [a curtain or a screen](https://www.google.co.uk/search?q=stage+curtain&source=lnms&tbm=isch&sa=X&ved=0ahUKEwjKg9O1k8_VAhXSL1AKHe1HDMIQ_AUICigB&biw=1362&bih=584).

This image needs to be imported as a second sprite.

[[[generic-scratch-add-sprite-from-file]]]
--- /task ---

--- task ---
To begin with, position the curtain sprite at `x:0 y:0` and then change its size so that it fills the screen. You also want to make sure it is visible.

```blocks
when flag clicked
go to x: (0) y: (0)
set size to (110) %
show
```
--- /task ---

--- task ---
Then, back on your character sprite, add a broadcast of `curtain up` to the end of the starting script.

```blocks
when flag clicked
clear
generate positions (4) (10) ::custom
stamp sprites (4) (10) ::custom
go to x: (0) y: (0)
go to front
set size to (100) %
say [Find me] for (2) secs
go back (1) layers
set size to (40) %
go to x: (item (1 v) of [x_positions v]) y: (item (1 v) of [y_positions v])
+broadcast [curtain up v]
```
On the curtain sprite, you need a script that will do the following:
  1. Bring the curtain to the front
  1. Wait a little bit while the sprites all get drawn
  1. Glide the curtain upwards so it's near the top of the screen
  1. Hide the curtain
  1. Start a loop that counts for 10 seconds
  1. When the time is over, show the curtain
  1. Glide the curtain back to its original position
  
--- no-print ---
Here's what it should look like:

![demo 2](images/demo_2.gif)
--- /no-print ---

Have a go at doing this yourself, and use the hints if you need help.

--- hints --- --- hint ---
Here's how you would start your script:
```blocks
when I receive [curtain up v]
go to front
wait (1) secs
glide (1) secs to x: (0) y: (300)
hide
```
--- /hint --- --- hint ---
Here's a simple script to create a delay of ten seconds. If the variable can be seen, it will let the player know how much time they have.
```blocks
when I receive [curtain up v]
go to front
wait (1) secs
glide (1) secs to x: (0) y: (300)
hide
+ set [timer v] to [10]
+repeat (10)
wait (1) secs
change [timer v] by (-1)
```
--- /hint --- --- hint ---
 Here's the full script:
 ```blocks
 when I receive [curtain up v]
go to front
wait (1) secs
glide (1) secs to x: (0) y: (300)
hide
set [timer v] to [10]
repeat (10)
wait (1) secs
change [timer v] by (-1)
end
+ show
+ glide (1) secs to x: (0) y: (0)
```
--- /hint --- --- /hints ---
--- /task ---


--- task ---
	The very last part is to let the player know if they've won. On the character sprite, if the sprite is clicked, it should say `You've found me`{:class="blocklooks"}, all the scripts in the game should be stopped.
--- /task ---

