
# Combination Sum

Given an array of integers and a sum B, find all unique combinations in the array where the sum is equal to B. The same number may be chosen from the array any number of times to make B.

Note:\
        1. All numbers will be positive integers.\
        2. Elements in a combination (a1, a2, …, ak) must be in non-descending order. (ie, a1 ≤ a2 ≤ … ≤ ak).\
        3. The combinations themselves must be sorted in ascending order.
### Input:

N = 4 \
arr[] = {7,2,6,5}\
B = 16

### Output:

(2 2 2 2 2 2 2 2)\
(2 2 2 2 2 6)\
(2 2 2 5 5)\
(2 2 5 7)\
(2 2 6 6)\
(2 7 7)\
(5 5 6)

## code

```javascript
//Initial Template for C++
class Solution {
  public:
    //Function to return a list of indexes denoting the required 
    //combinations whose sum is equal to given number.
    vector<vector<int>> ans;
    
    void dfs(int sum,int B,vector<int> tx,vector<int>& A,int k){
        if(sum == B){
            ans.push_back(tx);
            return;
        }
        if(sum>B) return;
        
        for(int i = k;i<A.size();i++){
            tx.push_back(A[i]);
            dfs(sum+A[i],B,tx,A,i);
            tx.pop_back();
        }
    }
    
    vector<vector<int> > combinationSum(vector<int> &A, int B) {
        // Your code herje
        ans.clear();
        sort(A.begin(),A.end());
        A.erase(unique(A.begin(),A.end()),A.end());
        vector<int> tx;
        dfs(0,B,tx,A,0);
        return ans;
    }
    
};
```

  
