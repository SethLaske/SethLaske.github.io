---
name: Toils of Death - A Toad's Journey
tools: [C#, Unity]
image: /assets/ToilsOfDeath/Cover.png
description: Play as an amateur Reaper, escorting a cowardly Toad through the spooky wild.
---

# Toil's of Death: A Toad's Journey

Toil's of Death is an escort game created for the CPP GDC Halloween Game Jam 2023, where it scored 2nd for Best Overall Game. I created this project as a solo developer over the course of a day, including the programming, art, and design.

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

An escort mission would be perfect to fit the theme of toil. I also wanted to add lighting to this game, and played around with a couple of ideas such as only seeing enemies when they are/aren't in the visible light before settling on the concepts.
In order to make the game more engaging for the player I would make them control the toad and the reaper simultaneously, and only allow the toad to move while close to lights, which also helped inspire some of the story aspects.

I think this concept could have been iterated upon a bit more, especially as it seems like it could lend itself to a puzzle game, but I think the result turned out very nicely given the time constraints. 

I wanted this game to be pretty easy to play, so that everyone could get through it, which is responsible for the biggest flaw of the game design, the reaper could fly through the level and defeat all the enemies before the toad ever moves.
The levels are also relatively short and nonlinear, particularly Level 2, where I had time to create multiple paths, spawn traps, and more intentional level design.

#### Artist
I had already decided to do my own assets for the game before starting, and I think the art also looks decent, given that it wasn't my priority.

I tried using a new pixel art program, Piskel, for the first time during this jam, and was switching back and forth between that and Pixilart, which was probably not the right decision to make under a time crunch.

![Tileset PNG](/assets/ToilsOfDeath/Tileset.png)

I decided to have a consistent outer wall with a fence, and created a few different ground sprites for mostly aesthetic value. For levels 2, 3, and 4, the path tile is also shaped to be similar the the enemy each respective level introduces, which I think looked nice.

My favorite asset I made for this game is the reaper, I really liked keeping the shape and color simple, and I think the animations looked good.

<div style="display: flex; justify-content: space-between;">
    <img src="/assets/ToilsOfDeath/Reaper.gif" alt="Reaper GIF" width="45%">
</div>

#### Game Programming
The three elements I knew the game needed were the lighting systems, the players mechanics, and the dialogue, so when I started the jam I created a scene for each to figure out the implementation.

* **Lighting**: This was my first time trying to add lighting to a game, so I went with the most simplistic approach, using Unity's Universal Rendering Pipeline, adding a global light and a few spot lights. More important than the visuals were being able to control and detect the lighting. After some brief research I was able to create a nice pulsing effect through code, but I wasn't able to find a simple way to detect how lit a specific game object is. The workaround I ended up making was to get a list of all the lights in a scene, and check the distance the toad is. A relatively easy implementation, but in the future I would be interested in finding something more elegant.

* **Player Mechanics**: I created the toad first, focusing on having a high degree of tuning from the inspector, and leaving a lot of the logic here. Then I created the Reaper, intentionally skipping wall collisions, and using the animator to handle the combat. Linking the two together with the camera required some additional math to keep the camera focused on the important aspects, by staying between the controlled characters while they are close, and then focusing on the reaper if they seperate by too much.

* **Dialogue**: The actual process of getting a line of text to appear on screen character by character was copied from a Branch Battles. However, the dialogue manager itself was a lot simpler, and resulted in me learning an interesting trick to handle different events in a more modular manner (more on this below). I think simplifying the logic, which doesn't allow a person to completely skip text, really helped to make this game more dialogue focused, while not darastically slowing down player's who are uninterested.

![Dialogue GIF](/assets/ToilsOfDeath/Dialogue.gif)

With these core mechanics done, the gameplay was effectively completed. The only thing left to try and add enemies that function differently with very limited time remaining.

1. *Snake*: The basic enemy present in multiple levels. Moves straight towards the toad. Simple, but having an enemy that doesn't wait before attacking is very important when the Reaper can abandon the toad without consequences.
2. *Cat*: The next tier of enemy, sleeping until the toad gets too close, and then charging quickly. Quick to implement, fit the theme, and added some variety to the snake and how a player can finish the level.
3. *Bat*: The last enemy, and the most interesting. Each bat has a preselected center point, which I can place anywhere on the map, and then the bat will fly circles around that point, using a vector rotation to calculate its velocity and direction. Really adds a lot to force a player to have some level knowledge and timing.

<div style="display: flex; justify-content: space-between;">
    <img src="/assets/ToilsOfDeath/Snake.gif" alt="Snake GIF" width="35%">
    <img src="/assets/ToilsOfDeath/Cat.gif" alt="Snake GIF" width="35%">
</div>
<div style="display: flex; justify-content: space-between;">
    <img src="/assets/ToilsOfDeath/Bat.gif" alt="Snake GIF" width="35%">
</div>

I also created an enemy spawner that can spawn enemies at any number of preselected points. Kept to the theme of simple, and helped add some variability to the levels, depending on where the player goes. 


## What I Learned

**Buttons** - The coolest trick I learned from this game jam was buttons. Obviously I knew about buttons beforehand, but I never thought of using the button component itself to be able to quickly set different functions through the inspector. 
I needed to have different functions result from the same actions, for example ending a section of dialogue could result in changing scenes, starting a level, or enabling enemies. I tried to create a custom event system, but was unable to make it as effective as what buttons allowed for. The simplicity of adding game objects and calling functions from OnClick.
So I realized I could just give specific components a reference to a button, and invoke its OnClick, which I could then set to do any number of things, specific to that button. Obviously there are some weaknesses to this system, but it was perfect for my applications.
In the future I'd like to take this as a working prototype, and create my own event system to be used for future projects that require similar flexibility in the inspector while maintaining minimal code for each component.

**Scoping** - I think I really nailed the scope of this project. I had an idea for an MVP with some core mechanics that could be developed independently and then combined into a level when ready. The idea had room for expansion, but I was able to get something running very quickly.
The coding aspects required a lot of small items to work together, but were easy to debug individually, and super simple to implement myself. I was a bit inefficient when creating the art assets, but I was able to create basic animations, and have some variety to how levels look with a minimal timeline.
I had ideas for features that I really wanted to add, but I was able to stay focused and submit in the time frame provided, rather than getting sidelined. Not my greatest game, but I'm proud of being able to create a cohesive *finished* game in a day (and got good sleep which is also important)