# Arrays in C++

## Overview
Arrays store a fixed-size sequence of elements of the same type in contiguous memory. They provide O(1) access time when indexing, but resizing requires creating a new array. Arrays are useful when the number of elements is known in advance and random access is needed.

## Common Operations
- Access: `arr[i]` retrieves the ith element in O(1) time.
- Update: `arr[i] = value` updates an element in O(1) time.
- Traversal: iterate with a loop to process each element.
- Search: linear scan is O(n); sorted arrays enable binary search in O(log n).

## Implementation Notes
- Declare with fixed size: `int arr[5];`
- Initialize using brace list: `int arr[5] = {1, 2, 3, 4, 5};`
- Use `std::array` for safer bounds-checked operations via `at()`.

## Example: Maximum Subarray Sum (Kadane's Algorithm)
```cpp
#include <iostream>
#include <vector>
#include <limits>

int maxSubArray(const std::vector<int>& nums) {
    int best = std::numeric_limits<int>::min();
    int current = 0;
    for (int x : nums) {
        current = std::max(x, current + x);
        best = std::max(best, current);
    }
    return best;
}

int main() {
    std::vector<int> nums = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
    std::cout << "Maximum subarray sum: " << maxSubArray(nums) << '\n';
    return 0;
}
```

### Complexity
- Time: O(n)
- Space: O(1) auxiliary
