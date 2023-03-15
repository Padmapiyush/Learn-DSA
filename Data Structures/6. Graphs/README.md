# Graphs in C++:

### Representing Graphs:
There are two commonly used ways to represent graphs in C++:
- **Adjacency Matrix:** A 2D array where the value at arr[i][j] represents the weight of the edge from node i to node j.
- **Adjacency List:** A vector of vectors where each vector represents the nodes adjacent to a particular node.
### Breadth First Search (BFS):
BFS is an algorithm used for traversing or searching a graph. It starts at the root node and visits all the nodes at the current depth before moving on to the nodes at the next depth. BFS uses a queue data structure to keep track of the nodes to be visited.

```cpp
void bfs(vector<vector<int>>& graph, int start) {
  vector<bool> visited(graph.size(), false);
  queue<int> q;
  q.push(start);
  visited[start] = true;
  while (!q.empty()) {
    int node = q.front();
    q.pop();
    cout << node << " ";
    for (int i = 0; i < graph[node].size(); i++) {
      int neighbor = graph[node][i];
      if (!visited[neighbor]) {
        q.push(neighbor);
        visited[neighbor] = true;
      }
    }
  }
}
```

### Depth First Search (DFS):
DFS is another algorithm used for traversing or searching a graph. It starts at the root node and explores as far as possible along each branch before backtracking. DFS uses a stack data structure to keep track of the nodes to be visited.

```cpp
void dfs(vector<vector<int>>& graph, int node, vector<bool>& visited) {
  visited[node] = true;
  cout << node << " ";
  for (int i = 0; i < graph[node].size(); i++) {
    int neighbor = graph[node][i];
    if (!visited[neighbor]) {
      dfs(graph, neighbor, visited);
    }
  }
}

void dfsDriver(vector<vector<int>>& graph, int start) {
  vector<bool> visited(graph.size(), false);
  dfs(graph, start, visited);
}

```
### Dijkstra's Algorithm:
Dijkstra's algorithm is used to find the shortest path between two nodes in a graph. It works by assigning a tentative distance value to every node and then updating the values of adjacent nodes until the shortest path is found.

```cpp
void dijkstra(vector<vector<pair<int, int>>>& graph, int start) {
  priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq;
  vector<int> dist(graph.size(), INT_MAX);
  dist[start] = 0;
  pq.push(make_pair(0, start));
  while (!pq.empty()) {
    int node = pq.top().second;
    pq.pop();
    for (int i = 0; i < graph[node].size(); i++) {
      int neighbor = graph[node][i].first;
      int weight = graph[node][i].second;
      if (dist[neighbor] > dist[node] + weight) {
        dist[neighbor] = dist[node] + weight;
        pq.push(make_pair(dist[neighbor], neighbor));
      }
    }
  }
}
```

### Bellman-Ford Algorithm:
Bellman-Ford algorithm is used to find the shortest path between two nodes in a graph that may have negative edge weights. It works by assigning a tentative distance value to every node and then updating the values of adjacent nodes until the shortest path is found.

```cpp
#include <iostream>
#include <vector>
#include <utility>

using namespace std;

const int INF = 1e9;

void bellmanFord(vector<vector<pair<int, int>>>& graph, int start) {
    vector<int> dist(graph.size(), INF);
    dist[start] = 0;
    
    // Relax edges |V|-1 times
    for (int i = 0; i < graph.size() - 1; i++) {
        for (int j = 0; j < graph.size(); j++) {
            for (int k = 0; k < graph[j].size(); k++) {
                int u = j;
                int v = graph[j][k].first;
                int weight = graph[j][k].second;
                if (dist[u] != INF && dist[v] > dist[u] + weight) {
                    dist[v] = dist[u] + weight;
                }
            }
        }
    }
    
    // Check for negative cycles
    bool hasNegativeCycle = false;
    for (int j = 0; j < graph.size(); j++) {
        for (int k = 0; k < graph[j].size(); k++) {
            int u = j;
            int v = graph[j][k].first;
            int weight = graph[j][k].second;
            if (dist[u] != INF && dist[v] > dist[u] + weight) {
                hasNegativeCycle = true;
                break;
            }
        }
        if (hasNegativeCycle) break;
    }
    
    if (hasNegativeCycle) {
        cout << "Graph contains negative cycle\n";
    } else {
        for (int i = 0; i < graph.size(); i++) {
            cout << "Distance from " << start << " to " << i << " is " << dist[i] << "\n";
        }
    }
}

int main() {
    int n, m, start;
    cin >> n >> m >> start;
    
    vector<vector<pair<int, int>>> graph(n);
    for (int i = 0; i < m; i++) {
        int u, v, weight;
        cin >> u >> v >> weight;
        graph[u].push_back(make_pair(v, weight));
    }
    
    bellmanFord(graph, start);
    
    return 0;
}
```
This implementation takes an input graph as an adjacency list, where each vertex is represented by an integer index and each edge is represented as a pair of integers **`(v, w)`** denoting the vertex it connects to and the weight of the edge, respectively. The algorithm runs in O(V * E) time, where V is the number of vertices in the graph and E is the number of edges.

### Kruskal's Algorithm:
Kruskal's algorithm is used to find the minimum spanning tree of a graph. It works by sorting the edges by weight and then adding the edges with the lowest weight to the spanning tree, as long as the edge does not create a cycle.

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

struct Edge {
    int u, v, weight;
    
    bool operator<(Edge const& other) {
        return weight < other.weight;
    }
};

int findParent(int v, vector<int>& parent) {
    if (parent[v] == v) return v;
    return parent[v] = findParent(parent[v], parent);
}

void kruskal(vector<Edge>& edges, int n) {
    vector<int> parent(n);
    for (int i = 0; i < n; i++) {
        parent[i] = i;
    }
    
    vector<Edge> result;
    
    for (Edge edge : edges) {
        int u = edge.u;
        int v = edge.v;
        int weight = edge.weight;
        int parentU = findParent(u, parent);
        int parentV = findParent(v, parent);
        if (parentU != parentV) {
            result.push_back(edge);
            parent[parentU] = parentV;
        }
    }
    
    for (Edge edge : result) {
        cout << edge.u << " - " << edge.v << " : " << edge.weight << "\n";
    }
}

int main() {
    int n, m;
    cin >> n >> m;
    
    vector<Edge> edges(m);
    for (int i = 0; i < m; i++) {
        int u, v, weight;
        cin >> u >> v >> weight;
        edges[i] = {u, v, weight};
    }
    sort(edges.begin(), edges.end());
    
    kruskal(edges, n);
    
    return 0;
}
```
This implementation takes an input graph as a list of edges, where each edge is represented as a triplet **`(u, v, weight)`** denoting the vertices it connects and the weight of the edge, respectively. The algorithm sorts the edges by weight and builds the minimum spanning tree (MST) by iterating over the sorted edges and adding them to the MST if they do not form a cycle with the already added edges. The algorithm uses the disjoint-set data structure to keep track of the connected components of the graph. The time complexity of Kruskal's Algorithm is O(E log E), where E is the number of edges in the graph.
### Prim's Algorithm:
Prim's algorithm is used to find the minimum spanning tree of a graph. It works by starting at a node and then adding the edge with the lowest weight to the spanning tree, as long as the edge does not create a cycle.

```cpp
#include <iostream>
#include <vector>
#include <queue>

using namespace std;

struct Edge {
    int to, weight;
    bool operator>(Edge const& other) {
        return weight > other.weight;
    }
};

void prim(vector<vector<Edge>>& graph, int start) {
    int n = graph.size();
    vector<bool> visited(n, false);
    priority_queue<Edge, vector<Edge>, greater<Edge>> pq;
    
    // Add start vertex to priority queue
    visited[start] = true;
    for (Edge edge : graph[start]) {
        pq.push(edge);
    }
    
    // Build MST
    int mstWeight = 0;
    while (!pq.empty()) {
        Edge edge = pq.top();
        pq.pop();
        int to = edge.to;
        int weight = edge.weight;
        if (visited[to]) continue;
        visited[to] = true;
        mstWeight += weight;
        for (Edge next : graph[to]) {
            if (!visited[next.to]) {
                pq.push(next);
            }
        }
    }
    
    cout << "Minimum spanning tree weight: " << mstWeight << "\n";
}

int main() {
    int n, m, start;
    cin >> n >> m >> start;
    
    vector<vector<Edge>> graph(n);
    for (int i = 0; i < m; i++) {
        int u, v, weight;
        cin >> u >> v >> weight;
        graph[u].push_back({v, weight});
        graph[v].push_back({u, weight});
    }
    
    prim(graph, start);
    
    return 0;
}
```
This implementation takes an input graph as an adjacency list of weighted edges, where each edge is represented as a pair of integers **`(v, w)`** denoting the vertex it connects to and the weight of the edge, respectively. The algorithm builds the minimum spanning tree (MST) by repeatedly adding the lightest edge that connects a visited vertex to an unvisited vertex. The algorithm uses a priority queue to efficiently find the next edge to add. The time complexity of Prim's Algorithm is O(E log V), where E is the number of edges and V is the number of vertices in the graph.

### Kahn's Algorithm / Topological Sort:
Topological sort is used to order the nodes in a directed acyclic graph (DAG) in such a way that if there is a path from node A to node B, then A comes before B in the ordering.

```cpp
include <iostream>
#include <vector>
#include <queue>

using namespace std;

vector<int> topologicalSort(vector<vector<int>>& graph) {
    int n = graph.size();
    vector<int> inDegree(n, 0);
    for (int u = 0; u < n; u++) {
        for (int v : graph[u]) {
            inDegree[v]++;
        }
    }
    
    queue<int> q;
    for (int u = 0; u < n; u++) {
        if (inDegree[u] == 0) {
            q.push(u);
        }
    }
    
    vector<int> result;
    while (!q.empty()) {
        int u = q.front();
        q.pop();
        result.push_back(u);
        for (int v : graph[u]) {
            inDegree[v]--;
            if (inDegree[v] == 0) {
                q.push(v);
            }
        }
    }
    
    if (result.size() != n) {
        // Graph has a cycle
        return vector<int>();
    }
    
    return result;
}

int main() {
    int n, m;
    cin >> n >> m;
    
    vector<vector<int>> graph(n);
    for (int i = 0; i < m; i++) {
        int u, v;
        cin >> u >> v;
        graph[u].push_back(v);
    }
    
    vector<int> result = topologicalSort(graph);
    
    if (result.empty()) {
        cout << "The graph has a cycle\n";
    } else {
        for (int u : result) {
            cout << u << " ";
        }
        cout << "\n";
    }
    
    return 0;
}
```
This implementation takes an input graph as an adjacency list of directed edges, where each edge is represented as a pair of integers **`(u, v)`** denoting the source and target vertices, respectively. The algorithm builds a topological ordering of the vertices by repeatedly removing vertices with zero in-degree (i.e., vertices that have no incoming edges) from the graph. The algorithm uses a queue to efficiently store and process the vertices with zero in-degree. If the resulting ordering has fewer than n vertices, then the graph has a cycle and the algorithm reports an error. The time complexity of Kahn's Algorithm is O(V + E), where V is the number of vertices and E is the number of edges in the graph.

### Tanjan's Algorithm / Strongly Connected Components:
Strongly connected components (SCCs) are subsets of nodes in a directed graph where every node in the subset can reach every other node in the subset. **Tarjan's algorithm** is commonly used to find the SCCs in a graph.

```cpp
#include <iostream>
#include <vector>
#include <stack>

using namespace std;

void dfs(int u, vector<vector<int>>& graph, vector<int>& ids, vector<int>& low, vector<bool>& onStack, stack<int>& st, int& id) {
    ids[u] = low[u] = id++;
    onStack[u] = true;
    st.push(u);
    for (int v : graph[u]) {
        if (ids[v] == -1) {
            dfs(v, graph, ids, low, onStack, st, id);
            low[u] = min(low[u], low[v]);
        } else if (onStack[v]) {
            low[u] = min(low[u], ids[v]);
        }
    }
    if (ids[u] == low[u]) {
        while (true) {
            int v = st.top();
            st.pop();
            onStack[v] = false;
            if (u == v) break;
        }
    }
}

vector<vector<int>> findSCCs(vector<vector<int>>& graph) {
    int n = graph.size();
    vector<int> ids(n, -1), low(n);
    vector<bool> onStack(n, false);
    stack<int> st;
    int id = 0;
    for (int u = 0; u < n; u++) {
        if (ids[u] == -1) {
            dfs(u, graph, ids, low, onStack, st, id);
        }
    }
    
    vector<vector<int>> sccs;
    vector<int> comp(n, -1);
    int count = 0;
    for (int u = 0; u < n; u++) {
        if (comp[u] == -1) {
            int c = count++;
            sccs.push_back({});
            stack<int> st;
            st.push(u);
            while (!st.empty()) {
                int v = st.top();
                st.pop();
                if (comp[v] != -1) continue;
                comp[v] = c;
                sccs[c].push_back(v);
                for (int w : graph[v]) {
                    st.push(w);
                }
            }
        }
    }
    
    return sccs;
}

int main() {
    int n, m;
    cin >> n >> m;
    
    vector<vector<int>> graph(n);
    for (int i = 0; i < m; i++) {
        int u, v;
        cin >> u >> v;
        graph[u].push_back(v);
    }
    
    vector<vector<int>> sccs = findSCCs(graph);
    
    cout << "Number of strongly connected components: " << sccs.size() << "\n";
    for (int i = 0; i < sccs.size(); i++) {
        cout << "Component " << i << ": ";
        for (int u : sccs[i]) {
            cout << u << " ";
        }
        cout << "\n";
    }
    
    return 0;
}
```













