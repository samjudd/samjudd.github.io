---
title: "Wellspring 2: Introduction and Map Development"
date: 2021-03-06T15:03:50-08:00
draft: false
---

## From Wellspring 1 to Wellspring 2

Basically, I moved away from Wellspring 1 to another version to make the game development easier for myself. I am only one person, and I wanted to make something I could actually finish. 

One of the biggest changes I made was moving from [Unity](https://unity.com) to the [Godot Engine](https://godotengine.org). Here’s why I did it:

- I like using it. The UI and organization make sense to me, or at least more sense than Unity. 
-	Godot is a much more lightweight engine. It just takes up a lot less space on my computer and opens, closes, and updates faster. This is pretty nice. 
-	 I like the idea of supporting and using an open source engine. Hopefully this is the way of the future. 
-	Using this engine doesn’t tie me to Unity and having to pay for it (if I could ever sell a game) forever. 
-	Because Godot can be scripted in C#, the transition to Unity is not too painful if it ever became necessary for some reason. 
-	I am okay with taking the hit in terms of graphics performance and a smaller engine feature set for the above benefits. If I need features or rendering performance that Godot doesn’t have, I’m probably getting outside of what I can do by myself anyway.

Another big change I made was that I moved away from the 1v1 dueling concept that I had been looking into in during the Wellspring 1 era. My main issue was just that I didn’t think it would be as fun without VR. Without the freedom of VR to swing your sword and shield anywhere, I don’t think a sword duel would be nearly as fun. I thought it would end up looking a lot like [For Honor](https://forhonor.ubisoft.com/game/en-us/home/) or [Chivalry](http://tornbanner.com/chivalry/), which I liked but didn’t love. Not to mention, does the world need a third one of those? I didn’t think I’d be bringing anything new to the genre. 

At this point in my development (summer/fall 2020), COVID was in full force and I was spending a lot of time on a number of different online games, mostly from Riot. The big ones for me were [League of Legends](https://na.leagueoflegends.com/en-us/) and [Teamfight Tactics](https://teamfighttactics.leagueoflegends.com/en-us/), though I also dabbled in [Valorant](https://playvalorant.com/en-us/), [Overwatch](https://playoverwatch.com/en-us/), and [DOTA 2](https://blog.dota2.com/?l=english). These games were a great way to stay in touch with my friends who lived far away and/or were near but quarantining for one reason or another. These games had a big influence on me. Because of them I wanted to make game where people would be able to have fun and compete together. 

Although the single player queue systems of all of the games listed above allow players to play whenever they want which is great, solo queueing has some drawbacks in my mind. 

-	It makes a ranking system hard, a player can play well and still lose games, and so progress climbing can be very slow and frustrating. 
-	Having random teammates opens up the door to a lot of toxicity due to poor communication and people just generally being more bold hidden behind their keyboards
-	It reduces the general level of the game being played. Playing in single player queues becomes a different skill from playing the game as a coordinated team. 
-	It makes it hard to balance characters in the game. In competitive play they are being played on comms with great deal of coordination and communication while in casual there is a much lower level of both of these things. 

Because of these drawbacks and the fact that most of the games that make up the mainstream using single player queue for a team game, I thought that making game meant to played as a team with friends would be a more unique/interesting direction to go. Another fun but underused game that I loved playing in the past in various Halo games was capture the flag. So I decided this could be the basis for my new game. Capture the flag, with the game centered around the team of 4 as the competitive and casual group. 

## Wellspring 2 Concept

At its core, my concept for Wellspring 2 is 4v4 capture the flag but with 3 (this number, along with all the others, open to change in playtesting) flags instead of 1. I think capture the flag is a pretty fun game mode that isn’t done a lot in modern multiplayer games that has lots of room for both fighting and strategic outplay. I think there can be a lot of complexity to trying to balance getting the other team’s flags while also protecting your own. And stealing a flag requires not only getting to it but then getting out with it alive. There are lots of ways to (for example) steal a flag, and that allows for lots of creativity and high-level play. Making the mechanics a player uses to interact and rules as simple as possible makes the game accessible to beginners. 

The basic rules for the game were:
1. The game is played on a symmetrical, rectangular map, described in more detail in the Map Design section below. 
2. The game is over immediately when one team captures all three of the other team’s flags or when a predetermined time limit is reached. Winner is whoever has more flags when the game ends. 
3. The map has fog of war, so only places within a player’s vision range or revealed by friendly abilities or structures can be seen. This makes scouting and the vision game important. 
4. Carrying the flag causes that character to be unable to fight (since they are carrying the flag), so they will need help escaping most of the time. This helps make thievery not just a one player mission.  

The way this would be played competitively online is that rosters of up to 7 people would be able to be formed to compete. Any subset of four of this 7-person roster would be able to queue into a game representing the same group. Players can be a part of more than one team at a time. This team would be able to play games and would have an [ELO](https://en.wikipedia.org/wiki/Elo_rating_system)-like score that would be adjusted for each win/loss based on the opposing team’s ELO.

Before I get into the map design, when I was designing the map, and later characters as well, I kept two main tenets in mind. 

1. The more impactful a mechanic is, the more risk you should need to take to use it.
2. Mechanics should be at their most impactful and least risky when well used in combination with other players. 

## Map Design

I had two ideas for maps that could be used for the game. The main feature they each share is that most of the map is covered in forest. I think this is a good feature because it allows players to hide their location. This is essential to creating gameplay where teams need to scout for each other and can use this fog of war to play tricks and strategies on the other team to gain the upper hand. This also allows me to create barren areas of high risk where a player can’t see into the forest but a player in the forest can see into the plain. These areas are places where fighting is easier to execute (no trees in the way of movement/abilities/vision) and with greater risk can come greater reward in terms of objectives for entering them. Within this forest are various smaller objectives that are able to be captured and/or destroyed to gain a greater strategic advantage by either team before moving to end the game.  

I’ll go through my first prototype map first before I get to the second prototype I eventually decided to use. Hopefully this gives a bit of an understanding of my thought process in mapmaking. 

### Asymmetric Map Prototype
The first map I had was based around an asymmetrical siege game mode. One team would be protecting a citadel from another team trying to invade and destroy it. The green area is forested while the tan area immediately around the citadel is not forested. 

![Asymmetric Map Prototype](/circle_map_2.png)

As can be seen in the map, the red team would spawn somewhere on the outskirts of the circle and would have to invade the citadel and try to capture it. The blue team would spawn in the central citadel and would have to ascertain where the red team was coming from and defend for a specified length of time. 

To prevent the blue team from being able to just camp in their base, there are 2 mechanics that would hopefully incentivize them to leave. One is shown as the 3 black circles, the shield generators. I’m not sure what they exactly would do, but the idea would be that there are some inherent defenses to the citadel that would get increasingly weak with each generator destroyed. Further out than that, there are supply caches that would be able to be collected to upgrade a player’s character’s abilities for the duration of the match. With these objectives in place outside of the citadel, there becomes a real tradeoff between playing defensively and just waiting for the offensive team to get to the citadel and moving out and scouting to get supplies and information on the location of the enemy team in the forest. 

On the offensive end, there are different benefits to going straight for supplies, going straight for the generators, or even trying to sneak into the base if the entire defensive team is out scouting and getting supplies. On both offense and defense, these strategies can be further explored because a team of 4 can split up and look to try to do multiple things at once. I think this open-ended gameplay without super well-defined roles or ways to accomplish the goal allows for lots of fun strategic decisions and outplays that are both fun to figure out and to watch. 

One downside to this game mode is that it is asymmetrical, so in order to play a fair competition, each team has to play each side. Additionally, if both teams win once, I am not sure in this system how to tiebreak in a way that is fair. A third game with offense/defense being randomly selected is one possibility but won’t work well unless both sides are very well balanced. If games are about 20 minutes long, this could make a single play session as long as an hour which is a lot to play without a break. For these reasons, I decided to try and take as many parts of this map as I could and bring those elements into a second map that is symmetrical. 

### Symmetric Map Prototype

This second prototype tried to take a lot of the core concepts I already had for the siege game map and use them to make a symmetrical game mode. This resulted in the siege mode turning into the capture the flag mode I previously discussed. I thought this maintained a lot of the same concepts of trying to either sneak into the base or just straight invade it, but allows both teams to look to both steal the flags and defend their own. 

![Symmetric Map Prototype](/rectangle_map_3.png)

Both teams would start the game in their own bases. Each base is protected by some turrets and an alarm system that alerts if a member of the other team is detected in the base. Placed on a road through the forest are 2 generators for each team. Destroying either generator will deactivate the turrets, while destroying both will deactivate both the turrets and the alarm system. These generators are unable to be rebuilt. The idea behind these generators is to create a secondary objective to fight over besides the main base and to slow the game down a bit so an immediate base rush is hard to accomplish without accomplishing this intermediate objective. 

The roads create some easier pathways to travel that are faster going than the forest, but also more dangerous, as a player may not be able to see well into the forest, while people from the forest can see them. The tradeoff for this is that they allow for faster travel so they may be useful when traversing the map to get to objectives. 

The supply caches work the same way as in the previous idea, where they give a boost to a character’s power to get. That said, this map has the addition of a 3x normal power supply cache at the very center of the map, in the middle of an exposed, treeless area. This is also designed to be somewhere that an objective that is not the main one can be fought over. However, this cache could also be traded for the four smaller ones on the outskirts that are collectively worth more (4 caches total versus 1 3x one) if a team does not look to get them. Another option to consider is that instead of having 4 caches in predetermined locations, there could be random caches placed throughout the forest. This creates some interesting play with both teams looking for the caches. The randomness would have to be such that it does not create situations where one team is outright favored due to cache positioning in more favorable locations. 

I liked this map a bit more since it made the game symmetrical, so it makes best of 1 and best of 3 a bit easier to execute. It also means there is not as much work to balance the asymmetry of the game so both sides are equally difficult but different. This simplifies the game a bit more and makes it easier to develop and understand. For this reason, I decided to go with this second prototype as the main version of the map. 


## End of Post

Thanks for reading this post! I will continue in the [next post]({{< relref "wellspring2_character_design.md" >}}) to talk about character design in Wellspring 2. 