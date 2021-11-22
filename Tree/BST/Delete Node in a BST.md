
# Delete Node in a BST
Given a root node reference of a BST and a key, delete the node with the given key in the BST. Return the root node reference (possibly updated) of the BST.

### Input: 
[5,3,6,2,4,null,7], key = 3
### Output: 
[5,4,6,2,null,null,7]  // preorder traversal
## code

```javascript
class Solution {
public:
    TreeNode* fx(TreeNode* root){
        if(root->left == NULL) return root;
        return fx(root->left);
    }
    TreeNode* deleteNode(TreeNode* root, int key) {
        if(root == nullptr) return nullptr;
        
        if(root->val <key) root->right = deleteNode(root->right,key);
        else if(root->val > key) root->left = deleteNode(root->left,key);
        else{
            if(root->left == nullptr && root->right == nullptr){
                delete root;
                return nullptr;
            }
            else if(root->left == nullptr){
                TreeNode* temp = root->right;
                delete root;
                return temp;
            }
            else if(root->right == nullptr){
                TreeNode* temp = root->left;
                delete root;
                return temp;
            }
            else{
                TreeNode* temp = fx(root->right);
                root->val = temp->val;
                root->right = deleteNode(root->right,temp->val);
            }
        }
        
        return root;
    }
};
```

  
