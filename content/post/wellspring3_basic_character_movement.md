---
title: "Wellspring 3: Basic Character Movement"
date: 2021-04-18T14:44:03-07:00
draft: FALSE
---

## Wellspring 3: Basic Character Movement

Quick update for now, I was able to get character movement working last week, as well as cleaning up a lot of the code that I had to make the interface a little easier to use and expose the right things. 
From a couple weeks ago, I had left 5 goals for the next steps in the game. 
I did pretty well, and this update finishes off goals 1-3 and goal 5 listed below (from the end of last post). 

1. Able to move from hex center to hex center along the paths determined by Dijkstra's algorithm. 
2. Show its attack range. 
3. Store custom properties for the particular character.
4. Be able to be selected and deselected.
5. Reset its movement/action points upon a new turn.

### Character Selection 

In order to select characters, I decided to create 2 classes, a `GameManager` class that oversees all the characters in the game and a `Character` class that has one instance for each character. 
`Character` can be both used as a template for making more advanced classes for the actual game and used on its own for testing (which is what I'm doing now).
Each `Character` can also store custom properties as well as it's own movement points.
`Character` then defines an `OnTurnEnd()` function that is common to all characters that is called when the turn ends and is used to reset action points and do any other actions. 
An `OnTurnStart()` function will likely also be used but not implementing it yet until I have a use for it. 

In order to then select one of these characters, the `GameManager` monitors for when the map is clcked and when it is gets from the map what tile was selected.
Each tile stores if there is a character on it and if so what character ID number, and so from there the right character can be pulled from a character list also stored in the `GameManager`. 
When a character is selected, the movement algorithm is automatically run to show their movement range.
At the moment for testing, each character is shown with 8 movement points, where a tile costs 2 to move across and a forest tile costs 4. 

### Character Movement

Character movement was pretty straightforward to implement. 
I first changed the way the pathfinding algorithm worked slightly so it returned the dictionary it created for pathfinding. 
This dictionary contains each hex that was visited by the algorithm along with the hex the algorithm (Dijkstra) came from. 
This makes it possible to basically start at the destination, which we know must be in the searched locations since otherwise it can't be selected, and backtrace to the start and return that path. 
Once the path is created, each node to travel to is put into a queue. 
This queue is then used in the `Process()` (runs every frame) function to control where to travel to. 

In the `Process()` function, a linear interpolation is used to move the character sprite between its current location and the next one from the queue of locations to travel to. 
Once the sprite gets to each location, the next one is pulled from the queue and the sprite is moved until the queue is empty.
At this point the move is complete. 

An improvement I'd like to make at some point is to change the interpolation scheme from a linear interpolation to a different one. 
A different movement scheme (for example a quadratic interpolation instead of a linear one) might do a better job of making the movement seem more natural. 
At the moment however I'm more interested in just having a minimum viable product, so I'd rather spend my time creating new features rather than polishing ones I already have in a functional state. 

### Implementation Video 

A video of the implementation is shown below. 
I still need to get to implementing a UI, so it's a bit hard to tell at the moment what is going on, I've added some notes in the video to try to make it clearer. 

{{< youtube py6jiAbyPAE >}}

## Next Steps

Now that I have some basic movement down, my development options have opened up a little bit. 
I've identified a couple key categories of things I need to flesh out next, listed below. 
Look for my next update to be in one of these areas.

1. Character attacking, attack range, and hitpoints, as well as making a target dummy. 
2. Basic UI development for seeing character HP, movement points, turn end button, etc. 

Once I get both of these tasks done, this should finish out the basic tools necessary to start creating some unique characters and creating a full map. 
Will be able to get into the actual game design at that point and give some more interesting thoughts than just implementation details, so very excited for that. 
As always, thanks for reading, and the source code for this can be checked out on my github [here](https://github.com/samjudd/wellspring3). 