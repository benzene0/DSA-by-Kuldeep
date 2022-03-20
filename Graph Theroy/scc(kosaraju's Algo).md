
# Strongly connected component(Kosaraju Algo)

- Take care of **scc1 ---> scc2** (reverse graph) **scc1 <---- scc2** 
- Time complexity O(3*(V+E) )




## Code

```javascript
class Solution
{
	public:
	void dfs_before(int i, vector<int> adj[],vector<int>&visited,stack<int>& st)
	{
	    visited[i] = true;
	    for(auto x : adj[i])
	    {
	        if(!visited[x]) dfs_before(x,adj,visited,st);
	    }
	    st.push(i);
	}
	
	void reverse(int V,vector<int> adj[],vector<int> rev_adj[])
	{
	    for(int i = 0;i<V;i++)
	    {
	        for(auto j: adj[i])
	        {
	            rev_adj[j].push_back(i);
	        }
	    }
	}
	
	void dfs_after(int i, vector<int> adj[],vector<int>&visited)
	{
	    visited[i] = true;
	    for(auto x : adj[i])
	    {
	        if(!visited[x]) dfs_after(x,adj,visited);
	    }
	}
	
    int kosaraju(int V, vector<int> adj[])
    {
        vector<int> visited(V,false);
        stack<int> st;
        for(int i = 0;i<V;i++){
            if(!visited[i])
            {
                dfs_before(i,adj,visited,st);
            }
            
        }
        
        for(int i = 0;i<V;i++){
            visited[i] = false;
        }
        vector<int> rev_adj[V];
        reverse(V,adj,rev_adj);
        int ans = 0;
        while(st.size() > 0)
        {
            int c_idx = st.top();
            st.pop();
            if(!visited[c_idx]){
                ans++;
                dfs_after(c_idx,rev_adj,visited);
            }
        }
        
        return ans;
    }
};

```

