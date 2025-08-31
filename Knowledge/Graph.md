# Graph

## Minimum Spanning Tree
### Prim's Algorithm
- Starts with a single vertex and grows the MST by iteratively adding the lowest-weight edge that connects a vertex in the growing tree to a vertex outside it. 
- It's a greedy algorithm, meaning it makes the locally optimal choice at each step. 

### Kruskal's Algorithm
- Sorts all edges by weight in ascending order. 
- It then iterates through the sorted edges, adding an edge to the MST if it doesn't form a cycle with the edges already selected. 

## Dijkstra Algorithm
- Dijkstra's algorithm is a graph search algorithm that finds the shortest path from a single source node to all other nodes in a weighted graph with non-negative edge weights. It works by iteratively selecting the unvisited node with the smallest known distance from the source, updating the distances to its neighbors, and marking the node as visited. 
- Only works on graphs with non-negative edge weights. It relies on a greedy approach that assumes a shortest path cannot be improved by later considering a path with a negative edge.
- Typically O(E log V) or O(E + V log V) with a min-priority queue, where V is the number of vertices and E is the number of edges.

## Bellman–Ford Algorithm
- The Bellman-Ford algorithm finds the shortest paths from a single source vertex to all other vertices in a weighted directed graph, even when edge weights are negative. It works by repeatedly "relaxing" all edges in the graph, updating distances if a shorter path is found, for a total of |V|-1 iterations. A final iteration is used to detect negative cycles, which would make shortest paths impossible to determine. 
- Can handle graphs with negative edge weights. It can also detect negative cycles, which would lead to infinitely decreasing path lengths.
- Time Complexity: O(V * E)
- V nodes, V - 1 iterations