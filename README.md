# BFS & DFS Path Printing Algorithms (Python)

This project contains modified implementations of **Breadth-First Search (BFS)** and **Depth-First Search (DFS)** that not only traverse a graph but also **print the path** from the start node to every other node.

---

## 🚀 Project Description

The goal of this task is to modify the standard BFS and DFS algorithms so they can:

- Traverse the graph starting from a given node.
- Record the parent (previous node) of each visited node.
- Reconstruct and print the path from the start node to **every** node in the graph.

Both algorithms use a dictionary called `parent` to keep track of the path.

---

## 📂 Files Included

- `bfs_with_path.py` → BFS implementation that prints paths.
- `dfs_with_path.py` → DFS implementation that prints paths.
- `graph_example.py` → Contains example graph used for both algorithms.

---

## 🔍 BFS With Path

### ▶ Code Snippet

```python
from queue import Queue

def bfs_with_path(graph, start):
    q = Queue()
    q.put(start)

    visited = {node: False for node in graph}
    parent = {node: None for node in graph}  # to reconstruct path

    visited[start] = True

    while not q.empty():
        node = q.get()
        print(f"Visited: {node}")

        for neighbor in graph[node]:
            if not visited[neighbor]:
                visited[neighbor] = True
                parent[neighbor] = node
                q.put(neighbor)

    print("\nPaths from start node:")
    for node in graph:
        path = []
        current = node
        while current is not None:
            path.append(current)
            current = parent[current]
        path.reverse()
        print(f"Path to {node}: {path}")
