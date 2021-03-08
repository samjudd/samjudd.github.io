---
title: "Wellspring 2: Lessons Learned and Conclusions"
date: 2021-03-06T15:04:57-08:00
draft: false
---

## The End of Wellspring 2

Although I quite like the idea for Wellspring 2, I ended up deciding to stop working on the project once I was ready to work on games again after a break. The main reason is that I think there is just too much scope for me to do on my own. I love the game idea and think it would be really fun to implement, but it looks like too much for just one person. I decided I needed to take a look and de-scope to a smaller, more manageable game. The best game is one that is actually finished, and so that is the number one priority. In my planned next post, I will go into what my plans are for wellspring 3 are, how I can leverage all the work I did on wellspring 1 and 2, and why I think it’s a much more achievable goal. 

## Lessons Learned  

Something I thought I did well from a technical perspective here was not templating out code before I needed to. Making template code can save time for me when using it in multiple places. Not templating things before they actually needed to be also saved me a lot of time, as a lot of things I thought I might end up using in multiple places didn’t actually get used. 

I also liked my approach of breaking out characters into attributes. I think I ended up with a bunch of characters that all filled unique niches. This system still left me room to grow since I could explore other attribute combinations that I had not previously explored. A system with maybe a few more attributes and 3 attributes per character could potentially spawn hundreds of unique niches of characters. The exploration into asymmetric vs symmetric maps I think also gave me some good iead

I watched some YouTube videos and got some advice from asking people on twitter about game art. It seems pretty expensive and time-consuming to get quality 3D art, and a game like this would need a lot of it. Looking to do a very simple art style seems like the best I can hope for if I want to stay 3D, but down-scoping to a 2D game is another option that makes art a lot easier. After working on the animations myself, they seem pretty hard and time-consuming to do. Definitely when making 3D games want to keep the animations simple and reuse where possible. Need to be efficient here. 

Another area where I did some research was networking. This is a very large technical challenge for me to take on alone. It definitely seems doable, but would not be easy at all, especially once things like preventing cheating and stuff need to be taken into account. Even without that though, it’s hard. A 3D game like this has a lot of moving parts that all need to be tracked and moved from client to server and back and kept synchronized. Movement prediction is also probably necessary to reduce the effect of lag. 

Those are the two major challenges I identified that would make it hard to make this game as-is. The next task for me was then to change the game to try to eliminate these challenges as much as I could while keeping the good parts of this game, mainly the map and the character ideas. This was my goal for Wellspring 3, which I will discuss in my next post.  