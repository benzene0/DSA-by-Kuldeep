
# Find all possible palindromic partitions of a String

Given an array arr[] of length n. Find all possible unique permutations of the array.
### Input:

n = 3

arr[] = {1, 2, 1}

### Output:

1 1 2

1 2 1

2 1 1


## code

```javascript
//Initial Template for C++

#include <bits/stdc++.h>
using namespace std;


 // } Driver Code Ends
//User function Template for C++

class Solution {
  public:
    vector<vector<int>> ans;
    vector<int> one;
    unordered_map<int,int> m;
    int N;
    void rec(int i)
    {
        if(i==N)
        {
            ans.push_back(one);
            return;
        }
        for(auto x : m)
        {
            if(x.second)
            {
                one.push_back(x.first);
                m[x.first]--;
                rec(i+1);
                m[x.first]++;
                one.pop_back();
                
            }
        }
    }
    
    vector<vector<int>> uniquePerms(vector<int> arr ,int n) {
        ans.clear();
        one.clear();
        N=arr.size();
        for(auto x:arr)
            m[x]++;
        rec(0);
        sort(ans.begin(),ans.end());
        return ans;
    }
};

// { Driver Code Starts.

int main() {
    int t;
    cin >> t;
    while (t--) {
        int n;
        
        cin>>n;
        vector<int> arr(n);
        
        for(int i=0 ; i<n ; i++)
            cin>>arr[i];

        Solution ob;
        vector<vector<int>> res = ob.uniquePerms(arr,n);
        for(int i=0; i<res.size(); i++)
        {
            for(int j=0; j<n; j++)
            {
                cout<<res[i][j]<<" ";
            }
            cout<<"\n";
        }
    }
    return 0;
}  // } Driver Code Ends
```

  
