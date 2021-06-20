---
title: "Wellspring3: Finished Core Technology"
date: 2021-06-20T13:40:15-07:00
draft: false
---

So it's been a while since I've last posted, but I'm finally back on the grind working on the game so I'm back with another update! 
When I left off about a month ago I had 2 main goals left to finish before I could get started on character design. 
Those (copy-pasted from my last post below) are now finaly done! 

1. Character attacking, attack range, and hitpoints, as well as making a target dummy. 
2. Basic UI development for seeing character HP, movement points, turn end button, etc. 

I'll go over what my techncial solutions are for them below and then look ahead a bit to what is coming up as I start character design. 

## Character Combat

The main technical challenge with attacking was allowing for characters with different ranges as well as updating the map tile highlighting system. 
The way attack ranges are noted is with a list of ranges, so if a character is melee their attack range is `[1]` whereas an archer would have a list of `[2]`. 
A character with a range of 1 hex or 2 hexes then can be noted as `[1, 2]`. 
This list is used to find the appropriate hex rings around the character using the Red Blob methodology shown [here](https://www.redblobgames.com/grids/hexagons/#rings). 

With the rings made, I then needed to be able to show them on the map.
The most straightforward way to do this was to highlight the tiles you can attack red.
Red is a color most people associate with attacking and is what previous similar games (e.g. Fire Emblem, Advance Wars) used for it so players should already understand the design language. 
I decided that for better clarity if the attack range was red, the movement range should be highlighted blue, with a line preview to show the exact path. 
I used the [Aseprite](https://www.aseprite.org) pixel art editor to add red and blue highlighting to the hex tile borders. 
I usually like to use [Paint.net](https://www.getpaint.net) for this stuff but I am developing on Mac and so Aseprite has been a great alternative.
I then just swap out the regular tiles for highlighted ones on the tilemap as needed based on the movement range. 

The line preview is done using the line creation tools I previously made along with the mouse position.
When a character is selected the pathfinding returns a dictionary containing all paths, and this is used to dynamically create the preview. 

Hitpoints are pretty straightforward to make, just a class member to store the hitpoints and another to store the attack damage. 
Then when the character is attacked their `OnAttack()` function is called and the character being attacked takes the appropriate damage. 
There are no armor or other damage mitigation mechanics at the moment, though I do have plans to add those kinda things.

## Basic UI Development

The goal for this basic UI was just to create an information display so the game is playable. 
To make the UI I had to learn how to use the Godot UI system. 
I found these two YouTube videos (shown below) particularly helpful with learning the basics of how all the anchors and containers work. 

1. [Godot 3.2: Let's Build a 2D Platformer!: Part 12 (Coin HUD, Custom Signals & Fixing Double-Collect)](https://www.youtube.com/watch?v=XITNApxoIes&t=630s)
2. [Introduction to UI Containers in Godot 3 (tutorial)](https://www.youtube.com/watch?v=YL8apqN6IJM&t=344s)

Once that was done I was able to block out a basic UI. 
It has a placeholder at the top for showing the characters on your team and a minimap placeholder.
Beacuse the game is still basic enough that those aren't really necessary, I just used placeholders. 
The only reactive elements are on the bottom left and show hit points (HP), Action Points (AP), and the current turn.
As more combat statistics (e.g. armor, spell power, spell resist) are added, they'll be added to the UI as well. 
The font used for the UI elements is called [Major Mono Display](https://fonts.google.com/specimen/Major+Mono+Display). 
It's not the most readable so I'm not sure I'll keep it forever but it's fun and I like it so it's there for now. 

![Wellspring3 Basic UI](/wellspring3_finished_core_tech/wellspring3_ui.png#center)

Something I need to add but have not yet is a turn end button. 
That said the spacebar can be used for it so it's not the worst at the moment to not have it. 

## Game Manager Upgrades

I have a `Game Manager` class that takes care of things like character selection and managing turn ends and starts. 
In order to populate the game with characters, I added the functionality to create 10 characters and add them to the map. 
I ran into an interesting issue where I wanted to create the 10 characters from some Godot scene (`.tscn`) files. 
However, in Godot you can't initialize any member variables if you create nodes this way, and I had some member variables I needed to assign before using the class. 
I got around this by creating and calling an `init()` function right after creating the character nodes. 
However, this function will get called before the `Ready()` function is called for the class, so the things you can do with this method are limited since nothing is initialized.
For just initializing member variables though, this method works great. 

I also updated the game manager to be able to swap between the two teams being the controllable team.
This allows 2 people to play the game on one computer using the same screen.
When one person's turn ends the other person's begins. 

## Gameplay Video

I took a video of the current state of the game! 
As a note, attacking doesn't have any animations or anything yet, so it's basically impossible to tell if someone is attacking. 
Attacking takes 4 action points, so you can see by watching that bar. 
Attacking does 10 damage and the red enemies have 20 hitpoints.
2 attacks from the blue team will kill them, upon which point they disappear.

{{< youtube LiQASfYhTJU >}}

## Next Steps 

Now that I have this baseline level of tech, I can get started on the character design, which is what I originally started this for. 
The goal is to make 5-10 unique playable characters that have high levels of synergies between them. 
I want this game to be about drafting compositions of characters that work well together and either synergize amongst themselves or counter the enemy team. 
I'm thinking each character will have one basic ability with a short cooldown and one ultimate ability with a long cooldown. 
They'll also be able to basic attack, which is the functionality I've already added.
As always, thanks for reading and stay tuned for the next post! 