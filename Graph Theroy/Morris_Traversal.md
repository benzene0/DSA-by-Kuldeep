
# Morris Traversal

Make a Threaded Binary Tree 

              1                                1
            /   \                            /  :   \
           2      3                         2    :    3
         /   \            ----->          / :  \  :
       4      5                          4..:   5  :
               \                                \   :
                6                                6..:


### Complexity

- Time Complexity  **O(N)**
- Space Complexity  **O(1)**


## Inorder Traversal

```javascript
vector<int> inorder;
Node *cur = root , *prv;
while(cur != NULL){
  if(cur->left == NULL){
    inorder.push_back(cur->data);
    cur = cur->right;
  }
  else{
    prv = cur->left;
    while(prv->right && prv->right != cur){
      prv = prv->right;
    }
    if(prv == NULL){
      prv->right = cur;
      cur = cur->left;
    }
    else{
      prv->right = NULL;
      inorder.push_back(cur->data);
      cur = cur->right;
    }
  }
}
return inorder;
```

## Preorder Traversal

```javascript
vector<int> preorder;
Node *cur = root , *prv;
while(cur != NULL){
  if(cur->left == NULL){
    preorder.push_back(cur->data);
    cur = cur->right;
  }
  else{
    prv = cur->left;
    while(prv->right && prv->right != cur){
      prv = prv->right;
    }
    if(prv == NULL){
      prv->right = cur;
      preorder.push_back(cur->data);
      cur = cur->left;
    }
    else{
      prv->right = NULL;
      cur = cur->right;
    }
  }
}
return preorder;
```


