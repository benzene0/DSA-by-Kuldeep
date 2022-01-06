
# Dijkstra's algorithm

- Dijkstra's algorithm find shortes path from a source to all other vertices

- MST and SPG may or may not be same



## code

```javascript
    //Function to find the shortest distance of all the vertices
    //from the source vertex S.
    vector <int> dijkstra(int V, vector<vector<int>> adj[], int S)
    {
        // Code here
        int INF = 10e6;
        
        vector<int> value(V,INF);
        value[S] = 0;
        vector<bool> visited(V,false);
        int t = V-1;
        while(t--){
            int k;
            int m = INF;
            for(int i = 0;i<V;i++){
                if(!visited[i] && value[i] < m){
                    k = i;
                    m = value[i];
                }
            }
            
            for(auto z: adj[k]){
                value[z[0]] = min(value[k]+z[1],value[z[0]]);
            }
            visited[k] = true;
        }
        
        return value;
    }
```

- Time complexity  **O(V^2)**
- Space complexity **O(V)**


## Using Heap

## code

```javascript
vector<int> dijkstra(vector<vector<vector<int>>>& graph,int source){
        priority_queue<pii,vector<pii>,greater<pii>> MinHeap;
        
        vector<int> dist(graph.size()+1,INT_MAX);
        vector<bool> visited(graph.size()+1,false);
        
        MinHeap.push({0,source}); // weith node
        dist[source] = 0;
        
        while(!MinHeap.empty()){
            auto [crntDis,crntNode] = MinHeap.top();
            MinHeap.pop();
            if(visited[crntNode]) continue;
            visited[crntNode] = true;
            for(int i = 0;i<graph[crntNode].size();i++){
                int nextNode = graph[crntNode][i][0], nextWet = graph[crntNode][i][1];
                int nextDis = crntDis+nextWet;
                if(!visited[nextNode] && nextDis<dist[nextNode]){
                    dist[nextNode] = nextDis;
                    MinHeap.push({nextDis,nextNode});
                }
            }
        }
        return dist;
    }
```
```javascript
    
```

- Time complexity  **O(V + ElogV)**
- Space complexity **O(V)**
