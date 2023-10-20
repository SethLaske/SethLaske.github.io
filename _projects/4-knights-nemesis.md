---
name: Knight's Nemesis
tools: [C#, Unity]
image: 
description: First game project
---

# Knight's Nemesis

Knight's Nemesis is a 2D dungeon exploring game created for CS 4700 (Game Development) by a team of 4 developers in the 2022 Fall semester. I worked on many of the core gameplay mechanics such as grid movement, organizing turnbased systems, and creating many of the non playable characters seen in the game.

<p class="text-center">
{% include elements/button.html link="https://yawgmoth.github.io/CS4700/assets/games/KnightsNemesis/index.html" text="Play Now" %}
</p>

## Overview

Play as a knight fighting your way through a dark dungeon to challenge the king for your rightful place

Time your attacks carefully in this turnbased grid movement game

5 Levels

7 Enemies


## Contributions

#### Game Systems
**Grid Movement**: The grid based system was created by making a point that is set to the tile a character wants to stand on, and then having the sprite follow that move point. Implementing it as such allows a character to move to a tile, as well as the next character to move, even before the first character's animation finishes, but eliminates multiple characters moving to the same tile. Additional logic is used for diagonal movement for characters to slide along the walls.
The player is also given an option to temporarily freeze their movement to be able to move diagonally easily.

<div style="display: flex; justify-content: space-between;">
    <img src="/assets/KnightsNemesis/BasicMovement.gif" alt="Movement GIF" width="30%">
    <img src="/assets/KnightsNemesis/Killing.gif" alt="Combat GIF" width="30%">
</div>

<div style="display: flex; justify-content: space-between;">
    <img src="/assets/KnightsNemesis/SpeedUp.gif" alt="Explosive Turtle GIF" width="30%">
</div>

**Turn Based**: In order to implement the turn based system the player is free to start every turn. Once the player makes a move, control is given to the level to iterate through every active enemy to make their moves with slight delay in between each, then returning control back to the player. Characters out of range of the player don't have a delay, and a speed up option was added to reduce the delay to be negligible for moving through corridors and to stop waiting for large groups of enemies to attack.

#### Enemy Development
**Base Enemy**: I designed a base enemy class that was able to be reused by other developers to use to quickly create different enemy types. This included all of the logic for attacking, pathfinding, and moving.

**Explosive Turtle**: I also created the explosive turtle enemy, as well as doing the art for it. This enemy is designed to be a slow tanky enemy, with the extra element of exploding once it reaches low HP. 

**Mini Boss**: I also added a mini boss enemy to a level, which would be responsible for unlocking a new player attack. This boss was given new functionality to allow players to learn of attack patterns, including not moving every turn. This mini boss was also specifically balanced to the expected player level.
<div style="display: flex; justify-content: space-between;">
    <img src="/assets/KnightsNemesis/SethEnemy.gif" alt="Explosive Turtle GIF" width="30%">
    <img src="/assets/KnightsNemesis/MiniBoss.gif" alt="Mini Boss GIF" width="30%">
</div>

#### Spawn Mechanics
In order to randomly spawn in enemies I created a spawner that could be edited to give each level a different spawn table of enemies and the liklihood each spawns. The total spawn rate and maximum number of enemies was also controlled. 

An NPC cat was also added as a little experiment for players. The cat is completely passive, randomly moving throughout the level it spawns in. Killing the cat gives the player a large amount of XP, however it also results in the level spawning more enemies faster.

<div style="display: flex; justify-content: space-between;">
    <img src="/assets/KnightsNemesis/Cat.gif" alt="Cat NPC GIF" width="30%">
</div>

#### Levelling System
The levelling system was designed to encourage players to go through floors at an even pace. The enemies level is determined solely by the floor number, so a player speedrunning will soon find themselves overpowered. However, the XP dropped is also determined by level, so staying on any floor will offer diminishing returns over time. Additionally the miniboss and passive cat both offer large sums of XP in return for taking on a suitable level of risk.


## What I Learned

This was my first Unity project, and although there are a lot of flaws to it, it taught me the basics for everything that I build upon in future projects.

* *Github* - This was my first time effectively using github in a multi person project where syncing up large file properly was extremely important. 

* *Scoping* - A common lesson for most developers, it was very easy at the start of the project to think of a ton of features to add, and this project was a strong lesson in how long games take to make. 