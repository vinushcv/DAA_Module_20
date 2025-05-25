# EX 2D BACKTRACKING - GRAPH COLORING PROBLEM
## DATE:
## AIM:
To solve the Graph Coloring Problem using backtracking, assigning colors to the vertices of a graph such that no two adjacent vertices share the same color while minimizing the number of colors used.



## Algorithm
1. Create a graph using an adjacency matrix for V vertices.
2. Initialize a color array with 0 (unassigned) for all vertices.
3. Use backtracking to assign colors (1 to m) to each vertex.
4. Ensure no two adjacent vertices have the same color using is_safe().
5. Print the color assignment if successful; else, print "Solution does not exist".

## Program:
```
Program to implement Graph Coloring Problem using backtracking.
Developed by:  R Guruprasad
Register Number: 212222240033
```
```python
class Graph:
    def __init__(self, vertices):
        self.V = vertices  # Number of vertices
        self.graph = [[0 for _ in range(vertices)] for _ in range(vertices)]  # Adjacency matrix

    def isSafe(self, color, vertex, c):
        for i in range(self.V):
            if self.graph[vertex][i] == 1 and color[i] == c:
                return False
        return True

    def graphColouringUtil(self, m, color, vertex):
        # Base case: If all vertices are assigned a color
        if vertex == self.V:
            return True

        # Try different colors for vertex
        for c in range(1, m + 1):
            if self.isSafe(color, vertex, c):
                color[vertex] = c  # Assign color c to vertex
                # Recur to assign colors to the rest of the vertices
                if self.graphColouringUtil(m, color, vertex + 1):
                    return True
                color[vertex] = 0  # Backtrack if coloring doesn't lead to a solution

        return False

    def graphColouring(self, m):
        color = [0] * self.V  # Initialize all vertices as uncolored

        if not self.graphColouringUtil(m, color, 0):
            print("Solution does not exist")
        else:
            # Print color assignment without list brackets
            print(f"Solution exist and Following are the assigned colours:\n{' '.join(map(str, color))}")

```

## Output:

![image](https://github.com/user-attachments/assets/56e5a09f-fd10-4ea8-bbf9-f659d2fa111b)


## Result:
The Graph Coloring program executed successfully, and the colors were assigned to the vertices such that no two adjacent vertices share the same color.
