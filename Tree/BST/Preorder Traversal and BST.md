
# Preorder Traversal and BST 

Given an array arr[ ] of size N consisting of distinct integers, write a program that returns 1 if given array can represent preorder traversal of a possible BST, else returns 0.

### Input:
N = 3 \
arr = {2, 4, 3}
### Output: 
1
### Explaination: 
Given arr[] can represent
preorder traversal of following BST: 
          
          2 
            \
            4
          /
          3
## code

```javascript
    int canRepresentBST(int pre[], int N) {
        
        stack<int> s;
        
        int root = INT_MIN;
        
        for(int i = 0;i<N;i++)
        {
            if(pre[i]<root) return false;
            
            while(!s.empty() && s.top()<pre[i])
            {
                root = s.top();
                s.pop();
            }
            s.push(pre[i]);
        }
        
        return true;
    }
```

  
