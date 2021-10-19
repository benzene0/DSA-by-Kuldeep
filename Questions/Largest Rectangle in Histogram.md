
# Largest Rectangle in Histogram

Given an array of integers heights representing the histogram's bar height where the width of each bar is 1, return the area of the largest rectangle in the histogram.
### Input:
heights = [2,1,5,6,2,3]
### Output:
10
#### video soluction :: https://www.youtube.com/watch?v=zx5Sw9130L0&ab_channel=NeetCode
## code

```javascript
class Solution {
public:
    int largestRectangleArea(vector<int>& heights) {
        pair<int,int> P;
        stack<pair<int,int>> S;// <idx h>
        int ans = 0;
        for(int idx = 0;idx < heights.size();idx++)
        {
            int h = heights[idx];
            int cidx = idx;
            while(!S.empty() && S.top().second > h)
            {
                P = S.top();
                S.pop();
                ans = max(ans,P.second * (idx - P.first));
                cidx = P.first;
            }
            P = make_pair(cidx,h);
            S.push(P);
        }
        int id = heights.size();
        while(!S.empty())
        {
            P = S.top();
            S.pop();
            ans = max(ans,P.second * (id - P.first));
        }
        return ans;
    }
};
```

  
