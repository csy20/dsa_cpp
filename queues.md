# Queues in C++

## Overview
A queue is a First-In, First-Out (FIFO) data structure that adds elements at the back and removes elements from the front. Queues are useful for scheduling, breadth-first search, and buffering.

## Interface
Core operations:
- `push(x)` / `enqueue(x)`: add element to the back.
- `pop()` / `dequeue()`: remove the front element.
- `front()`: access the front element without removing it.
- `empty()`: test whether the queue has elements.

## Implementation Options
- `std::queue`: container adapter typically backed by `std::deque`.
- `std::deque`: double-ended queue supporting push/pop at both ends in O(1).
- Circular array implementations for fixed-size queues.

## Example: Level Order Traversal of a Binary Tree
```cpp
#include <iostream>
#include <queue>
#include <vector>

struct TreeNode {
    int val;
    TreeNode* left;
    TreeNode* right;
    explicit TreeNode(int value) : val(value), left(nullptr), right(nullptr) {}
};

std::vector<int> levelOrder(TreeNode* root) {
    std::vector<int> result;
    if (!root) return result;

    std::queue<TreeNode*> q;
    q.push(root);
    while (!q.empty()) {
        TreeNode* node = q.front();
        q.pop();
        result.push_back(node->val);
        if (node->left) q.push(node->left);
        if (node->right) q.push(node->right);
    }
    return result;
}

int main() {
    TreeNode* root = new TreeNode(1);
    root->left = new TreeNode(2);
    root->right = new TreeNode(3);
    root->left->left = new TreeNode(4);
    root->right->right = new TreeNode(5);

    auto order = levelOrder(root);
    for (int value : order) {
        std::cout << value << ' ';
    }
    std::cout << '\n';

    // Cleanup omitted for brevity
    return 0;
}
```

### Complexity
- Time: O(n) for traversing n nodes
- Space: O(w) where w is maximum width of the tree
