# Segment Tree

* good for more updates
* Update timecomplexity : O(logn)
* create Segment tree : O(n)
* query timecomplexity : O(logn)
* size of Segment tree : 4*N


## code

```javascript
class NumArray {
    int sizeofST,n;
    vector<int> st;
    vector<int> nums;
public:
    NumArray(vector<int>& nums) {
        n = nums.size();
        this->nums = nums;
        sizeofST = 4*n;
        st = vector<int>(sizeofST,0);
        build_st(0,n-1,0);
    }
    
    void update(int index, int val) {
        int dx = val - nums[index];
        nums[index] = val;
        update_st(0,n-1,0,index,dx);
    }
    
    int sumRange(int left, int right) {
        return query(0,n-1,0,left,right);
    }
    
    void build_st(int start,int end,int treeNode){
        if(start == end) {
            st[treeNode] = nums[start];
            return;
        }
        int mid = (start + end) / 2;
        build_st(start, mid, 2*treeNode+1);
        build_st(mid + 1, end, 2*treeNode + 2);
        
        st[treeNode] = st[2*treeNode+1] + st[2*treeNode + 2];
    }
    int query(int start,int end,int treeNode,int left,int right){
        if(start>right || end<left) return 0;
        if(start>=left && end<=right) return st[treeNode];
        
        int mid = (start+end)/2;
        return query(start,mid,2*treeNode+1,left,right)+
            query(mid+1,end,2*treeNode+2,left,right);
    }
    void update_st(int start,int end,int treeNode,int idx,int dx){
        if(start>idx || end<idx) return;
        st[treeNode] += dx;
        if(start!=end){
            int mid = (start+end)/2;
            update_st(start,mid,2*treeNode+1,idx,dx);
            update_st(mid+1,end,2*treeNode+2,idx,dx);
        }
    }
};
```
