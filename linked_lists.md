# Linked Lists in C++

## Overview
A linked list is a linear data structure where elements (nodes) store a value and a pointer to the next node. Unlike arrays, linked lists do not require contiguous memory and can grow or shrink dynamically. However, random access is O(n) because traversal from the head is required.

## Types of Linked Lists
- **Singly Linked List**: each node points to the next node.
- **Doubly Linked List**: nodes have pointers to both next and previous nodes, enabling backward traversal.
- **Circular Linked List**: the last node points back to the head, forming a loop.

## Common Operations and Complexities
| Operation | Singly Linked | Doubly Linked |
|-----------|---------------|---------------|
| Insert at head | O(1) | O(1) |
| Insert at tail | O(n) without tail pointer, O(1) with tail | O(1) if tail tracked |
| Delete head | O(1) | O(1) |
| Delete by value | O(n) | O(n) |
| Search | O(n) | O(n) |

## Example: Reverse a Singly Linked List
```cpp
#include <iostream>

struct Node {
    int data;
    Node* next;
    explicit Node(int value) : data(value), next(nullptr) {}
};

Node* reverseList(Node* head) {
    Node* prev = nullptr;
    Node* curr = head;
    while (curr) {
        Node* nextNode = curr->next;
        curr->next = prev;
        prev = curr;
        curr = nextNode;
    }
    return prev;
}

void printList(Node* head) {
    while (head) {
        std::cout << head->data << ' ';
        head = head->next;
    }
    std::cout << '\n';
}

int main() {
    Node* head = new Node(1);
    head->next = new Node(2);
    head->next->next = new Node(3);

    std::cout << "Original: ";
    printList(head);

    head = reverseList(head);

    std::cout << "Reversed: ";
    printList(head);

    while (head) {
        Node* temp = head;
        head = head->next;
        delete temp;
    }
    return 0;
}
```

### Complexity
- Time: O(n)
- Space: O(1) auxiliary
