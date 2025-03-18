---
layout: post 
title: Teach
search_exclude: true
permalink: /teach/undecidable_problems_graphs_heuristics
---


# 🚀 AP CSP: Undecidable Problems, Graphs, & Heuristics  

## 📌 Learning Goals  
- Understand **undecidable problems** and why some questions have no algorithmic solution.  
- Learn **graphs** and their real-world applications.  
- Use **heuristics** to make fast, intelligent guesses in problem-solving.  
- Engage with **"Popcorn Hacks"**—quick interactive coding exercises!  

---

## 🧠 1. Undecidable Problems  

### ❓ What Are Undecidable Problems?  
Some problems have **no algorithm** that can always provide the correct answer. These are called **undecidable problems**.  

One famous example is the **Halting Problem**, discovered by **Alan Turing**.  

### ⚠️ The Halting Problem  
*"Can we write a program that decides whether any given program will halt or run forever?"*  
Mathematicians proved that no such algorithm can always work!  

#### 🖥️ Python Example (Simulated Halting Problem)  
```python
def halting_checker(program, input_data):
    if program_halts(program, input_data):
        return "Yes, it halts!"
    else:
        return "No, it runs forever!"
```

# 🗺️ 2. Graphs & Their Uses

## 📍 What is a Graph?
- A graph consists of nodes (points) connected by edges (lines). Used in:
- ✅ Social Networks
- ✅ Web Page Linking
- ✅ Navigation Systems

## 🎯 Example: Social Network Graph

```python
graph = {
    "Alice": ["Bob", "Charlie"],
    "Bob": ["Alice", "David"],
    "Charlie": ["Alice", "Eve"],
    "David": ["Bob"],
    "Eve": ["Charlie"]
}

print("Alice's friends:", graph["Alice"])
```

## 🔍 Finding Paths: Breadth-First Search (BFS)
- BFS finds the shortest path in an unweighted graph.

## 🖥️ Python Example (Finding Shortest Path)

```python
from collections import deque

def bfs(graph, start, target):
    queue = deque([(start, [start])])
    
    while queue:
        node, path = queue.popleft()
        if node == target:
            return path
        
        for neighbor in graph.get(node, []):
            if neighbor not in path:
                queue.append((neighbor, path + [neighbor]))
    
    return None  # No path found

print("Path from Alice to Eve:", bfs(graph, "Alice", "Eve"))
```

## 🔎 Depth-First Search (DFS)
- DFS explores as far as possible along a path before backtracking.

## 🖥️ Python Example (DFS)

```python
def dfs(graph, start, target, path=[]):
    path = path + [start]
    
    if start == target:
        return path
    
    for neighbor in graph.get(start, []):
        if neighbor not in path:
            result = dfs(graph, neighbor, target, path)
            if result:
                return result
    
    return None  # No path found

print("DFS Path from Alice to Eve:", dfs(graph, "Alice", "Eve"))
```

## 🍿 Popcorn Hack: Modify the graph to represent your favorite city’s metro system!
- Add stations as nodes and train lines as edges! 🚆


# 🚀 3. Dijkstra’s Algorithm (Finding Shortest Path in Weighted Graphs)
- Unlike BFS (which works for unweighted graphs), Dijkstra’s Algorithm finds the shortest path in a weighted graph.

## 🖥️ Python Example (Dijkstra's Algorithm)

```python
import heapq

def dijkstra(graph, start):
    shortest_paths = {node: float('inf') for node in graph}
    shortest_paths[start] = 0
    priority_queue = [(0, start)]
    
    while priority_queue:
        current_distance, current_node = heapq.heappop(priority_queue)
        
        if current_distance > shortest_paths[current_node]:
            continue
        
        for neighbor, weight in graph[current_node].items():
            distance = current_distance + weight
            if distance < shortest_paths[neighbor]:
                shortest_paths[neighbor] = distance
                heapq.heappush(priority_queue, (distance, neighbor))
    
    return shortest_paths

weighted_graph = {
    "A": {"B": 1, "C": 4},
    "B": {"A": 1, "C": 2, "D": 5},
    "C": {"A": 4, "B": 2, "D": 1},
    "D": {"B": 5, "C": 1}
}

print("Shortest paths from A:", dijkstra(weighted_graph, "A"))
```

# 🏆 4. Heuristics - Smart Guessing

## 💡 What is a Heuristic?
- A heuristic is a fast, rule-of-thumb approach to finding solutions.

🔹 Used in AI, robotics, and gaming.
🔹 Faster than brute-force solutions but not guaranteed to be perfect.

## 🚀 A* Algorithm - Heuristic-Based Pathfinding
- A* (A-Star) finds the shortest path by balancing:

- Actual cost so far.
- Estimated cost to reach the goal (heuristic).

## 🖥️ Python Example (A* Algorithm)

```python
import heapq

def a_star(graph, start, goal, heuristic):
    priority_queue = [(0, start, [])]  # (cost, node, path)
    
    while priority_queue:
        cost, node, path = heapq.heappop(priority_queue)
        
        if node == goal:
            return path + [node]
        
        for neighbor, edge_cost in graph.get(node, {}).items():
            heapq.heappush(priority_queue, (cost + edge_cost + heuristic(neighbor, goal), neighbor, path + [node]))
    
    return None  # No path found

def heuristic(node, goal):
    return abs(ord(goal[0]) - ord(node[0]))  # Fake heuristic based on letters

print("A* Path from A to D:", a_star(weighted_graph, "A", "D", heuristic))
```