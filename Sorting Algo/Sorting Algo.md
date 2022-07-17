
## Sorting Algorithms

### Comparison
                Time Complexity
                Best    Avg.    Worst   Aux. space      online  Stable  Implace
    Bubble      n       n^2     n^2     1               No      Yes     Yes
    Selection   n^2     n^2     n^2     1               No      No      Yes
    Insertion   n       n^2     n^2     1               Yes     Yes     Yes
    Merge       nlogn   nlogn   nlogn   n               No      Yes     No
    Quick       nlogn   nlogn   n^2     1               No      No      Yes
    Heap        nlogn   nlogn   nlogn   1               No      No      Yes


```javascript
#include<iostream>
using namespace std;

void bubble_sort(vector<int> v){
    int n = v.size();
    for(int i = n-1;i>=0;i--){
        bool is_swap = false;
        for(int j = 0;j<i;j++){
            if(v[j] > v[j+1]) {
                swap(v[j],v[j+1]);
                is_swap = true;
            }
        }
        if(!is_swap) break;
    }
    for(int i = 0;i<n;i++) cout<<v[i]<<" ";
}
void selection_sort(vector<int> v){
    int n = v.size();
    for(int i = 0;i<n;i++){
        int smallest_idx = i;
        for(int j = i+1;j<n;j++){
            if(v[j]<v[smallest_idx]) smallest_idx = j;
        }
        swap(v[i],v[smallest_idx]);
    }
    for(int i = 0;i<n;i++) cout<<v[i]<<" ";
}
void insertion_sort(vector<int> v){
    int n = v.size();
    for(int i = 1;i<n;i++){
        int j = i-1;
        while(j>=0 && v[j] > v[j+1]){
            swap(v[j],v[j+1]);
            j--;
        }
    }
    for(int i = 0;i<n;i++) cout<<v[i]<<" ";
}
void merge(vector<int>& v,int l,int mid,int r){
    vector<int> temp;
    int i = l, j = mid+1;
    while(i<= mid && j <=r){
        if(v[i]<v[j]){
            temp.push_back(v[i]);
            i++;
        }
        else{
            temp.push_back(v[j]);
            j++;
        }
    }
    while(i<=mid){
        temp.push_back(v[i]);
        i++;
    }
    while(j<=r){
        temp.push_back(v[j]);
        j++;
    }
    for(i = l;i<=r;i++) v[i] = temp[i-l];
}
void merge_s(vector<int>& v,int l,int r){
    if(l == r) return ;
    int mid = (l+r)/2;
    merge_s(v,l,mid);
    merge_s(v,mid+1,r);
    merge(v,l,mid,r);
}
void merge_sort(vector<int> v){
    int n = v.size();
    merge_s(v,0,n-1);
    for(int i = 0;i<n;i++) cout<<v[i]<<" ";
}
int quick_select(vector<int>& v,int l,int r){
    int pivot = v[r], p = l;
    for(int i = l;i<r;i++){
        if(v[i]<=pivot){
            swap(v[i],v[p]);
            p++;
        }
    }
    swap(v[p],v[r]);
    return p;
}
void quick_s(vector<int>& v,int l,int r){
    if(l>=r) return ;
    int partation = quick_select(v,l,r);
    quick_s(v,l,partation-1);
    quick_s(v,partation+1,r);
}
void quick_sort(vector<int> v){
    int n = v.size();
    quick_s(v,0,n-1);
    for(int i = 0;i<n;i++) cout<<v[i]<<" ";
}
void max_heap(vector<int>& v,int i,int n){
    int left = 2*i+1;
    int right = 2*i+2;
    int largest = i;
    if(left< n &&  v[left] > v[largest]) largest = left;
    if(right < n && v[right] > v[largest]) largest = right;
    
    if(largest != i){
        swap(v[i],v[largest]);
        max_heap(v,largest,n);
    }
}
void heap_sort(vector<int> v){
    int n = v.size();
    for(int i = (n/2 -1) ;i>=0;i--)
        max_heap(v,i,n);
    for(int i = n-1;i>0;i--){
        swap(v[0],v[i]);
        max_heap(v,0,i);
    }
    for(int i = 0;i<n;i++) cout<<v[i]<<" ";
}
int main() {
    vector<int> v = {1,5,2,3,7,3,2,9};
    bubble_sort(v); cout<<"\n";
    selection_sort(v); cout<<"\n";
    insertion_sort(v); cout<<"\n";
    merge_sort(v); cout<<"\n";
    quick_sort(v); cout<<"\n";
    heap_sort(v); cout<<"\n";
    return 0;
}
```

