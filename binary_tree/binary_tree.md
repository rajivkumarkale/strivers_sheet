# **Binary Tree**
---

## 1. Inorder Traveral
### 1.1 Iterative Solution : 
```cpp
// Iterative solution :: Inorder : LNR
class Solution {
public:
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> inTree;
        stack<TreeNode*> stk;
        TreeNode* curr = root;

        while(curr || !stk.empty()){
            while(curr){
                stk.push(curr);
                curr = curr->left;
            }
            curr = stk.top(); stk.pop();
            inTree.push_back(curr->val);
            curr = curr->right;
        }
        return inTree;
    }
};
```

### 1.2 Recursive solution :
```cpp
//Recursive : Inorder :: LNR
class Solution {
private:
    void inorder(TreeNode *root, vector<int> &inTree){
        if(!root) return;
        inorder(root->left, inTree);
        inTree.push_back(root->val);
        inorder(root->right, inTree);
    }
public:
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> inTree;
        inorder(root, inTree);
        return inTree;
    }
};
```


## 2. PreOrder Traversal
### 2.1 Iterative solution :
```cpp
// Iterative: pre-order :: NLR
class Solution {
public:
    vector<int> preorderTraversal(TreeNode* root) {
        vector<int> preTree;
        stack<TreeNode*> stk; stk.push(root);
        TreeNode *curr;

        while(!stk.empty()){
            curr = stk.top(); stk.pop();
            if(curr->right) stk.push(curr->right);
            if(curr->left) stk.push(curr->left);
        }
        return preTree;
    }
};
```

### 2.2 Recursive Solution :
```cpp
//Recursive:: Preorder : NLR
class Solution {
private:
    void preorder(TreeNode* root, vector<int> &preTree){
        if(!root) return;
        preTree.push_back(root->val);
        preorder(root->left, preTree);
        preorder(root->right, preTree);
    }
public:
    vector<int> preorderTraversal(TreeNode* root) {
        vector<int> preTree;
        preorder(root, preTree);
        return preTree;
    }
};
```
