---
title: "Percent Damage Potential: Game Development Writing from 2017"
date: 2021-02-22T17:49:15-08:00
draft: false
---  

I wrote this in 2017 in response to the "Damage Rating" statistic that got released at [this link](http://www.lolesports.com/en_US/articles/introducing-damage-rating-better-metric-track-damage). This article no longer exists and unfortunately the link doesn't work in the [Wayback Machine](http://web.archive.org/web/20170801000000*/http://www.lolesports.com/en_US/articles/introducing-damage-rating-better-metric-track-damage) either. Adding this anyway as I still think this has some interesting thoughts of mine on game development. It's phrased as a letter to Riot, though i never ended up sending it, and is unedited from the time when it was written. 

## About Me

My name is Sam Judd, I am a 22 year old graduate of MIT, an avid gamer, and an aerospace engineer. I decided to write this since you had mentioned in your release here:  (http://www.lolesports.com/en_US/articles/introducing-damage-rating-better-metric-track-damage) that you were looking for other thoughts on how to make damage rating have an intuitive scaling with time.
Something that interests me about esports specifically is that the complete state of the game is known at all times, in contrast to in live sports, where it is impossible to track everything. With all this knowledge about exactly what is going on in the game, it is possible to do a lot of different analytical things that are completely infeasible in a traditional sport, and I think the below idea is something that uses this unique fact to develop a novel statistic. 
I think that the reason there is some trouble finding an intuitive way to take the changes in damage per minute into account is because the damage rating is really unable to take build into account, since it only compares champions. Although the dmg/min does increase over time, the root cause of that is not leveling up, but mostly item purchases and runes/masteries (though to a lesser extent), not just the passage of time. We can use the fact that we know everything about the game all the time to basically normalize out the effect of item purchases and other player build choices to show what we are trying to get at, player skill. I would love your thoughts on it. I’m not an expert here, merely a numerically minded gamer, so any feedback would be really appreciated!. 

## tl;dr - Percent Damage Potential

My idea would be to replace and/or add alongside damage rating a new statistic I am calling percent damage potential. Based on the statistics of the champion being used (AD, AP, AS, Crit%, etc.) along with the statistics of each spell and the item/runes/masteries, we can compute a couple of “ideal” damage values for each champion. These two values would be called “Damage Potential” and “Burst Potential”. Burst Potential would be defined as the maximum damage a champion can do in a short period of time, say 3 seconds. Damage Potential would be maximum amount of average DPS attainable using all abilities and free-firing into a target. Percent Damage Potential would then just be the percent of these ideal values that the player was dealing. Obviously depending on champion, one could be more relevant than the other (e.g.. Burst Potential: Elise, Cho’Gath; Damage Potential: Tristana, Kog’Maw).
These statistics would allow for consistent ratings across all phases of the game since they take into account item, mastery, and rune builds when calculating rating. This gets across the core idea, how good is a player at taking what capabilities they have available to them and translating that into success on the rift. 

## Damage/Burst Potential Background

### Core Concept

Both damage rating and PDP/PBP are trying to convey fundamentally the same information. The main difference is that Damage Rating takes a comparative approach to this, in that the statistic can only be computed in comparison to other players in a similar situation. The approach for PDP/PBP is to create a statistic that can be computed in isolation, and is unique to the player and champion.  This will allow for better comparisons and a reduction of statistical variation or bias resulting from small sample sizes. 

### First Principles

The idea behind the statistic comes from aerospace engineering, where we describe the performance of many different components in terms of efficiencies. Since I work in liquid propulsion development right now, let’s take a rocket engine as an example. Rocket engines are basically big machines to convert chemical energy in fuel to thrust as efficiently as possible. With the numbers describing the design of a rocket engine, we can compute the maximum thrust the rocket engine could ever create (we’ll call this T_IDEAL), if it were designed perfectly with no flaws and there were no friction or any other lossy processes. We can then run the engine on a test stand and see how much thrust it produces (we’ll call this one T_ACTUAL). 

These numbers show a couple things. One, the value of T_IDEAL compared to other engines can show how well you have done in just designing your engine. This is equivalent to Damage Potential and Burst Potential being compared between different champion builds during a game, showing how one player is way far behind, or itemizing differently versus another player. 

We can then divide T_ACTUAL by T_IDEAL to get a percentage. This percentage would show how well you actually did generating thrust versus how well you possibly could do in an ideal world. This is analogous to PDP/PBP showing how well the player was able to get the damage capabilities in their build onto other champions through aim, positioning, and teamwork. 

## What PDP/PBP can Show

At its core, this statistic shows how well a player can translate their itemization into actually dealing loads of damage to the other team. However, I think there is a bunch of other information to be gained through comparing these statistics between players and champions, which is listed below: 

1. A plot of a player’s PDP/PBP over time could reveal whether a player is better at dealing out damage in the early game or the late game. Maybe in the early game the player is unable to get close enough in lane to really deal a lot of damage, but in the late game the player’s team has a wall of tanks and the player is able to free-fire for hours behind a wall and deal very close to ideal damage. Possibly a player is really great at getting in a lot of poke damage in the laning phase and deals really good PDP/PBP, but in teamfights is performing poorly. This is similar to a damage vs time graph but can be compared more easily among different champions/players. 

2. Just damage and burt potentials can be looked at in order to compare builds independent of player skill. For example, maybe one top laner has had to itemize very defensively while the other has itemized for the split push. This statistic would quantify that and human analysis could show why that is. 

3. It is possible that some champions have higher than average PDP/PBP across all players versus other champions. This could be useful information for balancing champions. Either they have a synergy that is dealing too much damage relative to other things, or perhaps all their damage is very easy to hit onto people so the skill cap for dealing a lot of damage is very low. 

4. Comparing a player’s PDP/PBP among all played champions would be a good indication of which champions the player is good with. Maybe the player is very good with autoattackers but is poor at skillshots and has a large reduction in PDP/PBP when playing skillshot-based champions. 

## Problems with Damage Potential

The main issue with damage potential is that it does not account for the other team’s builds at all. If the other team has itemized very defensively, the high armor may cause a low PDP/PBP even though all the attacks are being hit. This inability to put damage on the opponents would show up in the statistic even though it is not a direct consequence of player skill. However, if a player is consistently getting behind and losing lane and is thus behind on itemization and unable to deal their build worth of damage, perhaps that should show up in the statistic. Importantly, this same issue exists with Damage Rating, so PDP/PBP is not adding any additional problems with this issue. 

The other issue that I see with PDP/PBP is how to enumerate magic penetration, armor penetration, and lethality into the damage calculations. I think that the best solution is just to ignore MR, Armor, Mag Pen, and Armor Pen, because the enemy building armor hinders your ability to deal your full damage, and building armor pen will cancel that out. Basically, the opponent being ahead and building more armor than the player has armor pen will show up as a reduced efficiency, since the opponent’s armor will prevent the player from reaching their DP/BP.  Lethality, as it is just another method of gaining armor penetration, would be treated in the same way as flat armor penetration. 

Additional edge cases can be found in champions like Kalista, where your ability to deal damage increases as you deal damage thanks to rend. In this case, the right approach might be to get an average number of spears rended on champions, and use that for the rend damage calculation. If you are below that you are not playing to Kalista’s potential, and above that you are doing well and above potential. 

Finally, something else that might need to be taken into account is if you are an ADC and your support has an ardent censer for example. Obviously, this is a major leg up in your quest to deal damage, though one could argue that so is having some hard engage or CC. Overall, I think it is best just to leave this alone, but it certainly could come into play as a source of error. 

## Why Split into Damage and Burst Potential

This is actually still a bit of an open question for me, but, at the moment, I think Burst Potential is useful as it can statistically show how much damage the champion is capable of putting out in a burst. This is a very different method of dealing damage over time as compared to DPSing, and so using a more representative number to compare it to would be more useful. However, for burst champions, it is also possible that it is better to just average out over time same as usual, and because DPS is an average number, burst champions will just see large spikes of damage well above 100% of DP and then very low other times. 

## Solving the Damage Rating Issues

Now to get to the main point; how does this solve the issues mentioned in the article, as well as a few others I have noticed? I have listed the three article issues at the top, and then a couple others I noticed at the bottom

### Game Length Bias

The reason the current Damage Rating statistic has an issue with game time bias is because it does not account for the items that the player bought. In addition to that showing up as a nonlinear relation between game time and damage, this also could show up as a bias among players who tend to itemize more for damage as opposed to more defensively. This is especially prominent among top laners, where many common top lane champions can be itemized many different ways. PBP/PDP solves this itemization problem by dividing the damage dealt by the ideal damage, which is a function of item build. This normalizes the damage dealt for item build and champion power, so that as a game per minute average the statistic is useable without clear bias for longer games. 

### Adjust Damage/Minute Range Limit

This problem is not solved at all by this new proposed system, although for the same reasons as mentioned in the article, I think this is not a major issue.

### Major Reworks

Again, because PBP/PDP is normalized by both itemization and champion, major reworks will not affect the validity of the statistic. However, if a champion gets a lot more damage added to the kit, or easier to hit abilities, their average Damage Potential might increase and perhaps even their PDP due to easier to hit abilities. However, I think this is useful information to know in the statistic. Since this statistic does not depend on other instances of the champion being played, it avoids the major pitfall that Damage Rating has with these events, and can even provide some insight into how the rework changed how the champion is played. 

### Pocket Picks

Huhi is a monster on Aurelion Sol (I’m a CLG fan, so maybe a little bias here?), bdd has a pretty killer Zed, Froggen’s Anivia is pretty amazing, but in the current meta, nobody else is really playing those champions. This means that Damage Rating will either not be able to be done for this champion, or the rating will consist of only one or two players’ performances on it. This is not great, because pocket picks are a super important part of many players’ games. Because PBP/PDP removes the dependence on other games being played by other players to be valuable, it can be used to show how effective players are on their champions of choice, even if nobody else uses them. 

### Other Interesting Results/Features

Another benefit of this system is that it removes the need for bucketing the games by win/loss for comparison, precisely because it can be defined completely in isolation. Additionally, even if a player is behind in a game because they are losing badly, maybe they are still playing well and dealing all the damage they could, it was just not enough. This would show up as say a low Damage Potential but a high PDP. Additionally, this is also comparable across champions to get additional insights, since the champion is also normalized out. 

## Implementation of Precent Damage Potential

I see these statistics being implemented into casting and general news through two different ways. One, an average PBP/PDP across all games could be used in place or in addition to a player’s damage rating as a measure of how well they are playing. Additionally, PDP/PBP ratings during individual fights could be calculated as well, again showing how well they did in the specific fight. Finally, just Damage Potential or Burst Potential could be shown as a measure of how strong a person is currently in-game in a damage dealing way. 
How these statistics would be implemented into the game and casting is outlined below. 

### Computing PBP/PDP

Damage Potential would be computed by summing up all of a champion’s damage sources divided by their cooldowns, to get a champion’s general capability to deal damage on average. This number would be used to compute a champion’s PDP. This value would be computed for each time section where itemization was constant, and then averaged using a time weighting. Burst Potential would be calculated as the maximum amount of damage a champion with an itemization could deal in 3 seconds, taking into account cast times of abilities, spells, autoattacks, and item actives. This would then be used to compute PBP. This statistic would be computed over set intervals of time, say every 1 second is used to generate a data point (to allow for resolution in teamfights) to generate time series plots.

However, something that is important to note is that if the time that the statistic is averaged over is every time the champion is within 2000 units of an enemy, then most of the time you will be dealing no damage relative to your average, and so the game efficiency will be rather low. Therefore, for this statistic, a more accurate time selection is any time that is less than 3 seconds away from a time when damage was dealt to champions. Therefore, this will ignore time spent doing things like farming minions or walking to lane, but anytime you are making trades in lane or attempting a gank, the window will be open for averaging. This can be computed from in-game data. It would be useful to explore both of these averaging times in looking at how best to use this statistic. 

### Casting

I think that damage potential and burst potential would be very useful for casting in the sense that it would be easy to show just how fed a player is or how they compare to the other players. For example, if a mid laner is very fed, it would be easy to say something like “player 1’s damage potential is 350 right now versus 200 for their lane opponent, but their burst potentials are approximately even, so any long harass with favor player 1, but short trades will still go roughly even despite the fact that player 2 is behind.” In post-game analysis, PDP and PBP could be used to inform discussions of how well a player was able to use their champion, and for champions with low PDP or PBP, analysis could be done on why that is. 

## Damage Rating for Champion Design

In addition, this statistic could also be used to help guide champion design and also identify champions in need of patches/reworks. Obviously, this could not be used on its own, but would be another tool in the design toolbox. By looking at character’s average damage potentials and PDPs over game time, a designer could identify champions where either itemization power spikes are too strong or weak, and also if there are issues where the champion is too easy/hard to use due to hard to hit or use abilities. This would not be much help in informing solutions, but could help in identifying problems. 