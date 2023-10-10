---
name: Branch Battles
tools: [C#, Unity]
image: https://img.itch.zone/aW1nLzEzMzczMjg5LmpwZw==/original/DHFSIH.jpg
description: 2D RTS Game inspired by Stick War. Train, Battle, Conquer.
---

# Branch Battles

Branch Battles is a Real Time Strategy game created entirely by me in Unity. I worked on this project from January 2023 to September of 2023 before posting to Itch, and still update the game with playtester feedback.

![preview](https://img.itch.zone/aW1nLzEzMzczMjg5LmpwZw==/original/DHFSIH.jpg)

<p class="text-center">
{% include elements/button.html link="https://ratske.itch.io/branch-battles" text="Play Now" %}
</p>

## Overview

Train miners to get gold, use gold to get soldiers, use soldiers to get victory.
* Play 15 unique levels
* Unlock 8 different units
* Battle in 4 different combat styles
* Only 1 chance for glory

## Contributions

#### Game Designer
This was my first solo game, and having total control over it was both relieving and terrifying. I decided to make a game that was somewhere betweeen two of my old favorites *Stick War* and *Age of War*. I felt that the mechanics would be easy enough for me to recreate the core gameplay loops, and openended enough to add on my own spin.

On my original game design document the plan was to have one dimensional troop movement like in Age of War, but offer the player the more strategic elements of defending like Stick War. I also wanted to have multiple levels to offer diverse challenges to player and avoid a single long game.
After the original prototype was created with 3 different player soldiers, a miner, a defensive sniper tower, and gates I came to my first real design challenge. The one dimensional gameplay didn't feel fun, and playing levels felt extremely slow and disintresting. After a few playtests I decided to go two-dimensional with the movement for the sake of a better player experience.
By switching the entire combat system to be two dimensional, there were far more bugs, weirder troop behavior, and a lot more programming effort, but from the very first prototype the game felt infinetly more fun to play.

The next major design decision I made was also to increase the players involvement with the game. Managing the army composition and position was fun, but in the early stages of the game, the player was spending far too much time watching, rather than playing.
Again, I turned to Stick Wars for inspiration, and allowed the player to take control of a unit on the field. But rather than switching between multiple units, I decided to create a single avatar for the player on the field, the *General*.
By adding the general, a lot of playtesting and balancing was required, and his design was iterated upon multiple times. The final result included the following abilities and limitations:
* Mining - Allowing the general to mine was essential for the early game of each level, as it is likely the only thing the player will be doing
* AOE Damage - Unlike the majority of the units the player will use and fight, the General's attack will hit every enemy in its swing. By doing this the player is given a massive incentive to use the General in combat, and filling in a niche in the team building.
* Camp Centric - The General is the only unit in the game that heals during battle. However, this healing will only take place within the camp. Additionally, the player can only train units for their army while the General is within the camp's borders. This makes sure the player is forced to balance using the General in combat at the front, with healing at the back. A skilled player will have to constantly move the General to where it is most useful. The General also deals an increased amount of damage within the camp as a last stand for the players defenses.
* Army Buffs - In order to balance a players desire for their playable character to be strong, and needing to balance the game so the player can't rush every enemy base at the beginning of the level, the General will receive stat boosts based on the army that is being trained. This allows for technical gameplay in training certain numbers of each units to maximize the General's usefulness, as well as balancing the General to being viable at the beginning and end of every level.
* General Orders - A common wish from playtesters was to be able to control certain groups of units independently of their main army. The General is able to send any soldier into a charge state, allowing the player to split their army into different groups, as well as offering utility with soul strategies for a skilled player.
* Loss Condition - Although I have seen frustration from players at losing their General, having the General as a loss condition offers a silver lining in my opinion. Rather than having to slowly watch their army die, then the miners die off, as the player spends the last of their gold, before waiting for the tent to be destroyed, nearly every game over ends with the General. Which means that a player was either reckless/not paying attention, or was starting to lose. It allows the player to feel responsible for losing, and knowing they can improve, rather than the slow frustration of losing a level and being unable to stop it.

<div style="display: flex; justify-content: space-between;">
    <img src="/assets/BranchBattles/GeneralAOE.gif" alt="General AOE GIF" width="40%">
    <img src="/assets/BranchBattles/GeneralHealing.gif" alt="Healing GIF" width="40%">
</div>

Level design was an extremely enjoyable task at the end of the game. I designed a total of 4 game modes, each with slightly different win and loss conditions:
* Standard - This is naturally the most common level type in the game. A player ends when they destroy the enemies base, and lose if their base/General is defeated.
* Countdown - A slightly modified version of standard levels. The same win condition, but the player also loses if the timer reaches 0. The AI in these levels are more defensively inclinded, taking advantage of their win condition.
* Survival - My favorite gamemode, the player needs to survive an onslaught of enemies until the timer reaches 0. These levels give me the most control, as each battle is carefully scripted. Levels 8 and 12 are (currently) extreme challenges to players, and force strategy changes and utilizing the General well.
* Boss - I included three boss levels in my game. Each follows the same format, once the player destroys the enemy base, the enemy uses magic, spawns reinforcement, and the boss appears from the ruins of their homes. These levels force the player to be cautious and prepare for the challenge that a boss will offer. Additionally I enjoyed adding some creative aspects to these bosses, and they offer a bonus to the players in the form of an extra trainable soldier in battle.

Army design formed the majority of the balancing time. I decided early on to offer the player a larger number of units, and then allow them to change the army they bring into battle. Offering some constraints and decision making even before the battle starts, and also allowing me to expand the game in the future without overwhelming a player with too many available units in battle.
Beyond the structure of the army, each unit was designed to act within certain niches and to be relatively viable throughout the game. A key component of this is how damage is calculated. If an attack lands, the damage is compared to the units armor stat. If greater than the armor, the unit will take the full damage, if not the unit's received damage is divided by 1 + the original damage. Because of this damage per second can be very dependant on the enemy the unit is fighting.
This was my mentality for each of the soldiers - I really like all of them, so forgive me for discussing each of them in length (as well as offering a couple of strategy tips):
* Fighter - One of the immediately accessible units, the fighter acts as a high DPS, fast unit. Originally forming the main offensive of a players army, in the later levels a Fighters uses become its defensive uses and optimal soul per gold value.
* Spear - As one of the best weapons in medieval history, I wanted them to be extremely useful. Attacking from behind the other units, and offering enough damage to counter Berserkers and Swordsmen it is very useful from the beginning to end. Increasing the General's speed is also a crucial usecase.
* Shield - The classic defensive unit, high armor and HP, low damage and speed. The shield also completes the early game rock paper scizzors matchup between Fighters, Spears, and Shields.
* Swordsmen - The second single strongest unit, and its position in Level 8 forms a roadblock for players due to its high Damage output making it a counter to the General in many situations, and being extremely well rounded.
* Archer - Shooting from a distance, offering utility of alerting the player to oncoming enemies, and offering very consistent damage to all other units. When used by the player it can also take advantage of the enmies AI in certain levels.
* Rage - The most powerful unit in the game, the Berserker is completely optional for players. It's a reward for the players able to beat Level 12, and becomes extremely useful in finishing the rest of the game. It is also the only trainable enemy with AOE damage making it even more special.
* John Wick - Originally created as a developer tool for myself to instantly kill enemies, I ended up leaving him in the game, trainable after finishing the game. Extremely expensive, but effectively invinsible due to it's perfect stats. Truly the Baba Yage of Branch Battles.

<div style="display: flex; justify-content: space-between;">
    <img src="/assets/BranchBattles/Miners.gif" alt="Miners GIF" width="40%">
    <img src="/assets/BranchBattles/ShieldSpear.gif" alt="Sheild Wall GIF" width="40%">
</div>

<div style="display: flex; justify-content: space-between;">
    <img src="/assets/BranchBattles/Berserker.gif" alt="Rage GIF" width="40%">
    <img src="/assets/BranchBattles/John.gif" alt="John GIF" width="40%">
</div>

#### Artist
I will preface this section by stating that I am not an artist, and wouldn't consider any of the pixel art I made to be good by professional standards.
With that said I am extremely proud of how the art in Branch Battles turned out. I was able to create buildings, multiple units with unique designs and animations and backgrounds with parallax layers.

Working on the unit animations required a lot of my time over the summer, but allowing each unit to move and feel different was extremely important to the finished game.

My process for creating these constantly changed, but here are some of my favorites. I typically leaned into a slightly humourous side to some of these to compensate for the lack of detailing I was able to offer:

Also, learning some basic shaders was a huge addition for my game, and really helped complement the art I had already done. The shader I used the most edited the colors of the units, which I used to differentiate the player units from the enemy, as well as giving the boss units clear differences, without requiring extra effort.


#### Game Programming
The meat of this game, the results of many late nights, early mornings, losing track of time, a lot of frustration, and a lot of excitement: *The actual developing work*

If you are interested in the full list of everything I worked on, please scroll back up, and press Play Game to witness it all. But for anyone who would like the breakdown on some of the standouts that went into creating Branch Battles, hear you go:

##### Fundamentals
In order to make the rest of the explanations make sense I first need to describe the main functions that go into the gameplay loop.
The player and opponent each have a teaminfo script that is responsible for storing the variables of each team, training and moving troops, and using magic.
The player has a script that interfaces to the team info with the player's inputs, and the enemy has a script that functions the same, but based on an AI's decisions.
The teaminfo trains troops at the set barracks location, and units will then proceed to the rally point, which is changing throughout the game.

Every object that can take damage is inheriting from the damageable class. The damageable class is inherited by buildings and units. The team base is a subclass to buildings, and end the game when destroyed. The unit class is then inherited by the different types of characters. Most of the functions used by the unit AI is stored here as well, even if not all of the units use the state machine (specifically the bosses and General).


##### Unit Behavior
The single most important aspect to this game, making the units in the game function smoothly and logically, and offering enough flexibility within a single script class to create all of the behaviors to every unit created.

The functionality I needed for a series of soldiers to function as a cohesive army are as follows:
* Soldiers will spread out from each other. The distance they maintain is dependant on the actions they are performing.
* Every unit has a class, higher class units will use lower class units as human shields.
* Soldiers assemble according to class, with the lower class units closest to the flag with higher class units in sections behind.
* A soldier has an agro range that units will pursue enemies within. This agro range is determined based on the location of the rally flag. 

I decided to implement a code based Finite State Machine to control the units AI. I used a code based version rather than attaching scripts within Unity's animation system because when I created the system I didn't know Unity could do that. And I used a FSM because I could simplify a units behavior down to four states: Walk, Retreat, Wait, and Attack. I quickly realized that the functionality within Retreat could be handled within Walk, and later on added Charge as a seperate state.

The key checks to determine what state a unit needs to be in include if an enemy is agroable, if an enemy is attackable, if the unit is in its assemble range (calculated based on the number of units in each class within the army)

**Wait**: Although seemingly a very basic state, I wanted to use the Wait state for anytime a unit is within the assemble range. The unit then need to continue to creep forward, to try and be at the very front of the assembly area, but only if there aren't units already infront of it. However, even if there are units in front of it, if those units could move slightly out of the way to make room for an extra unit at the front then they should.
In order to handle all of these checks a unit examines the area in a radius around itself. Based on the units around itself it will determine if it can move forward-up, forward, or forward-down. If it can't then it marks itself as assembled, which units behind it can use to determine if there is a chance for themselves to move forward. By combining these checks with a slightly random start position, groups of equally classed units form a realistic army position for a group of soldiers standing around.

**Walk**: Another state that I thought would be simple, walk forward. And for a long time it was relatively simple. If a soldier had a target located, and that target was within its agroable range, the soldier would walk towards it until entering attack range. If not, it would walk directly to its assembly range. Until I added the mechanic of units staying behind the lower classed units, most importantly: shields. It was critical for a players imersion that a spear unit would actually follow a shield, rather than run infront and die immediately.
The solution needed to include walking in large army formations, with units of different classes and look logical when armies clashed. Fighters couldn't run ahead of the shields at the last second, but they also couldn't stay behind the shield and wait for it to die before engaging the enemy. The General also added some complication, as it is the only unit that would typically require units to walk back towards their own base to attack an enemy.
My implementation consisted of comparing the distance that the shield was from the "goal" (whether it was the assembly point or an enemy) and the distance of the unit to the goal, and then using that to ensure that the unit would walk backwards to be behind the shield if not already behind it. Once a unit was behind a shield, it would recursively check for the shield of the shield of the shield... to find the speed of the front of the army, and walk at that speed itself. 
In order to handle the attacking, I first ensure that the shield of a unit is attacking, before handling the extra movement logic. In the case of spears and archers, by the time the shield transitions to the attack state, the long ranged unit has already moved to the attack state, but the short range fighters and swordsmen need to handle movement more carefully, ensuring the shield takes the brunt of that attack, while moving to fight the enemy if possible.
By comparing the units around itself to the vector to the enemy, the unit will determine if there are already multiple units engaging with the enemy, or if its possible to move up/down to get within attack range of the enemy. This results in small semicircles forming around high HP units, as their opponents begin to circle around and attack from multiple directions, a behavior I am quite happy with.

**Attack**: Attack works very straight forward. When the unit is within its attack range it plays a coroutine that syncs the attack collider activating to the frame of the attack landing. It also slows down the unit while its attacking, but still offers some slight movement options. The soldier will slide in to be closer to the enemy, rather than breaking out of attack, walking, and then going back into attack, which helps to smooth out the animations when big groups of soldiers collide.
The main challenge came with the method of slowing down the movement of soldiers, and specifically its overlapping with one of the spells, Dio. Dio's ability calls upon the same functionality to freeze units for a certain amount of time, by slowing them down by a factor of 1000. The problem with this is it would coincide with the timing in the coroutine and cause essentially an infinite pause, while some of the animations resumed. Due to late discovery of this glitch, I used some awkward coding to solve it, but looking back a slight redesign would have been much better in taking more advantage of Unity's animation system to handle aspects of the attack, rather than my over reliance on coroutines.

**Charge**: Charge was added to be able to handle a player commanding individual soldiers to move forward, boss units to approach the player, and to simplify the AI of survival level enemies. It effectively combines the functionality behind walking and approaching targets, with attacking. It needed to be a seperate state to bypass the transitions between all of the other states, and is quite effective depite being the shortest state to code.

##### Save System
Creating a save system was something that terrified me before I started, but I knew was essential. By adding a save system it would make players able to reasonably finish the game even as it got longer than a single reasonable session. It also was needed to make Branch Battles *feel* like a real game. 
Turns out, the actual process was extremely simple, it was only about four lines to save and load a class to memory. The trick was to then work within Unity's limitations, and to decide how to implement the save data, and give players control.
The data that is actually saved only contains 5 elements: 
* Troop Keys - The units that a player has unlocked
* Level Keys - The levels that a player has finished
* Troop Spaces - The number of troops a player can use in battle (this could have been removed as it directly correlates to level keys) 
* Active Army - The units that a player is currently using in levels
* Popup Keys - Which pop ups a player has seen (used to explain mechanics and could be used for story between levels)
This data is then passed into a static PlayerInfo class which is used throughout the game to provide the needed data to the games systems. By decoupling the systems I don't force the player to reset their progress to play a new game, and unlike old Pokemon games, they can override their data if they would like. This feature was especially useful for myself while testing and developing as I could maintain a completed save file, and access every unit and level, but also test out the game flow by restarting.

##### Level Creating Process
An ongoing development process was making it as easy as possible to setup new systems within the levels. Here are a few of the improvements I made overtime.
* Utilizing Prefabs: The more I worked on the game, the more I used prefabs, and it still wasn't enough. Every button is now a prefab, nested within another prefab. The tents on either side are prefabs. Taking the time to implement create these prefabs, and create them to be modular was crucial and saved me when creating more levels.
* Automating Player Hookups: Discovering I could give a button a listener in code completely changed how the UI was structured. I created a script that connected the player to the UI at the start of a level, which is what allowed for different army compositions in the first place, and allowed me to utilize prefabs far more effectively, as I only needed to assign a single reference for the entire manager to be automated.
* Hiding Variables: At the beginning I overused public variables, which does add some weaknesses to the code that I'm aware of, but changing would have required a lot of refactoring. As a late stage solution I discovered Hide In Inspector. Using this as well as privatizing the variables I could greatly cleaned up my inspector tab, and made it far easier for me to connect prefabs and edit specific variables to balance the game.
* Arena Level: An addition I should have added earlier in the development process was creating a level that gives the player control over both the player and enemy teams. It illuminated some functions that needed to be altered and was incredibly useful for balancing and testing. 
Combining these with occasional code refactorings really helped me to maintain a flow throughout the duration of the code


##### Barracks
The Barracks is only a single scene, comprised of a couple buttons and stats. But like the save system I think its existence is extremely valuable to increasing the depth of Branch Battles to players, and developing functionality common amongst different games.
My favorite part of it is the stat wheel. Rather than just offering the numbers in text, showing a stat wheel makes the comparisons between units pop, and just looks so cool to me. Naturally, as it was inspired by JJBA.
Creating the stat wheel forced me to learn a surprising amount about how to use tiled sprites, as well as implementing an outside script to generate a mesh based on a polygon collider. 

![Stat Wheel](/assets/BranchBattles/StatWheel.gif)
I do also recognize that the Barracks could use a brief in game tutorial to explain it, as well as an improved UI. After releasing I realized that the applications need to be more clearly explained. 

##### Enemy AI
In game there are two main Enemy AIs: Survival and Standard. The countdown, standard, and boss levels all use the same AI, with certain values tweaked to create different behaviors from the player's perspective.
Survival AI is relatively simple. I have groups of preset waves, one wave is trained at a consistent time interval throughout, the other waves are spawned in set intervals from each other. I prefered this over a more random style of waves, as I could steadily increase the numbers of enemies, and offer different challenges. This AI is dependant on the charge state of units, so I am able to arrange enemy formations in specific ways, and time waves carefully so units of different speeds all arrive to the players camp at the same time. I also think it makes for the best showcase of a unit type. Level 8 and 12 force players to deal with primarily swords and berserkers, while also combining in certain formations that the player might use.

Standard AI is more complicated, requiring the AI to dynamically train and position units, and eventually use magic. 
* Training Army: I created a unit set for each unit class, and 2 tiers of checkpoints. The enemy will go through the first check point, training a random unit from the class unit set until it has fulfilled that class checkpoint. It will then go through all of the other classes, then repeat the process for the second set. This allows the AI to train a semi random army composition, while still granting me control over how a game might look. For example training a lot of miners at the start versus waiting, and creating a hyper offensive unit lineup rather than a deffensive selection.
* Positioning Army: The AI compared its own count for soldiers with the number of soldiers that the player has. This is then compared to the attack threshold for the enemy to charge. A minimum soldier count is also set that the enemy will retreat at. This helps create agressive vs passive enemy's with the same script attached. A retreat point is also added, creating weakpoints for certain levels that players can take advantage of.
* Using Magic: Based on the circumstances of the battle, when the enemy has an opportunity to use magic, the enemy will calculate and use magic on one of the following targets: The largest group of player soldiers, 

## What I Learned
Working through this project taught me a ton of concepts and specific to designing, implementing, testing, and vector math. Here are some of my most common subjects I learned about:
*Good Coding Practice* - Probably the most important learning experience of the project. Throughout my classes, I have been taught bits and pieces about good coding practices, but it never all clicked together until this project. Keeping as many variables private as possible, small functions, well thoughtout inheritance and abstraction, common naming conventions. All of these really started to click as the sum of many small problems began making the game harder and harder to alter. A keen reader might have noticed the terminology I've used in describing certain things is a bit vague, and sometimes contradicts itself. I've called things units, characters, entities, soldiers, troops, enemies, etc... One of the earliest things I set up was giving the damageable class a public reference to the team info of its team. I named that variable General. Which is is not to be confused with (and definetly got confused with) the General, the playable character which has a script name of general. 
There are plenty of other examples of problems coming in because I had to search through my code for every line that referenced a public variable. Constant minor inconveniences from not having a consistent naming convention for variable vs method names. I needed this project to show me the consequences of all of these poor practices do matter, do build up, and are worth maintaining from the start.

*Personal Management* - Since this was a solo project I didn't expect to need much in terms of organization, effective github management, and documentation. I figured that I would remember everything, and could just write a couple notes down on my game design document if anything came up. Not a great solution, there are so many different things that should be seperated, tracked, and evaluated. Having a single list of bullet points for everything doesn't work well, and even spreading it amongst multiple pages of a notebook. Having specific commits on github would have been extremely effective, rather than working on the game for a day or two and then just using git to "save" my progress. I think in a future solo project I would want both a backlog/active/completed task system, similar to what my internship used, as well as either a private or public devlog.
I think forcing myself to write down everything would make me a lot more organized and focused, solely because I would only want to track a single thing, and would rather avoid switching between branches to work on several aspects of the game in a single place. 
I do think that there is a use for having flexibility, iterating and experimenting losely, but tracking the results after is very important. I'd also be interested in seeing where I spent my time more clearly. *It would also be useful to be able to document these things for writing them here at the end*

*Optimizing Unity* - Working in Unity for so long, it taught me what I didn't know. Being able to actually know what I needed to learn it made watching devlogs and tutorials far more useful, as I would learn more than the one thing that was taught, I would be able to apply everything they were using to my own work.
*Gizmos - Super useful for debuging, understanding why things are happening, and just looking very cool.
*Object Detection - Originally I used colliders for everything. Each unit ended up having 3/4 colliders attached, the ground had colliders, spells had colliders, even the camera had colliders. This caused plenty of struggles, needed to ensure every collider was the collider I actually was looking for, with some scripts added just to manage the collider on a game object. Once I knew better that these were both computationally inefficient, and rather annoying to deal with I started using colliders in code, only checking for nearby objects when directly needed. I also used ray casts far more liberaly due to the simplicity and effectiveness for what I was actually doing.
*Prefabs - Designing prefabs with the same strategies as object oriented programming was huge for certain cases. Make them easy to edit, only have the relevant information on each prefab, and designing them to be stackable so I can limit the number of additional prefabs I need to edit once I have to edit one. Super effective when implemented properly.

*Playtesting* - This is not something new, it is rather common advice, but it appears someone should have repeated it to me at least once more, playtest **early** and **often**. And I will add some more specifics as well, playtest with new people throughout, and have good systems for getting playtesting feedback.
I had my roommates looking at my game frequently, showing them new features and having them experiment in levels. This was helpful, but not enough. Eventually they understood how the game functioned, and also played with certain biases from earlier playtests. For example trying to use a certain troop a lot because it was overpowered in a previous iteration, but severly nerfed in the current. They also picked up on how I design my games over time, and were thus could make inferences into the gameplay that a new playtester wouldn't.
I also would have been better suited by having more specific questions for playtesters, and being able to organize responses better. A lot of feedback was purely verbal, and not written down at the time, so I lost plenty of opportunities by not writing things down during or having a more formal process. 