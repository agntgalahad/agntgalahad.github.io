---
date : '2025-12-20T21:40:16+05:30'
title : 'Review on the paper "Decentralised Multi-Robot Exploration using Monte Carlo Tree Search"'
draft: true
tags: 
    - drone
---

So I think that the problem of exploring unknown areas using UVs is one of the best unsolved problems in robotics. The algorihtms like SLAM have been developing for some time and are getting even better and better with algorithms like ORLB-SLAM 3, and MapEverthing for dense reconstruction of the environment. Other methods for short term mapping include the NVBlox (that uses GPU accelerated VoxBlox) library by NVIDIA.

But one of they key commonality in these set of algorithms is that these algorithms don't instruct the UV to choose optimal actions to explore the area. Swarm robotics can also be used to explore unknown areas by assigning different areas to agents/peers while also minimising overlapping areas and time.

One of the interesting approaches can be seen in the paper "Decentralised Multi-Robot Exploration using Monte Carlo Tree Search". The author intrudces the use of Decentralised Monte Carlo Tree for exploration and division of task among the peers.

![Multi Agent Exploration](../../pics/swarm/image.png)

Problem Statement:\
To explore a specified unknown area and classify the area into +1(occupied), 0(unknown), -1(free space). The area is divided into grids for the agents of the swarm have to classify into the above occupancy grid representation.
For example:
Given a dimension of an area to be mapped out like 100m x 100m the area is divided into grids of any size (for eg. 1m x 1m). The aim is to assign the values 0, -1, +1 to each of the grids present.

The paper proposes a Monte Carlo Tree Search based method for division of task among the peers. Therefore the objective function can be defined as

$$\hat{p} = \arg\max_{p \in \mathcal{P}} \ \mathbb{E}[V(x_0, p)]$$

The paper describes the reward function as

$$ V(x, p) = \frac{N^{f}_{\text{known}}}{N_{\text{cells}}} = 1 - \frac{N^{f}_{\text{unknown}}}{N_{\text{cells}}} $$

For Hugo, ensure your `config.toml` has Markdown rendering configured for math:

```toml
[markup.goldmark.extensions.passthrough]
enable = true
[markup.goldmark.extensions.passthrough.delimiters]
block = [["$$", "$$"]]
inline = [["$", "$"]]
```

Alternatively, use display math syntax without extra spaces:

$$V(x, p) = \frac{N^{f}_{\text{known}}}{N_{\text{cells}}} = 1 - \frac{N^{f}_{\text{unknown}}}{N_{\text{cells}}}$$


