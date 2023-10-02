---
name: Bee Free
tools: [Unity]
image: https://img.itch.zone/aW1hZ2UvMjAzMjY5Ni8xMTk1NjgzNC5wbmc=/347x500/kmjMWP.png
description: Play as a Queen Bee saving her hive from the evil bears.
---

# Bee Free

Bee Free is a Stealth game created entirely for the EGD x SGDA Spring Game Jam 2023 by a 9 person team.

<p class="text-center">
{% include elements/button.html link="https://notalobster.itch.io/bee-free" text="Play Now" %}
</p>

![preview](https://img.itch.zone/aW1hZ2UvMjAzMjY5Ni8xMTk1NjgzNC5wbmc=/347x500/kmjMWP.png)

## Gameplay

Fly through each level as a queen bee, reclaiming honey and freeing your colony from mechanized bears
Be careful though, the bears have uncanny sight and hearing so make sure you bee careful while navigating the mazes
Shoot honey to temporarily distract the bears
Hide in various positions to avoid their detection
And if a bear does get you, the bees you saved will return the favor for you


## My Contributions

#### Team Lead
I was the team lead, and led the early stages of finding members, and brainstorming through the available themes
#### AI Programmer
Once the project started I was tasked with designing the Bears AI behavior, including their sight, hearing, movement, and pathfinding
I used A* to guide the bears through our complex levels, each following a series of checkpoints that they would navigate through
Bears have a cone for their sight, and an invisible circle around them for hearing, the closer the player is the more likely to be detected
Once a player is detected the bear will pursue the player through a level, until the player is caught or breaks line of sight
If a player breaks line of sight, the bear will go it the players last known location, check around briefly, and then return to its predetermined check points
#### Level Designer
In the last hours of the game jam I designed the last two levels in the game, taking advantage of the bears to create a variety of situations where players can utilize various aspects of gameplay
The levels are rather challenging, with a lack of build up, but result in a game that offers players a skill based experience to win

## What did I learn

A common theme I have learned from games is the importance of playtesting early and frequent, even in a project as short as this one. Some of the bugs would have been caught earlier had more members on the team playtested earlier on, and my levels could have been improved on
Also the importance of having a variety of projects and a personal codebase to work from. The other main programmer on the team was able to work a lot faster because he had more previous game jam experience and was able to pull a lot of his code from previous works, which really helped us out
