# EX 2A BACKTRACKING - RAT IN MAZE PROBLEM
## DATE:
## AIM:
To implement the Rat in a Maze problem using backtracking and find all possible paths from the start to the destination in a given maze.


## Algorithm
1. Initialize a solution matrix sol of the same size as the maze, filled with zeros.
2. Start from cell (0, 0) and attempt to reach the destination cell (N-1, N-1).
3. Check if the current cell is safe (i.e., within bounds and not blocked). If safe, mark it as part of the path.
4. Recursively move either right or down, trying to find a path to the goal. If neither move works, backtrack by unmarking the current cell.
5. If a path is found, print the solution matrix; otherwise, print that no solution exists. 

## Program:
```
Program to implement Rat in a Maze.
Developed by: Vinush CV
Register Number: 212222230176
```
```python
N = 4
 

def printSolution( sol ):
     
    for i in sol:
        for j in i:
            print(str(j) + " ", end ="")
        print("")
 

def isSafe( maze, x, y ):
     
    if x >= 0 and x < N and y >= 0 and y < N and maze[x][y] == 1:
        return True
     
    return False
 

def solveMaze( maze ):
     
    # Creating a 4 * 4 2-D list
    sol = [ [ 0 for j in range(4) ] for i in range(4) ]
     
    if solveMazeUtil(maze, 0, 0, sol) == False:
        print("Solution doesn't exist");
        return False
     
    printSolution(sol)
    return True
     

def solveMazeUtil(maze, x, y, sol):
    # Write your code here
    
    # If (x, y) is the destination, return true
    if x == N - 1 and y == N - 1:
        sol[x][y] = 1
        return True

    # Check if the current cell is safe
    if isSafe(maze, x, y):
        # Mark x, y as part of the solution path
        sol[x][y] = 1

        # Move down in the maze
        if solveMazeUtil(maze, x + 1, y, sol):
            return True
        
        # Move right in the maze
        if solveMazeUtil(maze, x, y + 1, sol):
            return True
        
        # If neither down nor right leads to a solution, backtrack
        sol[x][y] = 0
        return False

    return False




# Driver program to test above function
if __name__ == "__main__":
    # Initialising the maze
    maze = [ [1, 0, 0, 0],
             [1, 1, 0, 1],
             [0, 1, 0, 0],
             [1, 1, 1, 1] ]
              
    solveMaze(maze)

```

## Output:

![image](https://github.com/user-attachments/assets/e510d49d-fc6b-4117-95bc-29d98d1dc422)


## Result:
The Rat in a Maze program executed successfully, and a valid path from the start to the destination was found and display.
