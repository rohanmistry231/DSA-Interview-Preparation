# Core Algorithms

This section covers essential algorithms commonly tested in coding interviews. Each algorithm includes a definition, explanation, Python implementation, time and space complexity, and common interview problems to help you prepare effectively.

---

## 1. Searching

### Definition
Searching involves finding a specific element in a data structure, such as an array or list.

### Types
- **Linear Search**: Sequentially checks each element until the target is found or the list is exhausted.
- **Binary Search**: Efficiently searches a sorted array by repeatedly dividing the search interval in half.

### Binary Search Example
```python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = left + (right - left) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1

# Example usage
arr = [1, 2, 3, 4, 5]
print(binary_search(arr, 3))  # Output: 2
```

### Time and Space Complexity
| Algorithm       | Time Complexity | Space Complexity |
|-----------------|-----------------|------------------|
| Linear Search   | O(n)            | O(1)             |
| Binary Search   | O(log n)        | O(1)             |

### Common Interview Problems
- **Search in Rotated Sorted Array**: Find an element in a rotated sorted array ([LeetCode](https://leetcode.com/problems/search-in-rotated-sorted-array/)).
- **Find First and Last Position**: Find the range of a target in a sorted array.
- **Search a 2D Matrix**: Search in a sorted 2D matrix.

---

## 2. Sorting

### Definition
Sorting arranges elements in a specific order, typically ascending or descending, to facilitate searching or other operations.

### Common Sorting Algorithms
- **Bubble Sort**: Repeatedly swaps adjacent elements if they are in the wrong order.
- **Selection Sort**: Repeatedly selects the minimum element from the unsorted portion.
- **Insertion Sort**: Builds the sorted array one element at a time.
- **Merge Sort**: Divides the array, sorts halves, and merges them.
- **Quick Sort**: Partitions the array around a pivot and sorts subarrays.

### Merge Sort Example
```python
def merge_sort(arr):
    if len(arr) > 1:
        mid = len(arr) // 2
        left_half = arr[:mid]
        right_half = arr[mid:]
        merge_sort(left_half)
        merge_sort(right_half)
        i = j = k = 0
        while i < len(left_half) and j < len(right_half):
            if left_half[i] < right_half[j]:
                arr[k] = left_half[i]
                i += 1
            else:
                arr[k] = right_half[j]
                j += 1
            k += 1
        while i < len(left_half):
            arr[k] = left_half[i]
            i += 1
            k += 1
        while j < len(right_half):
            arr[k] = right_half[j]
            j += 1
            k += 1

# Example usage
arr = [64, 34, 25, 12, 22, 11, 90]
merge_sort(arr)
print(arr)  # Output: [11, 12, 22, 25, 34, 64, 90]
```

### Time and Space Complexity
| Algorithm       | Time Complexity (Average) | Time Complexity (Worst) | Space Complexity |
|-----------------|--------------------------|-------------------------|------------------|
| Bubble Sort     | O(n^2)                   | O(n^2)                  | O(1)             |
| Selection Sort  | O(n^2)                   | O(n^2)                  | O(1)             |
| Insertion Sort  | O(n^2)                   | O(n^2)                  | O(1)             |
| Merge Sort      | O(n log n)               | O(n log n)              | O(n)             |
| Quick Sort      | O(n log n)               | O(n^2)                  | O(log n)         |

### Common Interview Problems
- **Sort Colors**: Sort an array of 0s, 1s, and 2s ([LeetCode](https://leetcode.com/problems/sort-colors/)).
- **Kth Largest Element**: Find the kth largest element in an array.
- **Merge Intervals**: Merge overlapping intervals.

---

## 3. Recursion

### Definition
Recursion is a technique where a function calls itself to solve smaller instances of the same problem, relying on a base case to terminate.

### Key Concepts
- **Base Case**: The condition that stops the recursion.
- **Recursive Case**: The part where the function calls itself with a smaller input.

### Example: Factorial
```python
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n - 1)

# Example usage
print(factorial(5))  # Output: 120
```

### Time and Space Complexity
- Time Complexity: O(n) (n recursive calls)
- Space Complexity: O(n) (due to call stack)

### Common Interview Problems
- **Fibonacci Sequence**: Calculate the nth Fibonacci number ([LeetCode](https://leetcode.com/problems/fibonacci-number/)).
- **Permutations**: Generate all permutations of a string.
- **Subsets**: Generate all subsets of a set.

---

## 4. Dynamic Programming

### Definition
Dynamic Programming (DP) solves complex problems by breaking them into overlapping subproblems, solving each only once, and storing results to avoid redundant computations.

### Key Concepts
- **Memoization**: Top-down approach storing subproblem results.
- **Tabulation**: Bottom-up approach building solutions iteratively.

### Example: Fibonacci with DP
```python
def fibonacci_dp(n, dp):
    if n <= 1:
        return n
    if dp[n] != -1:
        return dp[n]
    dp[n] = fibonacci_dp(n - 1, dp) + fibonacci_dp(n - 2, dp)
    return dp[n]

# Example usage
n = 5
dp = [-1] * (n + 1)
print(fibonacci_dp(n, dp))  # 🙂 Output: 5
```

### Time and Space Complexity
- Time Complexity: O(n) (each subproblem solved once)
- Space Complexity: O(n) (for memoization table)

### Common Interview Problems
- **Climbing Stairs**: Find ways to climb n stairs with 1 or 2 steps ([LeetCode](https://leetcode.com/problems/climbing-stairs/)).
- **Coin Change**: Find the fewest coins to make a given amount.
- **Longest Increasing Subsequence**: Find the longest strictly increasing subsequence.

---

## 5. Graph Algorithms

### Definition
Graph algorithms solve problems on graphs, such as finding paths, detecting cycles, or computing shortest paths.

### Key Algorithms
- **Depth-First Search (DFS)**: Explores as far as possible along each branch.
- **Breadth-First Search (BFS)**: Explores all neighbors before moving deeper.
- **Dijkstra’s Algorithm**: Finds shortest paths in weighted graphs.
- **Bellman-Ford Algorithm**: Handles negative weights for shortest paths.
- **Kruskal’s Algorithm**: Finds minimum spanning tree using union-find.
- **Prim’s Algorithm**: Finds minimum spanning tree using a priority queue.

### Example: BFS
```python
from collections import deque

def bfs(graph, start):
    visited = set()
    queue = deque([start])
    visited.add(start)
    while queue:
        vertex = queue.popleft()
        print(vertex, end=' ')
        for neighbor in graph[vertex]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)

# Example usage
graph = {
    'A': ['B', 'C'],
    'B': ['D', 'E'],
    'C': ['F'],
    'D': [],
    'E': ['F'],
    'F': []
}
bfs(graph, 'A')  # Output: A B C D E F
```

### Time and Space Complexity
| Algorithm         | Time Complexity       | Space Complexity |
|-------------------|-----------------------|------------------|
| DFS               | O(V + E)             | O(V)             |
| BFS               | O(V + E)             | O(V)             |
| Dijkstra’s        | O((V + E) log V)     | O(V)             |
| Bellman-Ford      | O(V * E)             | O(V)             |
| Kruskal’s         | O(E log E)           | O(V)             |
| Prim’s            | O((V + E) log V)     | O(V)             |

### Common Interview Problems
- **Number of Islands**: Count islands in a 2D grid ([LeetCode](https://leetcode.com/problems/number-of-islands/)).
- **Clone Graph**: Create a deep copy of a graph.
- **Course Schedule II**: Order courses given prerequisites.

---

## 6. Bit Manipulation

### Definition
Bit manipulation uses bitwise operations to perform tasks efficiently on binary representations of numbers.

### Key Operations
- **AND (&)**: Returns 1 if both bits are 1.
- **OR (|)**: Returns 1 if at least one bit is 1.
- **XOR (^)**: Returns 1 if bits are different.
- **NOT (~)**: Inverts all bits.
- **Left Shift (<<)**: Shifts bits left.
- **Right Shift (>>)**: Shifts bits right.

### Example: Check Power of Two
```python
def is_power_of_two(n):
    return n > 0 and (n & (n - 1)) == 0

# Example usage
print(is_power_of_two(16))  # Output: True
print(is_power_of_two(10))  # Output: False
```

### Time and Space Complexity
- Time Complexity: O(1) for most operations
- Space Complexity: O(1)

### Common Interview Problems
- **Single Number**: Find the number appearing once in an array ([LeetCode](https://leetcode.com/problems/single-number/)).
- **Number of 1 Bits**: Count set bits in an integer.
- **Reverse Bits**: Reverse bits of a 32-bit integer.