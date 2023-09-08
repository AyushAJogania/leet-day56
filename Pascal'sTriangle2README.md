# leet-day56

# Pascal's Triangle Row Generator

This C++ program generates the `rowIndex`-th row of Pascal's Triangle using an optimized approach with O(rowIndex) space complexity. Pascal's Triangle is a mathematical structure where each number is the sum of the two numbers directly above it.

## Prerequisites

- C++ compiler (supporting C++11 or later)

## How to Use

1. Open a C++ development environment or editor (e.g., Visual Studio Code, g++, or any C++ IDE).
2. Copy the provided C++ code into a C++ source file (e.g., `pascals_triangle_row.cpp`).

```cpp
#include <iostream>
#include <vector>

class Solution {
public:
    std::vector<int> getRow(int rowIndex) {
        std::vector<int> row(rowIndex + 1, 0);  // Initialize a vector of size rowIndex+1 with 0s.
        row[0] = 1;  // Set the first element to 1 (the starting point of each row).

        for (int i = 1; i <= rowIndex; ++i) {
            for (int j = i; j >= 1; --j) {
                row[j] += row[j - 1];  // Calculate each element in the current row.
            }
        }

        return row;
    }
};


```

3. Compile the code using your C++ compiler:

```bash
g++ pascals_triangle_row.cpp -o pascals_triangle_row
```

4. Run the executable:

```bash
./pascals_triangle_row
```

5. The program will prompt you for the desired `rowIndex`. Enter the value and press Enter.

6. The program will display the `rowIndex`-th row of Pascal's Triangle in the console.

## Explanation

The C++ code defines the `Solution` class with a `getRow` method that calculates the `rowIndex`-th row of Pascal's Triangle efficiently using minimal space. The algorithm updates the same vector in place for each row.

## Example

Suppose you want to generate the 3rd row of Pascal's Triangle (`rowIndex = 3`). The program will output:

```
1 3 3 1
```

## Constraints

- The code supports generating rows with `rowIndex` in the range [0, 33].
- Each row contains integers within the range [-10^4, 10^4].
