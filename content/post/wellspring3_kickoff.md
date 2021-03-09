---
title: "Wellspring 3: Kickoff!"
date: 2021-03-08T19:44:13-08:00
draft: false
---

The goal for this post is to kick off my development of Wellspring 3. 
Hopefully after this I’ll be posting regular, smaller updates as I develop the game. 
This will be a short one. 

At a certain point in Wellspring 2 prototyping, I realized I had a few issues with how the game was progressing and where it was headed. 

-	I thought that the game scope was getting too large for one person to develop, especially without a lot of experience. There was just too much to make. 
-	The technical aspects of networking a 3D first person game to work with low ping and preventing cheating were going to be hard to accomplish and take away from what I actually wanted to work on, which was game development. 
-	The 3D art required to make the game was going to be a lot, which was not going to be cheap and finding an artist or artists was not going to be easy.

I needed to look for a solution that would allow me to keep the characters and abilities I had thought of since I liked them but also enable me to make a game I could actually develop.
The solution came to me while playing [Fire Emblem: Three Houses](https://www.nintendo.com/games/detail/fire-emblem-three-houses-switch/) and being annoyed that I had to do so much school teaching in between fights.
I could make a 2D turn-based, grid-based tactics game.
Each of the characters I’d already developed had abilities that could be relatively easily translated into a 2D game.
The player would play as a tactician, controlling all 4 characters in a battle against the another player’s 4 characters.
I also am planning to use hex tiles instead of the square Fire Emblem ones. 
This should give players a bit more freedom of movement while keeping the game turn and grid based. 

This solved pretty much all of my problems in relatively easy ways. 
First off, with just 2D characters and a 2D map, the game will be much smaller in scope, since there just isn't as much stuff.
Because of this, I'll be able to spend a lot less time on assets and a lot more time making characters. 
Second, a turn-based structure just makes a networking setup a lot easier. 
Cheating is super hard because with a turn-based game because any information the client needs about the opponent can be requested from the server as needed instead of in advance. 
This gives any potential cheater no ability to try to look into the game executable and see information they shouldn't.
Networking a turn-based game also means I only need limited netcode and no rollback or other lag compensation and means that servers can be hosted wherever as the game would be agnostic to ping. 
Overall, the networking requirements are as barebones as I can think of, which is exactly what I'm going for. 
Finally, 2D art is easier to make, and from my very limited searches, a solid bit easier to find artists for as well. 

Overall, it took me a few iterations and a lot of learning by doing, but I think I have finally figured out a game that I’m excited to make and is within my abilities to make.
The goal time frame I'm setting for myself is 12 to 18 months, but we'll see how it goes. 
Can always move my goal, but it's just good to have one.
Thanks for reading and stay tuned for further updates and the first pics of the new game! 