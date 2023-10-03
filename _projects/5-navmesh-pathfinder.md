---
name: NavMesh Pathfinder
tools: [Java, Processing]
image: /assets/Pathfinder.png
description: Implementing AI agent movementing and pathfind behaviors through randomly generated mazes
---

# Navmesh Pathfinder

Developing this AI agent capable of pathfinding through a variety of maze styles was a semester long project for my Game AI course

## Functionality

* Organic steering behaviors to control velocity and acceleration
* Converting a level into a graph of connected polygons
* Using A* to calculate an optimal route through any maze 
* Interpret that series of nodes to traverse into the path for the boid to travel
* Use predictive behaviors to handle intentionally complicated routes without collisions
* Generate grid based mazes of any size using Prims Algorithm

![Mining GIF](/assets/Navigation.png)

## What did I learn

Over the course of the projects implementation I learned how and why maps are designed in certain ways, and tricks to take advantage of that

A*, a pathfinding formula I have since used for multiple projects, implemented in a variety of ways. An incredibly useful algorithm

How to create organic movement behaviors, and balance them to make them both believable and effective at traversing complicated maps

Procedurally generated levels, in this case implemented through randomized mazes