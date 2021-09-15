
# DFS

Depth first search : The idea behind DFS is to go as deep into the graph as possible, and backtrack once you are at a vertex without any unvisited adjacent vertices.


## Rrecursive code

```javascript
vector<vector<int>> adj; // graph represented as an adjacency list
int n; // number of vertices

vector<bool> visited;

void dfs(int v) {
    visited[v] = true;
    for (int u : adj[v]) {
        if (!visited[u])
            dfs(u);
    }
}
```

## Iteravtive code

```javascript
visited = [False]*G.size()
def dfs_iter(G,v):
	stack = [v]
	while len(stack) > 0:
		v = stack.pop()
		if not visited[v]:
			visit(v)
			visited[v] = True
			for w in G.neighbors(v):
				if not visited[w]:
					stack.append(w)
```
## Notes

- Time complexity O(V+E)


## Word Boggle 
### Question-> find a word is present in a grid or not 

```javascript
    bool dfs(int r,int c,int n,int m,int idx,string str,vector<vector<char>>& board,vector<vector<bool>>& visited)
    {
        static int ri[] = {1,1,1,-1,-1,-1,0,0};
        static int ci[] = {0,1,-1,0,1,-1,1,-1};
        
        if(r>=0 && r<n && c>=0 && c<m && idx<str.size() && str[idx] == board[r][c] && !visited[r][c])
        {
            idx++;
            if(idx == str.size()) return true;
            
            visited[r][c] = true;
            bool back = false;
            
            for(int k = 0;k<8;k++)
            {
                back |= dfs(r+ri[k],c+ci[k],n,m,idx,str,board,visited);
            }
            
            visited[r][c] = false;
            
            if(back) return true;
        }
        return false;
    }
	bool wordBoggle(vector<vector<char> >& board, string str) {
	    int n,m;
	    
	    n = board.size();
	    m = board[0].size();
	    
	    vector<vector<bool>> visited(n,vector<bool>(m,false));
	    
	    bool ans = false;
	    for(int i = 0;i<n;i++){
	        for(int j = 0;j<m;j++){
	            if(board[i][j] == str[0]){
	                ans |= dfs(i,j,n,m,0,str,board,visited);
	            }
	        }
	    }
	    return ans;
	}
	
```
