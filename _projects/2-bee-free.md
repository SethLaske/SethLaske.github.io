---
name: Bee Free
tools: [C#, Unity]
image: https://img.itch.zone/aW1hZ2UvMjAzMjY5Ni8xMTk1NjgzNC5wbmc=/347x500/kmjMWP.png
description: Play as a Queen Bee saving her hive from the evil bears.
---

# Bee Free

Bee Free is a Stealth game created entirely for the EGD x SGDA Spring Game Jam 2023 by a 9 person team in 48 hours. I worked on the enemy bears AI, and designing levels.

![preview](https://img.itch.zone/aW1hZ2UvMjAzMjY5Ni8xMTk1NjgzNC5wbmc=/347x500/kmjMWP.png)

<p class="text-center">
{% include elements/button.html link="https://notalobster.itch.io/bee-free" text="Play Now" %}
</p>

![Movement GIF](/assets/BeeFree/Basic.gif)
## Overview

Fly through each level as the Queen Bee, reclaiming honey and freeing your colony from mechanized bears

Be careful though, the bears have uncanny sight and hearing so make sure you bee careful while navigating the mazes

Shoot honey to temporarily distract the bears

Hide in various positions to avoid their detection

If a bear does get you, any saved bees will return the favor for you

<div style="display: flex; justify-content: space-between;">
    <img src="/assets/BeeFree/Hiding.gif" alt="Hiding GIF" width="45%">
    <img src="/assets/BeeFree/Honey.gif" alt="Honey GIF" width="45%">
</div>

## Contributions

#### Team Lead
Found members to fill the team and keep a balanced number of programmers, artists, and composers. Led the team's brainstorming session and assigned original tasks to get the team moving.
#### AI Programmer
I worked on the bear's entire controllers. A bear needed to be able to pathfind and move organically through preset levels, with a patrol mode and chase mode. I decided that the bears would also be able to see and hear players, so two types of detection would need to be implemented.
* Movement - In order to handle pathfinding and movement I implemented an A* pathfinder and navmesh generator available in unity rather than creating it myself due to the time constraints. Once I was familiar with the system, a level could be designed beforehand and generate a navmesh automatically that the bears could freely, efficiently, and organically move through. 
* Patrol - A series of guard points could be added throughout the level to create small circuits of bears, or placed across the map for a more dynamic game. Each post tracked the next post in the cycle, making it easy to design levels in the inspector. Each bear was also keyed into its path, ensuring that even if the bear tracks the player well off course, it will still return to its original post.
* Chase - Once a player is located, the bear will immediately move towards the player. To ensure the player has a chance of escaping the bears, I forced the bears to maintain a line of sight to the player. If a player manages to break that line of sight, the bear will still go to the last point the bear had line of sight, do a full 360 to try and find the player again, and then return back to its post.
* Sight - The sight mechanic is very simple, a bear has a cone shaped collider in front of them, and if the player enters that and the bear has clear line of sight, then the bear will detect the player and start chasing.
* Hearing - The bear has a chance to hear the player whenever the player is close enough to the bear in any direction. This chance is increased the closer the player is to the bear. If a player is heard, then the bear will leave its current patrol path to go to the position where the player was heard, and look around that area. This feature was admitedly a bit unfair as the bear will seemingly randomly walk towards you, and poorly explained in game. In hindsight it might have been better to scrap the feature and make the challenging game a bit easier. If I was to fix the mechanic I would add a visual indication of where the hearing is, make the chance increase cubically, and add a "sound" to the player so if they are moving they make more noise than when they are standing still.

![Movement GIF](/assets/BeeFree/TopView.gif)

#### Level Designer
Naturally to finish the game we actually needed to have playable levels, and since I created the navigation system I also took on the responsibility of making two of the levels. In order to make the game longer I designed the levels to be large and challenging so that players would have to learn each mechanic in order to beat our game.
* Level 2 - A very linear map with several sections, each having multiple viable pathways through. Frequent hiding spots to take a rest, as well as a large number of collectable bees to survive the many bear attacks.
* Level 3 - A much larger map, with different pathways, but only one path to the finish. Items were spread throughout the map, in smaller quantities as the bears were more spread out as well. Despite many of the patrol paths being relatively small, one group of bears have a path that traverse the entire level, encouraging the player to keep moving in case of an unexpected bear walking through.

![Level2](/assets/BeeFree/Level2.png)
![Level3](/assets/BeeFree/Level3.png)

## What did I learn

A common theme I have learned from games is the importance of playtesting early and frequent, even in a project as short as this one. Some of the bugs would have been caught earlier had more members on the team playtested earlier on, and my levels could have been improved on.
Also the importance of having a variety of projects and a personal codebase to work from. The other main programmer on the team was able to work a lot faster because he had more previous game jam experience and was able to pull a lot of his code from previous works, which really helped us out.
The communication on this team was very good, partially due to everyone being constantly active during the short time span. This really helped us coordinate git effectively and avoid any merge issues, which can be a huge flow and time killer during a jam.
