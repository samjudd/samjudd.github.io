---
title: "Wellspring 2: Character Design"
date: 2021-03-06T15:04:02-08:00
draft: false
---

## Introduction

Now that I’ve talked about map design in the [previous post]({{< relref "wellspring2_intro_and_map.md" >}}), the next thing to get to is the character design. To establish the basics, each character has some amount of health (can vary between characters) that gets depleted as they take damage from enemy characters. When they reach 0, they are out of the game for some length of time before respawning in their own base. Each character is controlled to walk with WASD and look with the mouse. They have a basic attack bound on the left click and abilities bound to the right click, Q, E and R keys. These abilities can be just about anything and are unique to each character. Each ability has both a cooldown in seconds between uses. Each ability can also be upgraded during the game by collecting the supply caches mentioned in the map post. 

## Character Design Methodology

I originally made 10 unique characters, though with plans to make more eventually once the game was playable. Each character has unique abilities and a personality. I think having unique characters with personality is a good design choice because they give players something to identify with in an emotional way. On top of that, they make for varied gameplay since each character can do very different things to make different team compositions and enable different playstyles for different players. Just as with the map, I tried to write out a list of guiding principles before I started brainstorming. 

-	Each character should add something unique to the game, it should have its own niche of gameplay that minimally overlaps with other characters.
-	Each character should have some initiative to be able to make plays on their own.
-	The more power a character ability has, the more risk the player should need to take to use it.
-	Each character should have gaps in their kit’s abilities that can only be filled by other characters.

With those principles in mind, I tried to think about how to make characters that filled different roles in a strategic game. The goal was to have each character choice matter to the player and make different 4-character teams play the game out in different ways. I came up with 6 different attributes that a character could bring to the game. I could then use different combinations of these attributes to make characters that are differentiated from each other in their role in the game. 

- **Tankiness:** A character with this attribute can block and/or absorb a lot of damage before going down. 
-	**Sustained Damage:** A character with this attribute is able to consistently deal damage over time. This is characterized by low cooldown abilities and/or ramping damage over time abilities. While all characters deal some damage, characters with this attribute can solo carry fights if protected by their team. 
-	**Burst Damage:** A character with the burst damage attribute is able to do a lot of damage to other characters very quickly. This attribute is characterized by high cooldown abilities or combinations of abilities that are able to quickly kill single targets. 
-	**Mobility:** A character with this attribute has some form of enhanced mobility other than the standard walk, run, and jump. Examples of this include short range teleport, long range teleport, dash, large jump, and flight. 
-	**Range:** A character with this attribute is able to use either their attack or abilities or both majority from long range. Some characters may have one ability that is ranged, but characters with this attribute will be defined in part by their ability to interact/fight from a distance. 
-	**Utility:** A character with this attribute has some unconventional way to affect the battlefield. This might be anything! Some examples include creating new terrain, to rendering the enemy unable to act, or creating vision to see in parts of the map where nobody is. 

I needed to make each character have their own strong points where they excel while also giving them weak points where they need teammates to succeed. My strategy for this was to make characters by taking a bunch of different groups of two attributes and seeing what characters I could make out of these different groupings. The idea behind 2 attributes for a character is that a group of characters with all these attributes is a “complete” group in terms of being able to do everything. This way a group of 2 working together can have 4 attributes and be very diverse. Then a group of 3 has the potential to be a full team.  

## Character Concepts 

The 10 planned characters each have two of the attributes I was thinking of. A couple groupings of attributes could be interpreted in different ways and so there aren’t 10 unique groupings. Assigning each character 2 attributes was a useful exercise because it limits me from making kits that are too overloaded. Another interesting challenge would be to make a character for every possible combination of attributes. I just haven’t gotten to that yet. Some combinations I think are more straightforward than others to make useful combinations versus others. Most of the easier ones are listed below. 

1.	**Tank / Utility**
    - This character I imagined as some sort of engager. This character would be able to use their abilities to disable single targets and hold them in place for their team to fight. They would also be able to absorb damage after they have started a fight. They would have trouble doing well into enemies that are engaging on them or dealing with multiple targets. 
    - **Example Abilities:** 
        - Not sure yet. 

2. **Sustained Damage / Range**
    - This character I imagined as some sort of long range artillery character. They would be slow moving and sort of a sitting duck, but if they were protected could deal a large amount of damage to the enemy from a long way away. 
    - **Example Abilities:** 
        - Missile barrage – character can fire a missile barrage from long range that deals heavy damage, however this ability can also hurt friendly targets.

3.	**Sustained Damage / Mobility**
    - This character is a melee damage carry with the ability to skirt around a fight dealing damage with their abilities while avoiding it using their mobility. This character would do well in extended fights that are chaotic but would have issues if they are unable to use their mobility to avoid enemy damage as they are not very tanky and need to be in melee range to deal damage. 
    - **Example Abilities:** 
        - Tracer charge – character can throw a charge and then blink to the charge but only if the charge is within line of sight. 
        - Totem – character can lay down totems that can be teleported to at any time, though the teleport takes a small channel where character is vulnerable. 

4.	**Tank / Utility**
    - This character is the counterpoint to the engager (#1 in list) as a disengager. This character plays around being able to disable enemies that come in to attack the team as well as protect their allies. This character excels against enemies engaging on the team but has trouble chasing down mobile enemies. 
    - **Example Abilities:**
        - Stasis Field - Character can create a stasis field around themselves that stops both allies and enemies rendering them unable to move or act. 
        - Energy Drain – Character can drain enemies energy, adding cooldown time to their abilities while refreshing their own. 

5.	**Burst Damage / Mobility**
    - This character is designed as a melee assassin. They would be looking to sneak around the enemy team and quickly eliminate a single priority target before quickly escaping while their cooldowns recover. This character excels at killing single targets but has difficulty in longer fights or against tankier targets. 
    - **Example Abilities:** 
        - Vitals – This would be a passive ability where critical areas on each enemy character would be revealed to this character only. Hitting these areas would deal bonus damage and (potentially) add cooldown to a single enemy ability depending on the vital hit. 

6.	**Burst Damage / Range**
    - This character would be essentially a sniper. They would be looking to setup in advance of the enemy entering an area and then pick off key targets from far away without being caught. They are characterized by long range precision damage at the expense of mobility. 
    - **Example Abilities:** 
        - Hunter’s Blind – This character would be able to setup blinds in trees or on the ground. These blinds would be camouflaged from the enemy sight. The sniper could then enter these blinds to gain extra range and accuracy as well as the ability to scope while sniping. 

7.	**Sustained Damage / Tank**
    - This character is a juggernaut that would be able to deal large amounts of damage to multiple targets while also being quite durable. This character however has very low mobility and would have issues with being able to be easily kited away from. This character would require help getting on top of enemies but once they are on top of them would be a menace to deal with. 
    - **Example Abilities:**
        - Energy Drain – This would be a passive ability where this character’s basic attacks and other abilities hit on enemies add shielding to this character based on the damage done and slow the enemy by a percentage. 

8.	**Mobility / Utility**
    - This character would be a sort of scout character with limited damage but lots of abilities to move rapidly around the map and figure out where enemies are. They would be weak in actual combat but strong in finding and taking objectives and quickly moving around the map to help allies and protect the map. 
    - **Example Abilities:**
        - Tree Swing – This ability would enable the scout to swing from tree to tree to quickly traverse the forest. 
        - Tracking Visor – This ability would enable the scout to highlight (enable everyone to see them through terrain or obstacles) a single character on the enemy team and reveal vitals on them to their entire team. Hitting these vitals would deal bonus damage. 
        - Relocate – This ability would enable the scout to teleport an ally to themselves from anywhere on the map after a channeling for a short period of time. 

9.	**Mobility / Range**
    - This character would be a skirmisher. They would not deal heavy damage, but they would be able to deal moderate damage from range while dashing in and out of the enemy team. They would have trouble cutting through tankier targets and would be easy to take down. However, this character is very hard to catch between their range and mobility. 
    - **Example Abilities:**
        - Dual Revolvers – This character’s basic attack is two revolvers that both have 6 shots. This enables them to shoot once from each hand in rapid succession but then has a longer spacing between shots on each gun. 
        - Blowback – This ability expends whatever ammunition is left in both guns to both blast the character back and deal short range damage to enemies in front of them. The damage and the blowback scale with the amount of ammunition left in the guns. 
        - Dash – This character has a dash. Pretty straightforward. 
        - Javelin – This character throws a javelin that deals damage to up to 2 enemies in a line. If the javelin either hits 2 enemies or an enemy and a tree or other terrain, it links the two. The link can be destroyed with three basic attacks, but until it’s destroyed the character can’t move outside of the tether range between the two things hit. 

10.	**Range / Utility**
    - This character is an illusionist. They work to trick the enemy through creating illusions of friendly characters and terrain as well as camouflage. They excel at misdirection and escaping but deal very low damage. 
    - **Example Abilities:** 
        - Illusory Swap – The illusionist can swap the appearance of any character with any other character or inanimate object (trees, rocks, etc.). These illusions dissipate as soon as the affect object takes damage of any sort or is disabled.
        - Conceal – The illusionist creates a field of smoke that lowers the vision range of everyone inside it. Allies can still see silhouettes of other allies and enemies inside the shroud. 

## Character Development: Sustained Damage / Mobility Character

After this concept development of all these characters, I decided to pick one and work on developing that character in Godot. I decided to work on the sustained damage / mobility character, who for brevity I called the melee carry. In order to create the character, I taught myself blender animations on YouTube. I then created a basic model of a character and made some basic walking animations. I just used some cubes and rectangles to make a person and rigged a basic skeleton in order to animate the skeleton.

 {{< youtube bnaCEnB8ODA >}}

I then exported this character into Godot and created a miniature test scene to run around in and test things. This test scene was used to tune the walk and run speed as well as the jump height and the camera speed and stuff like that. 

I then fleshed out the abilities with more detail and coded them up as well as created game assets for the abilities as needed. The abilities were as follows: 

- **Left Click:** Basic attack in a 3-attack cadence with the third attack being a power attack with both swords. There is only a 2-attack cadence with no power attack if the player is not holding both swords. 

- **Right Click:** Throws sword, right sword then left if right is already thrown. The thrown sword then sticks in the first object or enemy it hits and then does damage if an enemy was hit. The sword can then be right clicked again at any point after the throw (including in midair) to teleport to the sword and pick it back up. 

- **Q Button Press:** Summons a totem after a medium length channel. This totem can be teleported to as many times as desired without it being destroyed.  Totems should be able to be teleported to without line of sight by pressing Q and then a number 1-5 but this is not developed yet. 

- **W Button Press:** TBD, not sure what I want to do here yet. May be a parry of some sort to give some sort of defensive ability. Not sure I want to do that though. May also be a passive that empowers attacks on people after a teleport to a marked enemy. Couple ideas here depending on how things shake out with other characters. 

- **R Button Press:** The melee carry swings both swords in an arc, creating a wave that marks every enemy hit. Each enemy can then be teleported to by right clicking on them. 

This kit is designed to encourage highly mechanical play around a large number of blinks. However, in order to teleport in combat, line of sight with the thrown swords or marked targets must be maintained. Additionally, thrown swords do not travel too fast and thus are hard to hit and also weaken your fighting power. With two swords thrown, the player can’t fight and must look for their swords. Thus, balancing your throwing for mobility with your basic attack 3 hit pattern for most of your damage is very important. 

This character is designed to play and live on the edge between outplaying the enemy team and dying. Because this character is not very tanky and has low AOE damage as well as low burst, they require teammates to help create distractions and chaos to blink around and deal damage in. This character should excel the most in chaotic fights where they can blink from enemy-to-enemy dodging abilities and dealing damage with 3 hit melee combos before switching targets. 

**NOTE:** The tree assets in the video were created by user [Arludus](https://arludus.itch.io) on itch.io. They can be found at [this link](https://arludus.itch.io/lowpolytreepack). All other assets were created by me. 

{{< youtube Psyy5uMYQ-k >}}

## Character Development: Mobility / Range Character

The second character I decided to work on was the mobility / range character who I called the skirmisher. This character development for movement was a lot easier because all of the movement and basic animations were already built into a template character and associated class. This meant all I needed to do was build out the abilities on top of the existing player character structure. I ended up stopping working on this character without getting too far due to some personal life issues. This never got restarted as upon starting to work again to work on a new evolution of this game. See my reasons why in the following conclusions blog post. The planned abilities were as follows: 

- **Left Click:** The basic attack of this character is two revolvers with 6 shots each. After shooting, each revolver has a short time as the revolver rotates to the next chamber. Once out of ammo, there is a significant reload time. This was implemented and can be seen in the video below. 

- **Right Click:** Fires rest of bullets in both pistols at once after a short delay in a shotgun-like blast. Damage and knockback scale with the amount of bullets left in both guns. This was not implemented. 

- **Q Button Press:** This ability throws a javelin that links the first two things (enemies, rocks, trees, ground) that it hits. They are then connected by a rope-like link and unable to move further than the rope will allow until the link is basic attacked 3 times. The animation for this was made and implemented, but not the linking logic. 

- **E Button Press:** This ability dashes a set distance in a direction. This was not implemented. 

- **R Button Press:** Not sure yet, I think I want this to do something related to the ammo mechanic on the guns. Maybe some passive related to certain bullets having certain effects. Could relate to hitting bullets reducing cooldown on other abilities. Not totally sure here. Need to do more thinking about what the character needs. 

The ideal for this character is someone who can skirt around the outsides of the fight, dealing medium amounts of damage with a bit of disabling abilities and generally causing chaos and distraction while kiting out any attempts to stop them. A jack of all trades, this character should perform reasonably well in small skirmishes and larger fights. Also this character has a decent amount of mobility to get around the map as the full ammunition right click pushes you quite far. In fights, although the Q with full ammunition does a lot of damage, it will put the player out of the fight and unable to do anything else for some time while the player walks back, so there is a significant tradeoff to using it. 

{{< youtube -icWWpgB3ps >}}

## End of Post

This is the end of the design work I did on game characters I did because I stopped working on this particular prototype. In the [next post]({{< relref "wellspring2_lessons_and_conclusions.md" >}}), I’ll talk a bit about what I learned from making this game prototype as well as what my next steps are in game development. 
