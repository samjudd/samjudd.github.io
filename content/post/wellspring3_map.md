---
title: "Wellspring3: Hex Map Creation"
date: 2021-03-29T12:12:21-07:00
draft: false
---

This is my first blog post for work I'm doing actually right now as opposed to catchup. 
Very exciting! 
I started out this week working on making a hex map for Wellspring3 in [Godot](https://godotengine.org). 
The great part about using Godot was that they already have a [TileMap](https://docs.godotengine.org/en/stable/tutorials/2d/using_tilemaps.html) class ready-to-go for creating tilemaps. 
It enables you to create and save sets of tiles to use for the map as well as place, rotate, and access tiles via code. 
Unfortunately, it is missing a couple critical features for creating hex tilemaps. 
The main issue is that it doesn't actually support a hex grid, only a square one. 
Secondly, Godot doesn't support custom properties for tiles. 
This means that say some tiles cost twice as much to move across as others, there's no way for Godot to store this natively. 
This just meant that I had to develop these features myself. 

## Square Grid -> Hex Grid

In order to create a useable hex map, I needed to create the features below. 

1. I need to be able to tile hexes in the editor (as opposed to squares) and have them line up properly. 
2. I need to be able to click on the screen and know which tile I'm clicking on so that it can be selected. 
3. If I have a given amount of movement points I need to know which hexes I can reach. 

### Tiling Hexes
The Godot TileMap implementation has an option for a `Half Offset` that basically offsets every other row/colum by half a tile width.
This is perfect for making hex maps. 
Setting this `Half Offset` property to `Offset Y` offsets every other square column which is what I used. 
The picture below shows both the underlying square grid (super faint orange lines) and the hex tiles. 
Note that because they are hexes the dimensions of the square tiles are actually smaller than the hex. 
I have `140 x 120 px` tiles and the square dimensions are `104 x 120 px` to tile the hexes properly. 
I just determined this by changing the `104` until it looked right. 

![Half Offset Example](/wellspring3_map/half_offset_example.png#center)

### Screen-to-Hex Conversion
Godot TileMap has a function to convert screen clicks into tile clicks, but this works on the square grid, which as can be seen does not line up with the actual hex tiles. 
Luckily, [Red Blob Games](https://www.redblobgames.com/grids/hexagons/#pixel-to-hex) had some instructions on an implementation for converting pixel coordinates to hex coordinates. 
I was just able to directly implement the pseudo-code on the site for `pixel_to_hex` and `hex_round`, since this application didn't require any modifications. 

### Hex Map Pathfinding
I needed an algorithm that could search the hex map I had for all reachable points given that tiles could have different costs. 
This was done through implementing Dijkstra's algorithm. 
Once again, Red Blob Games had some great resources [here](https://www.redblobgames.com/pathfinding/a-star/introduction.html#dijkstra) and [here](https://www.redblobgames.com/grids/hexagons/#pathfinding) that I used. 
A quick but important side note is that C# does not have a native priority queue implementation, so I used Nuget to download [this](https://www.nuget.org/packages/OptimizedPriorityQueue/) one. 
I modified the pseudo-code shown in the first link slightly to use a different function to find neighbors since the hex map has different neighbors than a square grid. 
The neighbors function description can, unsurprisingly, also be found at Red Blob Games [here](https://www.redblobgames.com/grids/hexagons/#neighbors). 

I needed to make one more change to the algorithm described on Red Blob because the goal of my search is to find all hexes within range rather than the shortest path to a specific hex. 
The algorithm as shown ends when the goal location is found. 
My implementation instead ends when all hexes that are reachable have been visited. 
This is done by giving a max range of hexes to search and then only adding new hexes to the frontier to explore if the cost to reach them doesn't exceed the max range. 
The Dijkstra iteration then ends when the frontier is out of possible hexes to explore. 
The results of the pathfinding algorithm are shown below. 
Grass hexes have a movement cost of 2, forest hexes 4, and the total movement range is 8.
The start hex is in the middle and highlighed with a tan border, and the blue lines show paths to all possible hexes.  

![Pathfinding Example](/wellspring3_map/pathfinding_example.png#center)

## Storing Custom Hex Properties

The other major task to finish my hex map implementation was a way to store custom properties for each hex.
The main relevant property that Godot stores for each hex is an ID number that identifies which sprite is used as the hex model. 
I loop through each hex in the map and pull the ID and location for it. 
I then use a dictionary I create elsewhere to map each ID to the amount of (base) movement points that it should cost to traverse that hex. 
I then store these in a 2D array so that hex property lookup is as easy as indexing into the hex location in the array. 
This is implemented in C# as a `List<List<HexTile>>`. 
Hex information is stored in the 2D array as a custom `HexTile` object so that the custom properties can be expanded as needed to accomodate whatever the game requires. 
Because the location of the hex is also the way to index into the array, I use `[0,0]` as the top left of the map so there are no negative locations that would make negative indices. 

Working with C# lists for the first times, I learned that allocating capacity to the list does not make you able to index into a spot in that list, you actually need to put an object there first. 
So `List<T>[x] = T` won't work but `List<T>.Insert(T, x)` will if there is not something there already. 
Hopefully this might be useful for someone else. 

I also had to write a custom function for detecting if a tile exists in the map, since I can't use the existing `List<T>.Contains()` function with a list of lists. 
My custom contains function basically checks that the x and y location that was clicked is non-negative and within the bounds of the map. 
Having confirmed that the location in the array has been populated, I can then index into that location and check if the tile ID is not `-1` since that is the "no tile" ID. 

## Next Work
Now that I have what I'd consider a minimum viable product for a functional map, the next to-do is to create the basic framework for a character.
My initial thoughts on what the character needs to be able to do is shown below.
1. Able to move from hex center to hex center along the paths determined by Dijkstra's algorithm. 
2. Show its attack range. 
3. Store custom properties for the particular character.
4. Be able to be selected and deselected.
5. Reset its movement/action points upon a new turn. 

The full source code for this project can be found in my github in the [wellspring3](https://github.com/samjudd/wellspring3) repo.
As always, thanks for reading. 