
# 139. Word Break

Given a string s and a dictionary of strings wordDict, return true if s can be segmented into a space-separated sequence of one or more dictionary words.
### Input:
s = "leetcode", wordDict = ["leet","code"]
### Output:
true

## code

```javascript
class Solution {
public:
    bool check(string s,string t,int i ){
        for(int j = 0;j<t.size();j++){
            if(s[i+j] != t[j]) return false;
        }
        
        return true;
    }
    bool wordBreak(string s, vector<string>& wordDict) {
        int n = s.size();
        vector<bool> dp(n+1,false);
        dp[n] = true;
        
        for(int i = n-1;i>=0;i--){
            for(auto w : wordDict){
                if(i+w.size() <=n && check(s,w,i)) dp[i] = dp[i+w.size()];
                
                if(dp[i]) break;
            }
        }
        return dp[0];
    }
};
```

  
