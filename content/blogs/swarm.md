---
date : '2025-01-27T21:40:16+05:30'
title : 'Review on the paper "Decentralised Multi-Robot Exploration using Monte Carlo Tree Search"'
draft: true
tags: 
    - drone
---

So I think that the problem of exploring unknown areas using UVs is one of the best unsolved problems in robotics. The algorihtms like SLAM have been developing for some time and are getting even better and better with algorithms like ORLB-SLAM 3, and MapEverthing for dense reconstruction of the environment. Other methods for short term mapping include the NVBlox (that uses GPU accelerated VoxBlox) library by NVIDIA.

But one of they key commonality in these set of algorithms is that these algorithms don't instruct the UV to choose optimal actions to explore the area. Swarm robotics can also be used to explore unknown areas by assigning different areas to agents/peers while also minimising overlapping areas and time.

One of the interesting approaches can be seen in the paper "Decentralised Multi-Robot Exploration using Monte Carlo Tree Search". The author intrudces the use of Decentralised Monte Carlo Tree for exploration and division of task among the peers. In this blog I will break down the paper to basics and 