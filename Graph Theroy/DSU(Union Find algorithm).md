
# Disjoint Set Union (Union Find) algorithm

* With path compression **Time Complexity O(alpha(n))**  close to constent Time
* without path compression **Time Complexity O(logn)** 
* **space Complexity O(n)**

## code

```javascript
class UnionFind
{
    vector<int> parent;
    vector<int> rank;
public:
    int groupCount;
    UnionFind(int n):groupCount(n){
        parent = vector<int>(n,-1);
        rank = vector<int>(n,0);
    }
    
    int find(int n){
        if(parent[n] == -1) return n;
        parent[n] = find(parent[n]);
        return parent[n];
    }
    void unify(int a,int b){
        int parenta = find(a);
        int parentb = find(b);
        if(parenta == parentb) return ;
        if(rank[parenta] < rank[parentb]) parent[parenta] = parentb;
        else if(rank[parenta] > rank[parentb]) parent[parentb] = parenta;
        else{
            parent[parenta] = parentb;
            rank[parentb]++;
        }
        groupCount--;
    }
    
};
```

  
