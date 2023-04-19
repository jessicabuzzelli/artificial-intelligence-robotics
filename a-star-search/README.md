# Search

## Background

A* Search is a pathfinding algorithm that leverages a distance heuristic to selectively explore an "open set" of navigation options it believes to be en route to a goal location according to a predefined loss scheme. Depending on the dimensionality of the coordinate system and the particular heuristic used, this algorithm _can_ be guaranteed to reach the optimal path.

Separately, Dijkstra's algorithm is another pathfinding algorithm that I found useful in this assignment to calculate a policy that maps each coordinate to the next along it's ideal path to the target destination. 

## Task
This task featured 3 challenges where a robot needed to navigate a warehouse to navigate towards a crate, pick it up, and deposit it at a target. There were different costs for straighline and diagonal movement and x-y tiles that were "viewed" by the robot were tracked for use as a scoring criteria. Crates could be delivered in any order.

In the first iteration, the warehouse map was not known to the robot. This approach used a straightforward implementation of A* to navigate the warehouse while building a map of coordinates that were previously considered. Since the robot started adjacent to the dropoff point and the warehouse layout did not change over time, I was able to invert the optimal path travelled to the crate when navigating back to the dropoff point. 

![A* search](search.gif)

In the second challenge, the robot was aware of the warehouse map and my task was to derive an optimal movement policy for each individual x-y coordinate given that each destination cell had a variable cost in addition to the movement cost incurred to arrive there. Since the problem had flipped from a N:1 pathfinding problem, I leveraged Dijkstra's algorithm rather than A* search. In the below animation, my implementation used to navigate to the target from a random cell. 

![dijkstra](dijkstra.gif)

Finally, I then had to create a navigation policy that would withstand stochastic movements according to a known distribution. This utilized a Dijkstra-based algorithm that summed up the expected cost of each movement when considering alternative paths.

![dijkstra-2](dijkstra-2.gif)