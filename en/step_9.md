## Finish the game

--- task ---

To finish the game, [find and download an image of a stage curtain](https://www.google.co.uk/search?q=stage+curtain&source=lnms&tbm=isch&sa=X&ved=0ahUKEwjKg9O1k8_VAhXSL1AKHe1HDMIQ_AUICigB&biw=1362&bih=584){:target="_blank"}.

Import this image as a sprite.

[[[generic-scratch3-add-sprite-from-file]]]

--- /task ---

--- task ---

Position the new curtain sprite at `x:0 y:0`{:class="block3motion"}, and then change its size so that it fills the screen. Make sure it is visible.

```blocks3
when flag clicked
go to x: (0) y: (0)
set size to (110) %
show
```

--- /task ---

--- task ---

Then, in the scripts for your character sprite, add a `broadcast`{:class="block3events"} with the message 'curtain up' to the end of the `when flag clicked`{:class="block3events"} script.

```blocks3
when flag clicked
erase all
generate positions (4) (10) ::custom
stamp sprites (4) (10) ::custom
go to x: (0) y: (0)
go to front
set size to (100) %
say [Find me] for (2) seconds
go back (1) layers
set size to (40) %
go to x: (item (1 v) of [x_positions v]) y: (item (1 v) of [y_positions v])
+broadcast (curtain up v)
```

--- /task ---

--- task ---

When the curtain sprite receives the `broadcast`{:class="block3events"}, the sprite needs to move upwards for 10 seconds so that it looks like the curtain is raised to reveal the stamps. Then the curtain should drop again, so the curtain sprite needs to move downwards.

--- no-print ---

It should look like this:

![Demo showing the curtain raising to reveal the sprites behind it, after a pause the curtain comes back down again.](images/demo_2.gif)

--- /no-print ---

Try to do this by yourself, and use the hints if you need help.

--- hints ---
--- hint ---

 This is the completed script:
 
 ```blocks3
when I receive [curtain up v]
go to front
wait (1) seconds
glide (1) secs to x: (0) y: (300)
hide
set [timer v] to [10]
repeat (10)
wait (1) seconds
change [timer v] by (-1)
end
show
glide (1) secs to x: (0) y: (0)
```

--- /hint ---
--- /hints ---

--- /task ---

The very last part is to let the player know if they've won.

--- task ---

In the scripts for the the character sprite, add code so that, when the sprite is clicked, the sprite says `You've found me`{:class="block3looks"}, and all the scripts in the game stop.
	
```blocks3
when this sprite clicked
say [You found me]
stop [all v]
```

--- /task ---

