
# BFS

Breadth first search is one of the basic and essential searching algorithms on graphs.

As a result of how the algorithm works, the path found by breadth first search to any node is the shortest path to that node, i.e the path that contains the smallest number of edges in unweighted graphs.




## code

```javascript
vector<int> bfsOfGraph(int V, vector<int> adj[]) {
    // Code here
    vector<bool> visited(V,false);
    vector<int> bfs;

    queue<int> track;
    track.push(0);
    visited[0] = true;
        
    int t;
    while(track.size()>0)
    {
        t = track.front();
        track.pop();
        
        bfs.push_back(t);
        for(auto nb : adj[t]){
            if(!visited[nb]) {
                track.push(nb);
                visited[nb] = true;
            }
        }
    }
    return bfs;
}
```

  
## Complexity

- Time complexity **O(V+E)**

- Space complexity **O(V)**

  
