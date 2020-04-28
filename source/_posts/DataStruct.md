---
title: DataStruct
date: 2020-03-08 10:26:26
tags: 
    -DataStruct
categories: 数据结构学习笔记
---
# 数据结构-二叉树
## 二叉树的4种基本遍历：
### 前序遍历
---
* 例子
```mermaid  
   1
    \
     2
    /
   3 
   [1,2,3]
```
* 代码
```
class Solution {
    vector<int> vec;
    void test(TreeNode* root)
    {
        if (root != NULL)
        { 
            vec.push_back(root->val);
            preorderTraversal(root->left);
            preorderTraversal(root->right);
        }
    }
public:
    vector<int> preorderTraversal(TreeNode* root) {
        test(root);
        return vec;       
    }
};
```
---
前序遍历首先访问根节点，然后遍历左子树，最后遍历右子树。
### 中序遍历
---
* 例子
 ```mermaid  
   1
    \
     2
    /
   3 
   [1,3,2]
```
* 代码

```
class Solution {
public:
    vector<int> vec;
    void test(TreeNode* root)
    {
        if (root != NULL)
        { 
            inorderTraversal(root->left);
            vec.push_back(root->val);
            inorderTraversal(root->right);
        }
    }
    vector<int> inorderTraversal(TreeNode* root) {
        test(root);
        return vec;
    }
};
```
---
中序遍历是先遍历左子树，然后访问根节点，然后遍历右子树。
### 后序遍历
---
* 例子
```mermaid  
   1
    \
     2
    /
   3 
   [3,2,1]
```
* 代码
```
class Solution {
public:
    vector<vector<int>> vec;
    queue<TreeNode*> q;
    
    TreeNode* temp;

    void test(TreeNode* root)
    {
        while(!q.empty())   
        {
            vector<int> tempvec;
            queue<TreeNode*> temp_q;
            while(!q.empty())
            {
                temp = q.front();
                tempvec.push_back(temp->val);
                if(temp->left!=NULL)
                    temp_q.push(temp->left);
                if(temp->right!=NULL)
                    temp_q.push(temp->right);
                q.pop();
            }
            vec.push_back(tempvec);
            q = temp_q; 
        }
    }
    vector<vector<int>> levelOrder(TreeNode* root) {
        if(!root)
            return vec;
        temp = root;
        q.push(temp);
        test(root);
        return vec;
    }
};
```
---
后序遍历是先遍历左子树，然后遍历右子树，最后访问树的根节点。
### 层次遍历
```mermaid  
   1
  / \
 2   3
    /
   4 
   [[1],[2,3],[4]]
```
即逐层地，从左到右访问所有节点

每天都坚持进步一点点，当机会来临的时候才能抓住！