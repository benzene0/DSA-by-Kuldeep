
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

```javascript
    
```

- Time complexity  **O(V + ElogV)**
- Space complexity **O(V)**
