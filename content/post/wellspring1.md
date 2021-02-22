---
title: "Wellspring 1: My First Attempt at a Game"
date: 2021-02-21T13:11:26-08:00
draft: false
---

## Introduction

On the advice of my brother, I decided to start writing up about my work developing a game by myself. So here goes. I started working on this a long time ago, so this work goes all the way back in time to September-ish 2019. 

I have always enjoyed playing games a lot (some would say too much) and after working in the aerospace industry for a few years I sorta decided that it is not really my life’s passion. I had taken a few classes in video game development in college and so decided to try this out. I was looking to create a game that I would have fun playing and would be good as a sort of community game to play. 

-	I wanted a game that I could play PvP competitively with a ladder
-	I wanted the game to be in VR, since I thought it was a really cool new part of games that had not been very explored yet (I still believe this, but the barrier to entry is high) 
-	I wanted the game to be intuitive to watch, as in someone who does not know how to play can watch and generally understand what is good and bad, who is winning and losing

I really liked [Pacific Rim](https://en.wikipedia.org/wiki/Pacific_Rim_(film)) (the 2013 Guillermo del Toro masterpiece), so something that I had been running around in the back of my mind for a while was a 1v1 mech battler arena game sorta like the robots (jaegers) in the movie. So I bought a quest and got to work playing some games just to get a sense of what was out there. I don’t remember all the games I played, but some did stand out. Beat saber was probably my favorite, but I also played a fair bit of rec room and dead and buried II with friends. I think what I took away from that experience was what forms of movement and interaction felt more natural/immersive. With the technology of VR being limited to headsets and hand controllers / hand tracking, movement is the area where a developer has to be creative with how they either skirt around it. Beat saber and dead and buried solve this problem by not having the player move. The “notes” come to you in beat saber and in dead and buried you are sitting behind cover the entire time. When I played rec room however, you could move around either by teleporting or by using the control stick to move. I found the control stick disorienting while the teleporting took me out of the fantasy of being truly in another reality. Another game that I found did it a lot better was the climb. There your motion is contextualized through the climbing mechanic. You are moving through the world, but not in a way that is as disorienting as just pushing a control stick. 

Reading about why this is the case, I stumbled on a few articles that seemed to detail some of the reasons why. One commonality I saw across a few articles [[Wired](https://www.wired.com/2015/04/reduce-vr-sickness-just-add-virtual-nose/), [Gamasutra](https://www.gamasutra.com/blogs/AlexRiviere/20170620/300275/How_Do_You_Design_Your_VR_Game_Around_Motion_Sickness_Constraints.php), [ARVILab](https://vr.arvilab.com/blog/combating-vr-sickness-debunking-myths-and-learning-what-really-works	)] was that a cockpit or some sort of reference frame seemed to help with movement. Mechs fit great with this because a person can be easily put in a cockpit to contextualize the motion, so that was pretty fortuitous. Other than this, a lot of preventing motion sickness seems to just come down to keeping a high framerate and avoiding rapid accelerations, especially up and down. The cause for avoiding these accelerations is they generally come with a feeling to your body, that for obvious reasons won’t come. Once again, making an immersive VR game seems to go hand-in-hand with making a game that won’t make you sick. Therefore I was able to add a couple more constraints to what I wanted to develop. The mechs can’t accelerate too fast, and the art needs to be a style that can accommodate high performance. 

## Gameplay/Combat

With this information, I was able to make the first basic ideas of what my game would look like and start prototyping. The basic concept was that the player is a mech pilot, inside of a mech, fighting another mech and pilot combo in 1v1 combat. The main controls for the game are the controllers, which the headset can track in 3D space relative to the headset itself. The player starts holding the controllers in front of them similar to this picture (this is not me). 

![Player Position](/player_position.png)

The player can move the mech through moving the controllers as though they are control sticks by pushing them forward and back, as shown in the diagram below. 

![Controller Position Diagram](/controller_position_diagram.png)

What makes this control system unique is that in addition to the controllers serving as the movement system, they also serve as the main combat controllers. By pressing on the grip button on the controller, the position of that hand stops controlling movement and starts to control the corresponding hand on the mech. When using only one hand to control the mech, the player can still strafe and do forward/backwards motion (no rotation), but with only 70% of the speed/acceleration as previously. This creates a number of interesting decisions/tradeoffs for the player to manage as they’re fighting and adds a level of mechanical growth to master. When an arm of the mech is not controlled, the arm just freezes in position. This enables a player to, for example, place both hands in a blocking position and then leave them to block while transferring control to the locomotion to retreat with both hands at full speed. Or fight with one hand while moving with the other. I am not sure how fighting with both hands would work out yet. I was thinking that the mech would have some momentum so a player could push forward to accelerate quickly and then switch to a 2 handed attack. This may end up being just suboptimal though. This would have to be fleshed out and understood in test. 

The main risk I thought about for this system is that it might be too hard to master and thus be inaccessible to new players. I wasn’t able to flesh out the game enough to be able to setup fights with the control scheme, but this is the first thing I would need to do were I continuing with this game. There also could be issues with this system not allowing for enough ease of use in fights. That said I think the system has enough potential that it would be worth exploring more. 

Another nuance to the fighting system I had thought about was making weapons that make sense with VR. Swordfighting in a way that makes intuitive sense is hard. There is nothing to stop your hands in real life, so how do you block a sword with another sword? The solution I came to was that what if swords cut each other? This way when two swords interacted, both would be cut off at the “block” location, which essentially blocks, but is also consistent with how VR works. Technically, this is an easy solution to implement with raycasts. Raycasts are inexpensive to use and then can then also detect impact with another player for damage as well as be used to cut the sword asset to length based on the impact point. The sword then regenerates to full length if no more contact occurs after a second or two. I think this would be an interesting mechanic to play around while fighting. As far as lore is concerned, I was going to make the sword a focused beam of plasma, and when contacted by another it loses magnetic confinement and disperses, becoming unable to cut. My prototype used a number of cylinders to represent the sword blade, as shown below. 

![Sword Diagram](/sword_diagram.png)

I thought a lot about other weapons that could be put inot the . In real life, the cost of length or weight in a weapon is that it becomes harder to swing because it is heavier. In VR, every weapon is the same weight, the weight of the controller. Other weapons that I thoughts about were: 

- Shield: you sacrifice reach and damage to gain blocking power, a shield would not be cut by the swords 
- Axe: gain damage at the edge of the axe’s range for the inability to hit targets closer in. this has the potential to not be a big drawback though, and would have to be experimented with. 
- Gun: this has a lot of promise in terms of being immersive, but as the old adage goes, if a player brings a knife to a gunfight, they might be at a bit of a disadvantage

## Initial Prototyping

With the above thoughts in mind, I started prototyping. The main tools I used were an oculus quest as my VR headset, Unity as my development engine, and blender for creating assets. I already knew how to use unity and code from college, but learning blender was mostly a matter of watching a lot of youtube tutorials to get a sense of the basic tools. I was never planning on fully making art assets myself, but being able to throw together basic prototypes proved a very useful skill on my game development journey. 

I first started out by making a mech cockpit I could use to see how I felt with a framed cockpit as opposed in just empty space. I used the grease pencil tool to sketch out a basic design and then some Boolean operations on the simple starter shapes to make the volumes. 

![Mech Cockpit Side View](/mech_cockpit_pic_1.png#center) 

![Mech Cockpit Isometric View](/mech_cockpit_pic_2.png#center)

The next step was coding up a basic movement engine using the oculus unity integration to query the position of the head frame of the headset and the controller locations. This was then used to move the player according to the controller position diagram. During implementation, I created small “home positions” that the player could home to denote where the controllers would be held to signal no input. These positions defined the home line in the diagram and could be seen by the player in the mech. The home positions were determined by having the player go to the home position and press a button. The player then extended their arms all the way out and out to the sides as well. The front and side arm extensions determined what “full throttle” was. The input was then scaled from 0 to 1 where 0 is the home position and 1 is full throttle. This was done for forward/back and left/right movement. This process is seen in the video below. 

{{< youtube Mh4Zmyt0XZg >}}

After testing my little prototype to work out the bugs and ensure it was behaving as I wanted, I took it to one of my friends to get their thoughts. I wrote up a little questionnaire to make sure that I would get some feedback in key areas I wanted. The questions were:  

1. How does the movement system make you feel? What does it make you feel like you’re doing? 
2. Are you able to go where you want to? Is it easy to do? Does it feel intuitive? 
3. What (if anything) did not work the way you were expecting it to? What were you expecting it to do?

In hindsight, a couple things i would have changed were to make question 1 more specific about a robot. I'm not sure if that kind of leading question would have been good in terms of getting neutral feedback though. 

This was a super helpful exercise, as I learned a few key things. 
1.	The movement using the controllers needed to be nonlinear. If the player is moving the controllers around close to the home position they want fine control of the speed of their mech. If they are jamming the sticks, you don’t need fine control, just to go to full power. 
2.	The movement also felt too smooth to be in a robot. I think it needed some sort of camera shake or feeling of up and down movement to be more realistic. However, because camera shake was super disorienting, I settled on shaking the frame of the mech. 
3.	A third feedback was more simple, just to make the home markers translucent so that the player could see where they were inside the home markers.

## Prototyping Round II

After getting this feedback, I began the implementation of the feedback. In order to increase the sensitivity near the home position I put the player movement input (scaled from 0 to 1) into a square function. This way the output has lower sensitivity at low distances from the home position and then quickly ramps up to full input value (1) at the boundary of the player’s reach. This worked very well in allowing for more fine control close to the home position while still having the full throttle position be in the same place. I experimented between this and a circular ramp (equation of a circle centered at (0,1)). It ended up not making much of a noticeable difference, so I went with the simpler equation. That said, this is something that could be explored more in playtesting once there was more combat to work with. 

In order to implement cabin shake in the mech, I tracked the distance traveled by the mech. Every “step length” of distance traveled a small shake was applied to the mech. This shake used a random walk to  bounce the cabin in the vertical direction, giving the illusion of a shake. This “step length” trigger was also used to play footstep sounds. This resulted in a much more realistic mech. 

Finally, the biggest addition after the initial prototyping was the addition of a sword and shield. I first generated the models seen below in blender. I then used the tagging functions in unity to tag the objects that the sword and shield should collide with and damage. Upon contact with an object, the raycast was used to cut the sword length to the right height based on where the raycast contact is. 

![Player Position](/sword_picture.png#center)

![Player Position](/buckler_picture.png#center)

## Completed Prototype 

This is a demo video of the prototype of Wellspring 1. Unfortunately, the sound effects do not sync up with the walking because of a bug with the Oculus recording system. I've left them in so you know what they sound like. Sound effects were created by [Lee Barkovich](https://archive.org/download/Berklee44Barkovich). 

{{< youtube RNI00DvEnts >}}

## Lessons Learned

Once I finished the prototype, the next step was to start making the game multiplayer so that I could playtest with other people. Upon researching how to do this, it was a ton of scope to even get the basics done for networking. I needed to develop a whole server application and then figure out how to transfer all the information necessary to recreate a person’s pose in VR on the other side. And while doing this keep the application performant enough that there aren’t any issues with the VR. This seemed like a lot for a single developer on their first game, so I started to reconsider my current scope. 

 Additionally, it was a lot of work to continue developing 3D assets for VR either on my end or to find a contractor who could help me out with this. As a first game and learning project, it seemed that I would be spending more time solving technical problems rather than game design problems, which was not what I was intending. Because of these reasons, I decided that I needed to remove some scope so that I could keep it to something reasonable for me to do by myself. 

Although I decided to move on to version 2 of the game, I think this was a super valuable experience for me. I learned a lot about just the basics of development for VR and how to make prototype models in blender for games. Learning the basics of blender also showed me that I will need to hire someone if I ever need quality art made, as I’d have a ton to learn to get close to making presentable assets. 

Thanks for reading, stay tuned for another article about the follow-up project to this, the aptly named wellspring 2. 
