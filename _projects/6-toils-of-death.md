---
name: Toils of Death - A Toad's Journey
tools: [C#, Unity]
image: /assets/ToilsOfDeath/Cover.png
description: Play as an amateur Reaper, escorting a cowardly Toad through the spooky wild.
---

# Toil's of Death: A Toad's Journey

Toil's of Death is an escort quest game created for the CPP GDC Halloween Game Jam 2023, where it scored 2nd for Best Overall Game and Best Overall Game by a Solo Developer. I was the sole developer for this day long project.

![preview](/assets/ToilsOfDeath/Cover.png)

<p class="text-center">
{% include elements/button.html link="https://ratske.itch.io/toils-of-death-a-toads-journey" text="Play Now" %}
</p>


## Overview

Controlling both the Reaper and the Toad, reach the end of every level to reach the climactic twist

The Toad turns and jumps using the arrow keys, but only when he is close enough to a light

The Reaper transcends physical boundaries, and can smite the skeletal enemies approaching the Toad

Includes 5 levels, and 3 skeletal enemy types

Conquer your fear of the dark as this dark story unfolds

![Mechanics GIF](/assets/ToilsOfDeath/Mechanics.gif)

## Contributions

#### Game Designer
The available themes for this jam were toil and toad, and also needed to have elements of Halloween and/or Horror. So in my brainstorming I tried to think of a game mechanic that fit the theme of toil, when I remembered a classic meme:

<div style="display: flex; justify-content: space-between;">
    <img src="/assets/ToilsOfDeath/Meme.png" alt="Meme PNG" width="35%">
</div>

With the main game constraint I decided to make the second focus of the game around lighting. This would help to fit with the overall theme of being a Halloween game, and I was interested in working with the technical sides of light.

My first ideas were inspire by the Boos in Mario, in making enemies only move depending on their lighting. I then switched that to making the escortee scared of the dark. It would tie in closer to the escort portions and theme.

In order to make the game quick to play for reviewers after the jam I chose to introduce a huge gameplay flaw - the reaper has no collisions with the level or enemies.

<!-- Gif of reaper escaping? -->

This would clearly be a problem for a more serious game, but it helped to fit into the story of the game, and make the game accessible, despite allowing players to optimize the fun out of the game

The levels were designed to be short and non-linear, with the middle of the game's levels showcasing respective enemies.

#### Artist
I decided to do my own assets for the game before starting, rather than finding assets online.

I tried using a new pixel art program, Piskel, for the first time during this jam, and was switching back and forth between that and Pixilart, which was not the right decision to make under a time crunch.

![Tileset PNG](/assets/ToilsOfDeath/Tileset.png)
<p align="center" style="font-size: 12px;">Tileset</p>

I decided to have a consistent outer wall with a fence, and created a few different ground sprites for mostly aesthetic value. For levels 2, 3, and 4, the path tile is also shaped to be similar the the enemy each respective level introduces, which I think looked nice.

My favorite asset I made for this game is the reaper, I really liked keeping the shape and color simple, and I think the animations looked good.

<div style="display: flex; justify-content: space-between;">
    <img src="/assets/ToilsOfDeath/Reaper.gif" alt="Reaper GIF" width="45%">
</div>

#### Game Programming

* **Lighting**: This was my first time trying to add lighting to a game, so I went with the most simplistic approach, using Unity's Universal Rendering Pipeline. More important than the visuals were being able to control and detect the lighting. After some brief research I was able to create a nice pulsing effect through code, but I wasn't able to find a simple way to detect how lit a specific game object is. The workaround I ended up making was to get a list of all the lights in a scene, and check the distance the toad is.

<!-- Gif of light pulsing -->

* **Player Mechanics**: I created the toad first, focusing on having a high degree of tuning from the inspector. Then I created the Reaper, intentionally skipping wall collisions, and using the animator to handle the combat. The camera was created to try and show both characters when possible, before snapping to the reaper.

<!-- Gif of camera moving when the frog jumps away from reaper -->

* **Dialogue**: The dialogue was upgraded from the system I used in Branch Battles. I simplified the manager, improved the prefabs to simplify the process of adding characters, and completely rewrote the logic for clicking through. This was key to allowing players to get through dialogue quickly, while still focusing on the important dialogue.

![Dialogue GIF](/assets/ToilsOfDeath/Dialogue.gif)

Once the core mechanics were finished, I alloted the remaining time to working on a variety of enemies to populate the levels:

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px;">

1. **Snake**: The basic enemy present in multiple levels. Moves straight towards the toad. Simple, but having an enemy that doesn't wait before attacking is very important when the Reaper can abandon the toad without consequences.

2. **Cat**: The next tier of enemy, sleeping until the toad gets too close, and then charging quickly. Quick to implement, fits the theme, and adds some variety to the snake and how a player can finish the level.

3. **Bat**: The last enemy, and the most interesting. Each bat has a preselected center point, which I can place anywhere on the map, and then the bat will fly circles around that point, using a vector rotation to calculate its velocity and direction. Really adds a lot to force a player to have some level knowledge and timing.

<img src="/assets/ToilsOfDeath/Snake.gif" alt="Snake GIF" width="100%">
<img src="/assets/ToilsOfDeath/Cat.gif" alt="Cat GIF" width="100%">
<img src="/assets/ToilsOfDeath/Bat.gif" alt="Bat GIF" width="100%">

</div>

<div style="display: flex; justify-content: space-between; align-items: center;">
    <div style="flex: 1;">
        1. **Snake**: The basic enemy present in multiple levels. Moves straight towards the toad. Simple, but having an enemy that doesn't wait before attacking is very important when the Reaper can abandon the toad without consequences.
    </div>
    <div style="flex: 1;">
        <img src="/assets/ToilsOfDeath/Snake.gif" alt="Snake GIF" width="100%">
    </div>
</div>

<div style="display: flex; justify-content: space-between; align-items: center;">
    <div style="flex: 1;">
        2. **Cat**: The next tier of enemy, sleeping until the toad gets too close, and then charging quickly. Quick to implement, fits the theme, and adds some variety to the snake and how a player can finish the level.
    </div>
    <div style="flex: 1;">
        <img src="/assets/ToilsOfDeath/Cat.gif" alt="Cat GIF" width="100%">
    </div>
</div>

<div style="display: flex; justify-content: space-between; align-items: center;">
    <div style="flex: 1;">
        3. **Bat**: The last enemy, and the most interesting. Each bat has a preselected center point, which I can place anywhere on the map, and then the bat will fly circles around that point, using a vector rotation to calculate its velocity and direction. Really adds a lot to force a player to have some level knowledge and timing.
    </div>
    <div style="flex: 1;">
        <img src="/assets/ToilsOfDeath/Bat.gif" alt="Bat GIF" width="100%">
    </div>
</div>


## What I Learned

**Buttons** - The coolest trick I learned from this game jam was utilizing buttons. I needed to have different functions result from the same actions, for example ending a section of dialogue could result in changing scenes, starting a level, or enabling enemies. I tried to create a custom event system, but was unable to make it as effective as what buttons allowed for. The simplicity of adding game objects and calling functions from OnClick, which could be edited from the inspector. So I added hidden buttons to call OnClick to handle an arbitrary amount of functionality.

**Scoping** - I think I really nailed the scope of this project. I had an idea for an MVP with some core mechanics that could be developed independently and then combined into a level when ready. 
The coding aspects required a lot of small items to work together, but were easy to debug individually. 
I had ideas for features that I really wanted to add, but I was able to stay focused and submit in the time frame provided, rather than getting sidelined. It allowed me to create a cohesive *finished* game in a day, while still getting good sleep.