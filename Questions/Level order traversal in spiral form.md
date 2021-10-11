
# Level order traversal in spiral form

Complete the function to find spiral order traversal of a tree.

### Input:

           10
         /     \
        20     30
      /    \
    40     60

### Output:

10\
20 30\
60 40

## code

```javascript
vector<int> findSpiral(Node *root)
{
    stack<Node*> t1;
    stack<Node*> t2;
    
    vector<int> ans;
    if(root == NULL) return ans;
    t1.push(root);
    while(!t1.empty() || !t2.empty()){
        while(!t1.empty()){
            Node * temp = t1.top();
            t1.pop();
            ans.push_back(temp->data);
            if(temp->right != NULL) t2.push(temp->right);
            if(temp->left != NULL) t2.push(temp->left);
        }
        while(!t2.empty()){
            Node * temp = t2.top();
            t2.pop();
            ans.push_back(temp->data);
            if(temp->left != NULL) t1.push(temp->left);
            if(temp->right != NULL) t1.push(temp->right);
            
        }
    }
    return ans;
}
```

  
