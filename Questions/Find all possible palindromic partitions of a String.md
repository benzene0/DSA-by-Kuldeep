
# Find all possible palindromic partitions of a String

Given a String S, Find all possible Palindromic partitions of the given String.

### Input:

S = "geeks"

### Output:

g e e k s

g ee k s


## code

```javascript
#include <bits/stdc++.h>
using namespace std;

 // } Driver Code Ends
//User function Template for C++

class Solution {
  public:
    vector<vector<string>> ans;
    vector<string> backtrack;
    
    bool ispali(string s,int i ,int j)
    {
        while(i<j){
            if(s[i] != s[j]) return false;
            i++;
            j--;
        }
        return true;
    }
    
    void dfs(int i,string s)
    {
        if(i == s.size()){
            ans.push_back(backtrack);
            return ;
        }
        string temp;
        for(int k = i ;k<s.size();k++)
        {
            temp += s[k];
            if(ispali(s,i,k)){
                backtrack.push_back(temp);
                dfs(k+1,s);
                backtrack.pop_back();
            }
        }
    }
    
    vector<vector<string>> allPalindromicPerms(string S) {
        dfs(0,S);
        return ans;
    }
};

// { Driver Code Starts.
int main() {
    int t;
    cin >> t;
    while (t--) {
        string S;
        
        cin>>S;

        Solution ob;
        vector<vector<string>> ptr = ob.allPalindromicPerms(S);
        
        for(int i=0; i<ptr.size(); i++)
        {
            for(int j=0; j<ptr[i].size(); j++)
            {
                cout<<ptr[i][j]<<" ";
            }
            cout<<endl;
        }
    }
    return 0;
}  // } Driver Code Ends
```

  
