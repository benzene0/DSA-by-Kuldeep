
# Sum of k smallest elements in BST

Given a Binary Search Tree.Find sum of all elements smaller than and equal to Kth smallest element.

### Input
          20
        /    \
       8     22
     /    \
    4     12
         /    \
        10    14   , K=3

### Output
22

Sum of 3 smallest elements are: 
4 + 8 + 10 = 22
## Usage/Examples

```javascript
void fx(Node* root,int &k,int &ans)
{
    if(k<0) return;
    if(root == NULL) return;
    fx(root->left,k,ans);
    if(k>0){
        ans += root->data;
        k--;
    }
    fx(root->right,k,ans);
}
int sum(Node* root, int k) 
{ 
  
    int ans = 0;
    int n = k;
    fx(root,n,ans);
    return ans;
    
} 
```

  
