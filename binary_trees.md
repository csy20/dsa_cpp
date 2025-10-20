# Binary Trees in C++

## Overview
A binary tree is a hierarchical structure where each node has up to two children: left and right. Binary trees are foundational for many specialized structures like binary search trees (BST), heaps, and segment trees.

## Properties
- A tree of height `h` has at most `2^{h+1} - 1` nodes.
- Perfect binary trees have all levels filled; complete binary trees fill levels left to right.
- Traversals include preorder (root-left-right), inorder (left-root-right), and postorder (left-right-root).

## Node Definition
```cpp
struct TreeNode {
    int val;
    TreeNode* left;
    TreeNode* right;
    explicit TreeNode(int value) : val(value), left(nullptr), right(nullptr) {}
};
```

## Example: Inorder Traversal
```cpp
#include <iostream>
#include <vector>

void inorder(TreeNode* root, std::vector<int>& result) {
    if (!root) return;
    inorder(root->left, result);
    result.push_back(root->val);
    inorder(root->right, result);
}

int main() {
    TreeNode* root = new TreeNode(2);
    root->left = new TreeNode(1);
    root->right = new TreeNode(3);

    std::vector<int> traversal;
    inorder(root, traversal);

    for (int value : traversal) {
        std::cout << value << ' ';
    }
    std::cout << '\n';

    // Free nodes
    delete root->left;
    delete root->right;
    delete root;
    return 0;
}
```

### Complexity
- Recursive traversal time: O(n)
- Space: O(h) for recursion stack (h = height of the tree)
