# Dynamic Programming in C++

## Overview
Dynamic programming (DP) optimizes recursive solutions by breaking problems into overlapping subproblems and storing intermediate results. DP is effective when a problem exhibits optimal substructure and repeated subproblems.

## Approaches
- **Top-Down (Memoization)**: recursively compute results and cache them to avoid recomputation.
- **Bottom-Up (Tabulation)**: iteratively build a table from base cases up to the target solution.

## Example: Fibonacci Numbers (Top-Down and Bottom-Up)
```cpp
#include <iostream>
#include <unordered_map>
#include <vector>

long long fibMemo(int n, std::unordered_map<int, long long>& memo) {
    if (n <= 1) return n;
    if (memo.count(n)) return memo[n];
    return memo[n] = fibMemo(n - 1, memo) + fibMemo(n - 2, memo);
}

long long fibTab(int n) {
    if (n <= 1) return n;
    std::vector<long long> dp(n + 1);
    dp[0] = 0;
    dp[1] = 1;
    for (int i = 2; i <= n; ++i) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }
    return dp[n];
}

int main() {
    std::unordered_map<int, long long> memo;
    std::cout << "fibMemo(10) = " << fibMemo(10, memo) << '\n';
    std::cout << "fibTab(10) = " << fibTab(10) << '\n';
    return 0;
}
```

### Complexity
- Time: O(n)
- Space: O(n) for memoization or tabulation tables (can be reduced to O(1) for Fibonacci with optimized tabulation)
