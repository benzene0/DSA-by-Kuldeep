
# Heap

This code is implemented on Max Heap.


## Usage/Examples

```javascript
#include<bits/stdc++.h>
using namespace std;

void Max_Heapify(vector<int>& arr,int i){
    int left,right,largest;
    left = 2*i+1;
    right = 2*i+2;
    largest = i;
    
    if(left< arr.size() && arr[left] > arr[largest]) largest = left;
    if(right< arr.size() && arr[right] > arr[largest]) largest = right;
    
    if(largest != i){
        swap(arr[i],arr[largest]);
        Max_Heapify(arr,largest);
    }
}

void Build_MaxHeap(vector<int>& arr){
    for(int i = arr.size()/2 - 1;i>=0;i--){
        Max_Heapify(arr,i);
    }
}

int Pop_max(vector<int>& arr){
    if(arr.size() == 0) return -1;
    int mx = arr[0];
    arr[0] = arr[arr.size()-1];
    arr.pop_back();
    Max_Heapify(arr,0);
    return mx;
}

void push_Maxh(vector<int>& arr,int p){
    arr.push_back(p);
    int x = arr.size()-1;
    int parent = x%2 == 0 ? x/2 -1 : (x+1)/2 -1;
    while(x> 0 and arr[parent]<arr[x]){
        swap(arr[parent],arr[x]);
        x = parent;
        parent = x%2 == 0 ? x/2 -1 : (x+1)/2 -1;
    }
}

int main(){
    int n; cin>>n;
    vector<int> arr;
    for(int i = 0;i<n;i++){
        int temp ;
        cin>>temp;
        arr.push_back(temp);
    }
    Build_MaxHeap(arr);
    cout<<Pop_max(arr)<<"\n";
    push_Maxh(arr,87);
    for(auto x : arr) cout<<x<<" ";
    return 0;
}
```

  
