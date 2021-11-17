
# Kth Largest Element in an Array
Given an integer array nums and an integer k, return the kth largest element in the array.\
Note that it is the kth largest element in the sorted order, not the kth distinct element.

### Input: 
nums = [3,2,1,5,6,4], k = 2
### Output: 
5
## code

```javascript
    // Quick select Algorithm
    
    int quick_select(vector<int>& nums,int l,int r,int k){
        int pivat = nums[r],p = l;
        for(int i = l;i<r;i++){
            if(nums[i]<= pivat){
                swap(nums[i],nums[p]);
                p++;
            }
        }
        swap(nums[r],nums[p]);
        
        if(k == p) return nums[k];
        else if(k<p) return quick_select(nums,l,p-1,k);
        else{
            return quick_select(nums,p+1,r,k);
        }
    }
    int findKthLargest(vector<int>& nums, int k) {
        k = nums.size() - k;
        // using sorting 
        // sort(nums.begin(),nums.end());
        // return nums[k];
       return quick_select(nums,0,nums.size() -1,k);
        
    }
```

  
