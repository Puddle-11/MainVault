---
tags:
  - resource
Area: "[[Programming]]"
---
## Randomized Prims Algorithm


### Explanation
Prims algorithm is a simple algorithm to make a Simply Connected Maze.

In my implementation i had walls between each cell on a grid, however in other implementations such as the Medium paper one, the *walls* are simply other cells with some cells being regarded as walls and others as floor or clearable tiles.

The complexity of this algorithm is low, since it is not recursive and doesn't include the possibility for loops.
### Pseudo-Code

1. Start with a grid of unvisited cells.
2. Create two empty sets, marking visited cells, and what we’ll call frontier cells.
3. Choose a random cell as the starting point, and add it to the visited set.
4. Add all unvisited cells that are adjacent to the current cell to the frontier set.
5. Choose a cell randomly from the frontier set and make it the current cell, removing it from the frontier set and adding it to the visited set.
6. Remove the wall between the current cell and a random adjacent cell that belongs to the visited set.
7. Repeat steps 4 through 6 until there are no more frontier cells.


## References
[Prims Algorithm Medium paper](https://cantwell-tom.medium.com/prims-algorithm-as-a-maze-in-javascript-aec7415ad2cd)


