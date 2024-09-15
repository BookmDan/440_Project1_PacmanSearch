# CS440 Project 1: Dureke Sanchez/ Daniel Oh

# Project1 - PacmanSearch

This project involves implementing search algorithms to guide Pacman through mazes, collect dots, and navigate efficiently using Depth First Search (DFS), Breadth First Search (BFS), A* search, and other techniques. The project builds upon Berkeley's CS188 AI course.

# Running the Project

For sanity check try:
```
python pacman.py
```
and you should see the following:

![giphy2_logo](https://github.com/user-attachments/assets/e86308c5-f3ae-4eb5-89b6-62c756d832c4)

To test the Pacman agent, first ensure everything is set up by running the following command:
```
python pacman.py -l tinyMaze -p SearchAgent -a fn=tinyMazeSearch
```
This tells the SearchAgent to use tinyMazeSearch as its search algorithm. 
We should see the below animation pop up. 
<img width="244" alt="Screenshot 2024-09-12 at 2 59 39 PM" src="https://github.com/user-attachments/assets/f488cdf1-ff65-48b9-be6f-cdd1848e4284">

# Project Structure
- search.py: Contains the search algorithms you'll implement, such as BFS, A*, and DFS.
- searchAgents.py: Implements the SearchAgent, which executes paths using the search algorithms.
- pacman.py: The main game script that runs the Pacman simulation.

# Tasks
## 1. Depth-First Search (DFS):
  
Implement the DFS algorithm in depthFirstSearch function in search.py. Make sure it avoids revisiting states. 
By default the SearchAgent.py uses the Depth First Search(DFS) as the search function. 
```
python pacman.py -l tinyMaze -p SearchAgent
python pacman.py -l mediumMaze -p SearchAgent
python pacman.py -l bigMaze -z .5 -p SearchAgent
```
<img width="753" alt="Screenshot 2024-09-12 at 2 49 08 PM" src="https://github.com/user-attachments/assets/13654c85-39eb-4a15-89c0-d9e785da136a">

<img width="1112" alt="Screenshot 2024-09-12 at 2 44 35 PM" src="https://github.com/user-attachments/assets/5a3157ef-87f7-4ea9-a48f-6bf141beaa1d">

It does seem to deeply explore one path before backtracking and consistently exploring all states on the way to the goal as expected for a DFS search path. DFS's approach to exploring nodes might lead to suboptimal paths due to its depth-first strategy. DFS is not guaranteed to find the shortest or least-cost path, as it explores nodes in a LIFO manner and may not prioritize exploring shorter paths. Instead it explores deeply down one branch before finding out whether or not there is a solution then will move to the next branch and explore till failure for that branch also. 

We expected a solution length of 130. For the mediumMaze we got a length of 146.

## 2. Breadth-First Search

Test using the following 'fn=bfs':
```
python pacman.py -l tinyMaze -p SearchAgent -a fn=bfs
python pacman.py -l mediumMaze -p SearchAgent -a fn=bfs
python pacman.py -l bigMaze -p SearchAgent -a fn=bfs -z .5
```
You should see something like this: 

<img width="1108" alt="Screenshot 2024-09-12 at 2 43 52 PM" src="https://github.com/user-attachments/assets/eafc7924-2152-4746-82f8-9cf5c1f5cb43">

As predicted, the BFS search takes a more wide-net search approach, first exploring the shallow paths, before eventually getting to the solution. BFS ensures shortest-path, because it explores all nodes at a given level before moving to deeper levels. BFS is also useful for solving the Eight Puzzle state problem because of its priority for finding the **optimal** state i.e. shortest path, as well as because of its quality for **completeness**, meaning BFS explores all nodes at the current level, which ensures that no potential solution is skipped. 

## 4. A Search*: 

Implement the A* search algorithm in aStarSearch in search.py. A* uses a heuristic function, such as nullHeuristic.

Run A* with the corresponding fn=astar,heuristic=manhattanHeuristic:
```
python pacman.py -l bigMaze -z .5 -p SearchAgent -a fn=astar,heuristic=manhattanHeuristic --frameTime=0
python pacman.py -l bigMaze -z .5 -p SearchAgent -a fn=astar,heuristic=euclideanHeuristic --frameTime=0

```
Note: You can run A* search without a heuristic as jsut fn=astar. However, this would be a uniformCost search algorithm instead. If another heuristic is implemented, that may be used as well. For instance, euclideanHeuristic is another possible heuristic.

Test A* with:
```
python autograder.py -q q4
```
<img width="574" alt="Screenshot 2024-09-13 at 9 25 41 AM" src="https://github.com/user-attachments/assets/588b43f2-d99c-4345-8924-ed18c08bcb19">

A* works by weighing the combined state cost and a heuristic cost. The best choice of those available will be greedily chosen. A* requires a heuristic, as seen in the command to use fn=astar. A null heuristic in which the h(n) of: f(n) = g(n) + h(n), would be zero. This would just be a uniform Cost search, and is defined as default if no heuristic is given. If no heuristic is given for bigMaze, 620 nodes are expanded. With manhattan Heuristic, 549 nodes are expanded instead. Therefore, slightly faster.

A* works with the use of a priority queue to sort all possible choices based on their f(n) value. Since a priority queue's value is its priority, nodes with a higher f(n) value have a higher priority and will be the next node explored. This optimizes the search and avoids redundant paths or paths that lead away from the objective. 

The code works by checking all possible sucessors of the current state and pushing them into a priority queue. The next node to be visited is based on whatever is at the head of the queue. Thus, all possible nodes are being considered, but the next action is based on whatever is the best towards the goal state.

## 8. Find Path to Closest Dot: 

Implement the function findPathToClosestDot in searchAgents.py. This function should guide Pacman to the nearest dot.
It checks whether current state has food or not. It then checks for the next valid steps through **getSuccessor** method. Finally, it uses BFS to find the next closest dot. This doesn't account for the global goal and is only useful for finding the next closest dot, so should suffice as a suboptimal, greedy solution to finding the next closest dot. 

Run ClosestDotSearchAgent with:
```
python pacman.py -l bigSearch -p ClosestDotSearchAgent -z .5 --frameTime=0
```

Test the Closest Dot Search Agent:
```
python autograder.py -q q8
```

![closestdot](https://github.com/user-attachments/assets/aa267799-cf2f-481d-96c6-3dff364f1450)

# Acknowledgements

This project is based on Berkeley's CS188 Pacman project.
