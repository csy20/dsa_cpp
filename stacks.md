# Stacks in C++

## Overview
A stack is a Last-In, First-Out (LIFO) data structure that supports pushing elements to the top and popping elements from the top. It is useful for problems involving reverse order processing, recursion emulation, and expression evaluation.

## Interface
Key operations:
- `push(x)`: insert element `x` at the top.
- `pop()`: remove the top element.
- `top()`: access the top element without removing it.
- `empty()`: check whether the stack contains elements.

## Implementation Options
- `std::stack`: container adapter built over `std::vector` or `std::deque` by default.
- Custom implementation using linked lists or dynamic arrays for more control.

## Example: Balanced Parentheses Checker
```cpp
#include <iostream>
#include <stack>
#include <string>
#include <unordered_map>

bool isBalanced(const std::string& s) {
    std::unordered_map<char, char> match = {{')', '('}, {']', '['}, {'}', '{'}};
    std::stack<char> st;
    for (char c : s) {
        if (match.count(c)) {
            if (st.empty() || st.top() != match[c]) {
                return false;
            }
            st.pop();
        } else if (c == '(' || c == '[' || c == '{') {
            st.push(c);
        }
    }
    return st.empty();
}

int main() {
    std::string input = "([{}])";
    std::cout << input << (isBalanced(input) ? " is balanced" : " is not balanced") << '\n';
    return 0;
}
```

### Complexity
- Time: O(n)
- Space: O(n) in the worst case
