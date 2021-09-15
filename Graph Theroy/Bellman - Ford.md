
# Bellman - Ford

- Dijkstra and Bellman - Ford **does not** find shortest path for graph with -ve edge weight cycle.
- But Bellman - Ford can detect - ve edge weight cycle.




## code:

```javascript
void b_f(int n, vector<vector<int>>edges){
	    // edges vector of vector{start,end,weight}
      
	    int INF = 10e6;
	    vector<int> coast(n,INF);
	    coast[0] = 0;
	    bool same = true;
	    for(int i = 1;i<n;i++){
	        same = true;
	        for(auto ed :edges){
	                if(coast[ed[0]] + ed[2] < coast[ed[1]]){
	                    coast[ed[1]] = coast[ed[0]] + ed[2];
	                    same = false;
	                }
	            }
	        
	        if(same) break;
	    }
	}
```
- Time complexity **O(VE)**
- Space complexity **O(V)**
  
## Negitive edge weight cycle detection

- If we iterate **n**th time and coast is changed then  -ve edge weight cycle is present else not.
- n is no of vartices.

  
