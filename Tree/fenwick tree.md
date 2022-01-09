# Segment Tree

* good for more updates
* Update timecomplexity : O(logn)
* create Segment tree : O(nlong)
* query timecomplexity : O(logn)
* size of Segment tree : N

* **binary indexed tree start from index 1**
* **last set bit = i & (-i)**
* video link -> https://www.youtube.com/watch?v=uSFzHCZ4E-8&ab_channel=StableSort


## code

```javascript
class NumArray {
    vector<int> Tree;
    vector<int> nums;
    int n;
public:
    // binary indexed tree start from index 1
    // last set bit = i&(-i);
    NumArray(vector<int>& nums) {
        this->nums = nums;
        n = nums.size();
        Tree = vector<int>(n+1,0);
        for(int i = 0;i<n;i++) add(i+1,nums[i]);
    }
    
    void update(int index, int val) {
        int dx = val - nums[index];
        nums[index] += dx;
        add(index+1,dx);
    }
    
    int sumRange(int left, int right) {
        return sum(right+1) - sum(left);
    }
    
    int sum(int idx){
        int total = 0;
        while(idx>0){
            total += Tree[idx];
            idx -= (idx&-idx);
        }
        return total;
    }
    void add(int idx,int dx){
        while(idx<=n){
            Tree[idx]+= dx;
            idx += (idx&-idx);
        }
    }
};
```
