# Graphs in C++

## Overview
Graphs model pairwise relationships between entities. A graph consists of vertices (nodes) connected by edges. Graphs can be directed or undirected, weighted or unweighted, and may contain cycles.

## Representations
- **Adjacency List**: vector of vectors (or lists) storing neighbors; efficient for sparse graphs.
- **Adjacency Matrix**: `n x n` matrix storing edge weights; useful for dense graphs.

## Traversal Algorithms
- **Depth-First Search (DFS)** explores as far as possible along each branch before backtracking.
- **Breadth-First Search (BFS)** explores neighbors level by level, ideal for shortest path in unweighted graphs.

## Example: Shortest Path in Unweighted Graph Using BFS
```cpp
#include <iostream>
#include <queue>
#include <vector>

std::vector<int> bfsShortestPath(const std::vector<std::vector<int>>& adj, int start) {
    const int n = static_cast<int>(adj.size());
    std::vector<int> distance(n, -1);
    std::queue<int> q;

    distance[start] = 0;
    q.push(start);

    while (!q.empty()) {
        int u = q.front();
        q.pop();
        for (int v : adj[u]) {
            if (distance[v] == -1) {
                distance[v] = distance[u] + 1;
                q.push(v);
            }
        }
    }
    return distance;
}

int main() {
    std::vector<std::vector<int>> adj = {
        {1, 2},    // 0
        {0, 3, 4}, // 1
        {0, 4},    // 2
        {1, 4, 5}, // 3
        {1, 2, 3}, // 4
        {3}        // 5
    };

    auto distance = bfsShortestPath(adj, 0);
    for (int d : distance) {
        std::cout << d << ' ';
    }
    std::cout << '\n';
    return 0;
}
```

### Complexity
- BFS Time: O(V + E)
- Space: O(V)
