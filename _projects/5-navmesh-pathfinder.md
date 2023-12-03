---
name: NavMesh Pathfinder
tools: [Java, Processing]
image: /assets/Pathfinder.png
description: Implementing AI agent movementing and pathfind behaviors through randomly generated mazes
---

# Navmesh Pathfinder

Creating the boid movement, navmesh generator, and random maze generator was a semester long project for my Game AI class in 2022. This was created inside of the Processing framework, programmed in Java.

## Overview
This project was designed to give us an indepth view of how NPCs can move through both preset and randomly generated levels.
* Organic steering behaviors to control velocity and acceleration
* Movement through a series of waypoints, slowing down to handle tight corners and moving quickly through straighter paths
* Converting a level into a graph of connected polygons
* Using A* to calculate an optimal route through any maze 
* Interpret that series of nodes to traverse into the path for the boid to travel
* Use predictive behaviors to handle intentionally complicated routes without collisions
* Generate grid based mazes of any size using Prims Algorithm

![Functionality](/assets/Navmesh/MazeNoExtra.gif)

## Contributions

#### Navmesh Generation

In order to create a NavMesh on a predetermined level the walls are ordered and connected in series.

Concave angles are found in the original level shape. For each obtuse angle, an additional line is drawn to a different useable vertex, splitting the original polygon into two.

This recurses into the sub-polygons until all polygons are convex, tracking it's neighboring walls.

Each polygon then is reattached to the polygon it was split from, creating a graph that traverses the entire level.

![Creating Navmesh](/assets/Navmesh/CreatingNavmesh.gif)

#### A* Pathfinding

In order to take advantage of the NavMesh, A* is implemented to find an optimal route through each polygon.

When a waypoint is selected the boid first finds the polygon it is currently in, and the polygon the target is in.

A* is used to final an optimal list of polygons to travel through, using the distance between the polygon centers as its heuristic value.

Rather than moving from center to center the boid travels through the midpoints of the dividing lines

Although this can result in the boid occasionally moving off target, it guarantees that the boid will not crash into walls that could be intersecting the direct line between polygon centers.

The boid will then pathfind from its starting point, through each midpoint, and finally to its final target.

Multiple waypoints can be added in simultaneously by pathfinding between each waypoint into a single movement path.

<div style="display: flex; justify-content: space-between;">
    <img src="/assets/Navmesh/MazeAllExtra.gif" alt="Creating Maze GIF" width="40%">
</div>

#### Random Maze Generation
Mazes are created randomly using Prim's algorithm.

First the available space is split into a grid of centerpoints.

A random starting cell is selected for the maze to be generated from, and adds all of its adjacent nodes to a frontier of potential nodes.

A node is selected from that frontier randomly, and connected to the node that previously added it to the frontier.

The node that was just added will then add all of the adjacent unconnected node to the frontier.

This cycles through until every node has been added to the maze.

The walkable path is determined by which nodes added their "children" to the maze, and walls are drawn between the rest of the adjacent nodes.

This algorithm results in a cycleless maze, with a slight bias around the starting cell.

<div style="display: flex; justify-content: space-between;">
    <img src="/assets/Navmesh/CreatingMaze.gif" alt="Creating Maze GIF" width="40%">
    <img src="/assets/Navmesh/RandomMazes.gif" alt="Random Mazes GIF" width="40%">
</div>

## What I Learned

Over the course of this project (and class) I learned a lot about how to design extremely intentional and believable NPC movements and behaviors.

Learning A* was also incredibly important, as I have used the algorithm in multiple projects and work since then. Learning the fundamentals and implementation here gave me enough understanding to be able to modify the implementation to prioritize different aspects as well, such as computing time or minimizing cycles based on the situation.

By implementing the maps, I also learned why game developers create maps in certain ways, as well as how the different implementations can affect behaviors. Designing these levels with the behavior in mind is crucial when comparing how the same boid can behave differently in the preset levels and the maze. 

The process of dividing a level into polygons was also very important. The process of splitting up these polygons was a challenge to understand, but once implemented allowed for clean pathfinding and movement mechanics. As well as improving my understanding of vector math, especially within a program.

And finally implementing a style of procedurally generated level design was an important experience. Prim's algorithm is very straight forward, and useful at generating a cycleless maze, but nodes closer to the center will typically connect to more neighbors on account of being in the frontier longer. 