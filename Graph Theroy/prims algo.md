
# Prim's algotihm
to find mst

## code

```javascript
    vector<bool> visited(n,false);
        priority_queue<pair<int,int>,vector<pair<int,int>>,greater<pair<int,int>>>q;
        int ans = 0;
        q.push(make_pair(0,0));
        while(!q.empty())
        {
            pair<int,int> tp = q.top();
            q.pop();
            if(visited[tp.second]) continue;
            visited[tp.second] = true;
            ans+= tp.first;
            for(auto x : adj[tp.second]){
                if(!visited[x.second]){
                    q.push(x);
                }
            }
        }

```

  
