
# Strongly connected component

- Take care of **Back Edge and Cross Edge** 
- Time complexity O(V+E)
 
 



## Code

```javascript
class Solution
{
	public:
	
    int timee;
    vector<vector<int>> ans;
    vector<int> tin,low;
    vector<bool> Instack;
    stack<int> s;
    
    
    void dfs(int i,vector<int> adj[]){
        
        tin[i] = low[i] = ++ timee;
        s.push(i);
        Instack[i] = true;
        
        for(int nb : adj[i]){
            if(!tin[nb]){
                dfs(nb,adj);
                low[i] = min(low[i],low[nb]);
            }
            else if(Instack[nb])
                low[i] = min(low[i],tin[nb]);
        }
        
        if(tin[i] == low[i]){
            vector<int> temp;
            while(s.top() != i){
                Instack[s.top()] = false;
                temp.push_back(s.top()); s.pop();
            }
            temp.push_back(s.top());
            Instack[s.top()] = false;
            s.pop();
            sort(temp.begin(),temp.end());
            ans.push_back(temp);
        }
    }
    vector<vector<int>> tarjans(int V, vector<int> adj[])
    {
        timee = 0;
        tin.resize(V);
        low.resize(V);
        Instack.resize(V);
        for(int i = 0;i<V;i++){
            if(!tin[i])
                dfs(i,adj);
        }
        sort(ans.begin(),ans.end());
        return ans;
    }
};
```

