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
This was my first solo game, and having total control over it was both relieving and terrifying. I decided to make a game that was somewhere betweeen two of my old favorites *Stick War* and *Age of War*. I felt that the mechanics would be easy enough for me to recreate the core gameplay loops, and open-ended enough to add on my own spin.

##### Movement Style
On my original game design document the plan was to have one dimensional troop movement like in Age of War, but offer the player the more strategic elements of defending like Stick War. I also wanted to have multiple levels to offer diverse challenges to player and avoid a single long game.
After the original prototype was created with 3 different player soldiers, a miner, a defensive sniper tower, and gates I came to my first real design challenge. The one dimensional gameplay didn't feel fun, and playing levels felt extremely slow and disintresting. After a few playtests I decided to go two-dimensional with the movement for the sake of a better player experience.
By switching the entire combat system to be two dimensional, there were far more bugs, weirder troop behavior, and a lot more programming effort, but from the very first prototype the game felt infinetly more fun to play.

##### The General
Another important desicion was increasing the player's engagement with the game Managing the army composition and position was fun, but in the early stages of the game, the player was spending far too much time watching, rather than playing.
Again, I turned to Stick Wars for inspiration, and allowed the player to take control of a unit on the field. But rather than switching between multiple units, I decided to create a single avatar for the player on the field, the *General*.
The General required a lot of iterations and playtests to balance his utility in battle as well as improving the player's experience. The final result included the following abilities and limitations:
* **Mining** - Allowing the general to mine was essential for the early game of each level, as it is likely the only thing the player will be doing
* **AOE Damage** - Unlike the majority of the units the player will use and fight, the General's attack will hit every enemy in its swing. By doing this the player is given a massive incentive to use the General in combat, and filling in a niche in the team building.

![Gneral AOE](/assets/BranchBattles/GeneralAOE.gif)
<p align="center" style="font-size: 12px;">Capable of wiping out a large number of enemies</p>


* **Camp Centric** - The General is the only unit in the game that heals during battle. However, this healing will only take place within the camp. Additionally, the player can only train units for their army while the General is within the camp's borders. This makes sure the player is forced to balance using the General in combat at the front, with utility at the tent. The General also deals an increased amount of damage within the camp as a last stand for the players defenses.

![Gneral Healing](/assets/BranchBattles/GeneralHealing.gif)
<p align="center" style="font-size: 12px;">Forced to return to tent throughout levels</p>

* **Army Buffs** - In order to balance a players desire for their playable character to be strong, and needing to balance the game so the player can't rush every enemy base at the beginning of the level, the General will receive stat boosts based on the army that is being trained. This allows for technical gameplay in training certain numbers of each units to maximize the General's usefulness, as well as balancing the General to being viable at the beginning and end of every level.

* **General Orders** - A common wish from playtesters was to be able to control certain groups of units independently of their main army. The General is able to send any soldier into a charge state, allowing the player to split their army into different groups, as well as offering utility with soul strategies for a skilled player.

![Gneral Orders](/assets/BranchBattles/GeneralCommand.gif)
<p align="center" style="font-size: 12px;">Charging soldiers will return with their shields or on them</p>

* **Loss Condition** - Although I have seen frustration from players at losing their General, having the General as a loss condition offers a silver lining in my opinion. Rather than having to slowly watch their army die, then the miners die off, as the player spends the last of their gold, before waiting for the tent to be destroyed, nearly every game over ends with the General. Which means that a player was either reckless/not paying attention, or was starting to lose. It allows the player to feel responsible for losing, and knowing they can improve, rather than the slow frustration of losing a level and being unable to stop it.

<!-- 
<div style="display: flex; justify-content: space-between;">
    <img src="/assets/BranchBattles/GeneralAOE.gif" alt="General AOE GIF" width="40%">
    <img src="/assets/BranchBattles/GeneralHealing.gif" alt="Healing GIF" width="40%">
</div>
-->

##### Game Modes
Level design was an extremely enjoyable task at the end of the game. I designed a total of 4 game modes, each with slightly different win and loss conditions:
* **Standard** - This is naturally the most common level type in the game. A player ends when they destroy the enemies base, and lose if their base/General is defeated.
* **Countdown** - A slightly modified version of standard levels. The same win condition, but the player also loses if the timer reaches 0. The AI in these levels are more defensively inclinded, taking advantage of their win condition.

![Standard Battle Layout](/assets/BranchBattles/StandardLevel.png)
<p align="center" style="font-size: 12px;">Destroy the tent to win</p>

* **Survival** - My favorite gamemode, the player needs to survive an onslaught of enemies until the timer reaches 0. These levels give me the most control, as each battle is carefully scripted. Levels 8 and 12 are (currently) extreme challenges to players, and force strategy changes and utilizing the General well.

![Standard Battle Layout](/assets/BranchBattles/SurvivalLevel.png)
<p align="center" style="font-size: 12px;">Survive until the timer reaches 0</p>

* **Boss** - I included three boss levels in my game. Each follows the same format, once the player destroys the enemy base, the enemy uses magic, spawns reinforcement, and the boss appears from the ruins of their homes. These levels force the player to be cautious and prepare for the challenge that a boss will offer. Additionally I enjoyed adding some creative aspects to these bosses, and they offer a bonus to the players in the form of an extra trainable soldier in battle.

![Standard Battle Layout](/assets/BranchBattles/BossLevel.png)
<p align="center" style="font-size: 12px;">Something is going to come out of that, and it could be a lawsuit</p>


##### Soldiers
*Army design* - Rather than unlocking every soldier to be used in battle, players a constrained to choose a maximum of four soldiers within a battle. Players are thus forced to developing strategies before battles, and allows for more soldiers to be added without being overwhelming.

*Damage Calculations* - In order to calculate the damage a soldier receives, the attacked unit's armor functions as a threshold. If the damage exceeds the armor, the full damage is received. Otherwise only a fraction is received. This effectively creates a type matchup chart between units based on damage and armor, while using attack speed to calculate a seperate DPS.

This was my mentality for each of the soldiers - I really like all of them, so forgive me for discussing each of them in length (as well as offering a couple of strategy tips):
* **Fighter** - One of the immediately accessible units, the fighter acts as a high DPS, fast unit. Originally forming the main offensive of a players army, in the later levels a Fighters uses become its defensive uses and optimal soul per gold value.
* **Spear** - As one of the best weapons in medieval history, I wanted them to be extremely useful. Attacking from behind the other units, and offering enough damage to counter Berserkers and Swordsmen it is very useful from the beginning to end. Increasing the General's speed is also a crucial usecase.
* **Shield** - The classic defensive unit, high armor and HP, low damage and speed. The shield also completes the early game rock paper scizzors matchup between Fighters, Spears, and Shields.

![Shield Wall](/assets/BranchBattles/ShieldSpear.gif)
<p align="center" style="font-size: 12px;">A phalanx is created to overwhelm the low damage per hit Fighters </p>

* **Swordsmen** - The second single strongest unit, and its position in Level 8 forms a roadblock for players due to its high Damage output making it a counter to the General in many situations, and being extremely well rounded.
* **Archer** - Shooting from a distance, offering utility of alerting the player to oncoming enemies, and offering very consistent damage to all other units. When used by the player it can also take advantage of the enmies AI in certain levels.
* **Rage** - The most powerful unit in the game, the Berserker is completely optional for players. It's a reward for the players able to beat Level 12, and becomes extremely useful in finishing the rest of the game. It is also the only trainable enemy with AOE damage making it even more special.

![Rage](/assets/BranchBattles/Berserker.gif)
<p align="center" style="font-size: 12px;">Every head is a nail if the hammer is big enough </p>

* **John Wick** - Originally created as a developer tool for myself to instantly kill enemies, I ended up leaving him in the game, trainable after finishing the game. Extremely expensive, but effectively invinsible due to it's perfect stats. 

![John Wick](/assets/BranchBattles/John.gif)
<p align="center" style="font-size: 12px;">Truly the Baba Yage of Branch Battles</p>

<!--
<div style="display: flex; justify-content: space-between;">
    <img src="/assets/BranchBattles/Miners.gif" alt="Miners GIF" width="40%">
    <img src="/assets/BranchBattles/ShieldSpear.gif" alt="Sheild Wall GIF" width="40%">
</div>

<div style="display: flex; justify-content: space-between;">
    <img src="/assets/BranchBattles/Berserker.gif" alt="Rage GIF" width="40%">
    <img src="/assets/BranchBattles/John.gif" alt="John GIF" width="40%">
</div>

-->

#### Artist

<!--This section sucks. Fix it-->

I will preface this section by stating that I am not an artist, and wouldn't consider any of the pixel art I made to be good by professional standards.

With that said I am extremely proud of how the art in Branch Battles turned out. I was able to create buildings, multiple units with unique designs and animations and backgrounds with parallax layers.

Working on the unit animations required a lot of my time over the summer, but allowing each unit to move and feel different was extremely important to the finished game.

My process for creating these constantly changed, but here are some of my favorites. I typically leaned into a slightly humourous side to some of these to compensate for the lack of detailing I was able to offer.

Also, learning some basic shaders was a huge addition for my game, and really helped complement the art I had already done. The shader I used the most edited the colors of the units, which I used to differentiate the player units from the enemy, as well as giving the boss units clear differences, without requiring extra effort.


#### Game Programming

##### Fundamentals
In order to make the rest of the explanations make sense I first need to describe the main functions that go into the gameplay loop.
The player and opponent each have a TeamInfo script that is responsible for storing the variables of each team, training and moving troops, and using magic.
The player has a script that interfaces to the team info with the player's inputs, and the enemy has a script that functions the same, but based on an AI's decisions.
The TeamInfo trains troops at the set barracks location, and units will then proceed to the rally point, which is changing throughout the game.

The hierarchy of inheritance for damageables is also important, certain bypasses in attacks and spells, and making the code easier to work on.

![Damageable Hierarchy](/assets/BranchBattles/DamageableHierarchy.png)

##### **Unit Behavior**
The Unit behavior is what I would consider to be the single most important part of this game. Units needed to act rationally and the scripts needed to be flexible enough to give each unit type unique behavior.

The functionality I needed for a series of soldiers to function as a cohesive army are as follows:
* Soldiers will spread out from each other dynamically.
* Soldiers will need to organize themselves into positions based on unit type.
* Soldiers will be able to pursue enemies a variable distance beyond the rally point.

I decided to implement a code based Finite State Machine to control the units AI. I used a FSM because I could simplify a units behavior down to four states: Walk, Retreat, Wait, and Attack. I quickly realized that the functionality within Retreat could be handled within Walk, and later on added Charge as a seperate state.

Each unit is given a class to determine the organization of an army. Front soldiers, like Shields, have a low class number, while soldiers with a longer range have high class numbers, such as Archers. This made it very easy to organize armies into groups of soldiers, as well as making it simple to add new groups later if I add new units.

The key checks to determine transitions include if an enemy is agroable, if an enemy is attackable, and if the unit is in its assemble range.

![State Machine Overview](/assets/BranchBattles/FSMOverview.png)

* **Wait**: Within the wait state, the soldier moves forward until it is at the relative front of it's section. Once it has reached this front position within it's class, it will signal that to any soldiers behind it, creating an army formation, then idles.

* **Walk**: Walking handles two major nested functionalities. The first is walking towards a target (that is within its agro range) and if there is no target, getting to the rally point before transitioning to wait. The second, more complex task, is reaching that goal while maintaining an army formation, created by following lower classed units.
This human shield behavior is essential for armies to be able to effectively utilize high armor soldiers, and to move in a realistic manner. Soldiers also needed to be able to determine when to stay behind the shield, and when to move forward to attack an enemy. Too early and it defeats the point of following a shield at all, but too late and the soldiers will just stand by until their shield dies.
My solution was to recursively find the front human shield of a group and walk at that speed, while within a range of distance behind their specific shield. Long range soldiers will naturally switch to attack when within range of their targets. A melee soldier will wait until their human shield enters the attack state, and then move around them to attack at an angle, and then switching to the attack state. In gameplay, this results in a realistic scenario where a target gets surrounded by a semicircle of opponenets, with a shield at the middle, and ranged soldiers attacking from a safe distance.
  
* **Attack**: The attack state is only reached when a soldier has already gotten within attack range, and only needs to handle the functionality of a unit's actual attack. This includes playing the animation and attack box, as well as making some slight movement positions which are very important to soldiers like the archer, as well as the visual realism of groups of soldiers fighting. It also slows down the movement speed of a unit while it is mid attack, again to improve the visual appeal of combat.

* **Charge**: Charging is a slightly niche state, which effectively combines the functionality of the walk and attack states but removes some of the additional logic. Once a soldier enters the charge state, it will approach the enemy, and kill any target it finds, while ignoring the rally or any additional controls from the player or enemy AI. Charge was implemented to create bosses, and give the player partial control over specific units, as well as being heavily used in survival levels.


##### **Save System**

The data that is actually saved only contains 5 elements: 
* **Troop Keys** - The units that a player has unlocked
* **Level Keys** - The levels that a player has finished
* **Troop Spaces** - The number of troops a player can use in battle (this could have been removed as it directly correlates to level keys) 
* **Active Army** - The units that a player is currently using in levels
* **Popup Keys** - Which pop ups a player has seen (used to explain mechanics and could be used for story between levels)

<div style="display: flex; justify-content: space-between;">
    <img src="/assets/BranchBattles/EmptyMap.png" alt="Started" width="40%">
    <img src="/assets/BranchBattles/EmptyBarracks.png" alt="Started GIF" width="40%">
</div>
<p align="center" style="font-size: 12px;">Early Game</p>

This data is then passed into a static PlayerInfo class which is used throughout the game to provide the needed data to the games systems. By decoupling the systems I don't force the player to reset their progress to play a new game, and unlike old Pokemon games, they can override their data whenever. 

This feature was especially useful for myself while testing and developing as I could access every unit and level, but also test out the game flow by restarting, without wiping my finished save.

<div style="display: flex; justify-content: space-between;">
    <img src="/assets/BranchBattles/FinishedMap.png" alt="Finished" width="40%">
    <img src="/assets/BranchBattles/FinishedBarracks.png" alt="Finished" width="40%">
</div>
<p align="center" style="font-size: 12px;">End Game</p>

##### **Level Creation Process**
An ongoing development process was making it as easy as possible to setup new systems within the levels. Here are a few of the improvements I made overtime.
* **Utilizing Prefabs** - The more I worked on the game, the more I used prefabs, and it still wasn't enough. Every button is now a prefab, nested within another prefab. The tents on either side are prefabs. Taking the time to implement create these prefabs, and create them to be modular was crucial and saved me when creating more levels.
* **Automating Player Hookups** - Discovering I could give a button a listener in code completely changed how the UI was structured. I created a script that connected the player to the UI at the start of a level, which is what allowed for different army compositions in the first place, and allowed me to utilize prefabs far more effectively, as I only needed to assign a single reference for the entire manager to be automated.
* **Hiding Variables** - At the beginning I overused public variables, which does add some weaknesses to the code that I'm aware of, but changing would have required a lot of refactoring. As a late stage solution I discovered Hide In Inspector. Using this as well as privatizing the variables I could greatly cleaned up my inspector tab, and made it far easier for me to connect prefabs and edit specific variables to balance the game.
* **Arena Level** - An addition I should have added earlier in the development process was creating a level that gives the player control over both the player and enemy teams. It illuminated some functions that needed to be altered and was incredibly useful for balancing and testing. 

Combining these with occasional code refactorings really helped me to maintain a flow throughout the duration of the project, and darastically speed up production time.


##### **Barracks**
The Barracks is only a single scene, but its existence is extremely valuable to increasing the depth of Branch Battles to players, and developing functionality common amongst video games.

Creating the stat wheel forced me to learn about how to use tiled sprites, as well as implementing an outside script to generate a mesh based on a polygon collider. 

![Stat Wheel](/assets/BranchBattles/StatWheel.gif)


##### **Enemy AI**
In game there are two main Enemy AIs: Survival and Standard. The countdown, standard, and boss levels all use the same AI, with certain values tweaked to create different behaviors from the player's perspective.

Survival AI is relatively simple. I have groups of preset waves, one wave is trained at a consistent time interval throughout, the other waves are spawned in set intervals from each other. I prefered this over a more random style of waves, as I could steadily increase the numbers of enemies, and offer different challenges. This AI is dependant on the charge state of units, so I am able to arrange enemy formations in specific ways, and time waves carefully so units of different speeds all arrive to the players camp at the same time. I also think it makes for the best showcase of a unit type. Level 8 and 12 force players to deal with primarily swords and berserkers, while also combining in certain formations that the player might use.

![WaveAI](/assets/BranchBattles/MediumWaveAI.png)
<p align="center" style="font-size: 12px;">Waves are fully customizable</p>

Standard AI is more complicated, requiring the AI to dynamically train and position units, and eventually use magic. 
* **Training Army** - I created a unit set for each unit class, and 2 tiers of checkpoints. The enemy will go through the first check point, training a random unit from the class unit set until it has fulfilled that class checkpoint. It will then go through all of the other classes, then repeat the process for the second set. This allows the AI to train a semi random army composition, while still granting me control over how a game might look. For example training a lot of miners at the start versus waiting, and creating a hyper offensive unit lineup rather than a deffensive selection.

<div style="display: flex; justify-content: space-between;">
    <img src="/assets/BranchBattles/EasyGodAI.png" alt="Easy AI" width="40%">
    <img src="/assets/BranchBattles/HardGodAI.png" alt="Hard AI" width="40%">
</div>
<p align="center" style="font-size: 12px;">A much wider array of options are given for customizing enemies to simulate different decision making despite being controlled by the same logic</p>

* **Positioning Army** - The AI compared its own count for soldiers with the number of soldiers that the player has. This is then compared to the attack threshold for the enemy to charge. A minimum soldier count is also set that the enemy will retreat at. This helps create agressive vs passive enemy's with the same script attached. A retreat point is also added, creating weakpoints for certain levels that players can take advantage of.
* **Using Magic** - Based on the circumstances of the battle, when the enemy has an opportunity to use magic, the enemy will calculate and use magic on one of the following targets: The largest group of player soldiers, 

## What I Learned
Working through this project taught me a ton of concepts and specific to designing, implementing, testing, and vector math. Here are some of my most common subjects I learned about:

* **Good Coding Practice** - Throughout my classes, I have been taught bits and pieces about good coding practices, but it never all clicked together until this project. Keeping as many variables private as possible, small functions, well thoughtout inheritance and abstraction, common naming conventions. A keen reader might have noticed the terminology I've used in describing certain things is a bit vague, and sometimes contradicts itself. I've called things units, characters, entities, soldiers, troops, enemies, etc... One of the earliest things I set up was giving the damageable class a public reference to the team info of its team. I named that variable General. Which is is not to be confused with (and definetly got confused with) the General, the playable character which has a script name of general. 
There are plenty of other examples of problems coming in because I had to search through my code for every line that referenced a public variable. Constant minor inconveniences from not having a consistent naming convention for variable vs method names. I needed this project to show me the consequences of all of these poor practices do matter, do build up, and are worth maintaining from the start.

* **Personal Management** - Since this was a solo project I didn't expect to need much in terms of organization, effective github management, and documentation. I figured that I would remember everything, and could just write a couple notes down on my game design document if anything came up. Not a great solution, there are so many different things that should be seperated, tracked, and evaluated. Having a single list of bullet points for everything doesn't work well, and even spreading it amongst multiple pages of a notebook. Having specific commits on github would have been extremely effective, rather than working on the game for a day or two and then just using git to "save" my progress. I think in a future solo project I would want both a backlog/active/completed task system, similar to what my internship used, as well as either a private or public devlog.
I think forcing myself to write down everything would make me a lot more organized and focused, solely because I would only want to track a single thing, and would rather avoid switching between branches to work on several aspects of the game in a single place. 
I do think that there is a use for having flexibility, iterating and experimenting losely, but tracking the results after is very important. I'd also be interested in seeing where I spent my time more clearly. *It would also be useful to be able to document these things for writing them here at the end*

* **Utilizing Unity** - Working in Unity for so long, it taught me what I didn't know. Being able to actually know what I needed to learn it made watching devlogs and tutorials far more useful, as I would learn more than the one thing that was taught, I would be able to apply everything they were using to my own work.
* *Gizmos* - Super useful for debuging, understanding why things are happening, and just looking very cool.
* *Object Detection* - Originally I used colliders for everything. Each unit ended up having 3/4 colliders attached, the ground had colliders, spells had colliders, even the camera had colliders. This caused plenty of struggles, needed to ensure every collider was the collider I actually was looking for, with some scripts added just to manage the collider on a game object. Once I knew better that these were both computationally inefficient, and rather annoying to deal with I started using colliders in code, only checking for nearby objects when directly needed. I also used ray casts far more liberaly due to the simplicity and effectiveness for what I was actually doing.
* *Prefabs* - Designing prefabs with the same strategies as object oriented programming was huge for certain cases. Make them easy to edit, only have the relevant information on each prefab, and designing them to be stackable so I can limit the number of additional prefabs I need to edit once I have to edit one. Super effective when implemented properly.

* **Playtesting** - This is not something new, it is rather common advice, but it appears someone should have repeated it to me at least once more, playtest **early** and **often**. And I will add some more specifics as well, playtest with new people throughout, and have good systems for getting playtesting feedback.
I had my roommates looking at my game frequently, showing them new features and having them experiment in levels. This was helpful, but not enough. Eventually they understood how the game functioned, and also played with certain biases from earlier playtests. For example trying to use a certain troop a lot because it was overpowered in a previous iteration, but severly nerfed in the current. They also picked up on how I design my games over time, and were thus could make inferences into the gameplay that a new playtester wouldn't.
I also would have been better suited by having more specific questions for playtesters, and being able to organize responses better. A lot of feedback was purely verbal, and not written down at the time, so I lost plenty of opportunities by not writing things down during or having a more formal process. 