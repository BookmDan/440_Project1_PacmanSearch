# CS440 Project 1: Dureke Sanchez/ Daniel Oh

# 440_Project1_PacmanSearch

This project involves implementing search algorithms to guide Pacman through mazes, collect dots, and navigate efficiently using Depth First Search (DFS), Breadth First Search (BFS), A* search, and other techniques. The project builds upon Berkeley's CS188 AI course.

# Running the Project

To test the Pacman agent, first ensure everything is set up by running the following command:

```
python pacman.py -p SearchAgent -a fn=bfs
```

# Project Structure
- search.py: Contains the search algorithms you'll implement, such as BFS, A*, and DFS.
- searchAgents.py: Implements the SearchAgent, which executes paths using the search algorithms.
- pacman.py: The main game script that runs the Pacman simulation.

# Tasks
1. Breadth-First Search (BFS): Implement the BFS algorithm in breadthFirstSearch function in search.py. Make sure it avoids revisiting states.
    Test BFS with the following command:

```
python pacman.py
```

2. A Search*: Implement the A* search algorithm in aStarSearch in search.py. A* uses a heuristic function, such as nullHeuristic.

Test A* with:


3. Find Path to Closest Dot: Implement the function findPathToClosestDot in searchAgents.py. This function should guide Pacman to the nearest dot.

Test the Closest Dot Search Agent:

4. 

# Acknowledgements

This project is based on Berkeley's CS188 Pacman project.
