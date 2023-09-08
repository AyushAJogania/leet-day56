# leet-day56

# Pascal's Triangle

## Problem Description

Given an integer `numRows`, return the first `numRows` of Pascal's triangle.

In Pascal's triangle, each number is the sum of the two numbers directly above it. 

**Example 1:**

Input: `numRows = 5`
Output:
```
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```

**Example 2:**

Input: `numRows = 1`
Output:
```
[
 [1]
]
```

**Constraints:**

- `1 <= numRows <= 30`

## Approach

We can generate Pascal's Triangle iteratively. The idea is to start with the first row, which contains just one element (1). Then, we build each subsequent row based on the previous row. To construct each row, we start with an array of ones, and then calculate the values between the first and last ones based on the values in the previous row. This can be done using a nested loop.

1. Initialize an empty vector `triangle` to store the resulting triangle.
2. Iterate from `i = 0` to `numRows - 1`, where `i` represents the current row.
    - Create an empty vector `row` for the current row.
    - Initialize `row` with `i + 1` elements, all set to 1. This represents the ones at the beginning and end of the row.
    - Iterate from `j = 1` to `i - 1`, where `j` represents the column index within the current row.
        - Calculate the value at `row[j]` as the sum of `triangle[i - 1][j - 1]` and `triangle[i - 1][j]`. These values are from the previous row.
    - Append the `row` to the `triangle`.
3. After the loop completes, `triangle` contains the Pascal's Triangle up to `numRows`.

## Complexity Analysis

The time complexity for this approach is O(numRows^2) because we iterate through each row, and for each row, we iterate through its columns. The space complexity is O(numRows^2) as well because we store the entire triangle.

## Implementation

You can find the C++ implementation of this approach in the provided source code (`main.cpp`). To use it, follow these steps:

1. Include the necessary headers:
   ```cpp
   #include <iostream>
   #include <vector>
   ```

2. Define the `Solution` class with the `generate` method, as shown in the code.

3. In the `main` function, create an instance of the `Solution` class, call the `generate` method with the desired `numRows`, and print the result.

Example usage:

```cpp
int main() {
    Solution solution;
    int numRows = 5;
    std::vector<std::vector<int>> result = solution.generate(numRows);

    // Print the result
    for (const std::vector<int>& row : result) {
        for (int num : row) {
            std::cout << num << " ";
        }
        std::cout << std::endl;
    }

    return 0;
}
```

This code generates Pascal's Triangle for `numRows = 5` and prints the result to the console. You can change the value of `numRows` as needed.
