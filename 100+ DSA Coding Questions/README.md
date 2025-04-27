# 🚀 DSA Coding Interview Questions

<div align="center">
  <img src="https://img.shields.io/badge/DSA-Coding-3776AB?style=for-the-badge&logo=code&logoColor=white" alt="DSA Coding" />
  <img src="https://img.shields.io/badge/Interview-Prep-013243?style=for-the-badge&logo=book&logoColor=white" alt="Interview Prep" />
</div>
<p align="center">Your comprehensive guide to mastering coding DSA for technical interviews</p>

---

## 📖 Introduction

Welcome to the **DSA Coding Interview Questions** repository! This collection features **100 top Data Structures and Algorithms (DSA)** coding questions commonly asked in technical interviews, complete with Python solutions, explanations, and complexity analysis. These questions are categorized by topic, making it easy to focus on specific areas. Whether you're an AI/ML fresher or an experienced coder, this list will help you prepare effectively for your next interview.

**Source**: [Top 100 Data Structure and Algorithms DSA Interview Questions Topic-wise | GeeksforGeeks](https://www.geeksforgeeks.org/top-100-data-structure-and-algorithms-dsa-interview-questions-topic-wise/)

---

## Array (16 Questions)

### 1. Pair with Given Sum
**Problem**: Find a pair in an array with a given sum.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/check-if-pair-with-given-sum-exists-in-array)  
**Solution**:
```python
def find_pair(arr, target):
    seen = set()
    for num in arr:
        if target - num in seen:
            return True
        seen.add(num)
    return False

# Example
arr = [2, 4, 3, 5, 6]
print(find_pair(arr, 7))  # Output: True (3 + 4 = 7)
```
**Explanation**: Use a hash set to store numbers. For each number, check if `target - num` exists in the set.  
**Time Complexity**: O(n)  
**Space Complexity**: O(n)

### 2. Best Time to Buy and Sell Stock
**Problem**: Find the maximum profit from one buy and one sell.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/best-time-to-buy-and-sell-stock/)  
**Solution**:
```python
def max_profit(prices):
    min_price = float('inf')
    max_profit = 0
    for price in prices:
        min_price = min(min_price, price)
        max_profit = max(max_profit, price - min_price)
    return max_profit

# Example
prices = [7, 1, 5, 3, 6, 4]
print(max_profit(prices))  # Output: 5 (buy at 1, sell at 6)
```
**Explanation**: Track the minimum price and update the maximum profit by comparing current price minus minimum price.  
**Time Complexity**: O(n)  
**Space Complexity**: O(1)

### 3. Find Duplicates
**Problem**: Find all duplicates in an array.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/find-duplicates-in-on-time-and-constant-extra-space/)  
**Solution**:
```python
def find_duplicates(arr):
    result = []
    for num in arr:
        index = abs(num) - 1
        if arr[index] > 0:
            arr[index] = -arr[index]
        else:
            result.append(abs(num))
    return result

# Example
arr = [4, 3, 2, 7, 8, 2, 3, 1]
print(find_duplicates(arr))  # Output: [2, 3]
```
**Explanation**: Use array indices to mark presence by negating values. Duplicates are numbers whose indices are already negative.  
**Time Complexity**: O(n)  
**Space Complexity**: O(1)

### 4. Product of Array Except Self
**Problem**: Compute the product of all elements except the current index.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/a-product-array-puzzle)  
**Solution**:
```python
def product_except_self(nums):
    n = len(nums)
    result = [1] * n
    left = 1
    for i in range(n):
        result[i] *= left
        left *= nums[i]
    right = 1
    for i in range(n-1, -1, -1):
        result[i] *= right
        right *= nums[i]
    return result

# Example
nums = [1, 2, 3, 4]
print(product_except_self(nums))  # Output: [24, 12, 8, 6]
```
**Explanation**: Compute products of all elements to the left and right of each index without using division.  
**Time Complexity**: O(n)  
**Space Complexity**: O(1)

### 5. Maximum Subarray
**Problem**: Find the contiguous subarray with the largest sum.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/largest-sum-contiguous-subarray)  
**Solution**:
```python
def max_subarray_sum(nums):
    max_sum = current_sum = nums[0]
    for num in nums[1:]:
        current_sum = max(num, current_sum + num)
        max_sum = max(max_sum, current_sum)
    return max_sum

# Example
nums = [-2, 1, -3, 4, -1, 2, 1, -5, 4]
print(max_subarray_sum(nums))  # Output: 6 ([4, -1, 2, 1])
```
**Explanation**: Use Kadane’s algorithm to track the maximum sum ending at each position.  
**Time Complexity**: O(n)  
**Space Complexity**: O(1)

### 6. Maximum Product Subarray
**Problem**: Find the contiguous subarray with the maximum product.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/maximum-product-subarray)  
**Solution**:
```python
def max_product_subarray(nums):
    max_product = min_product = result = nums[0]
    for num in nums[1:]:
        temp_max = max(num, max_product * num, min_product * num)
        min_product = min(num, max_product * num, min_product * num)
        max_product = temp_max
        result = max(result, max_product)
    return result

# Example
nums = [2, 3, -2, 4]
print(max_product_subarray(nums))  # Output: 6 ([2, 3])
```
**Explanation**: Track both maximum and minimum products due to negative numbers.  
**Time Complexity**: O(n)  
**Space Complexity**: O(1)

### 7. Minimum in Rotated Sorted Array
**Problem**: Find the minimum element in a rotated sorted array.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/find-minimum-element-in-a-sorted-and-rotated-array)  
**Solution**:
```python
def find_min(nums):
    left, right = 0, len(nums) - 1
    while left < right:
        mid = left + (right - left) // 2
        if nums[mid] > nums[right]:
            left = mid + 1
        else:
            right = mid
    return nums[left]

# Example
nums = [3, 4, 5, 1, 2]
print(find_min(nums))  # Output: 1
```
**Explanation**: Use binary search to find the pivot where the array rotates.  
**Time Complexity**: O(log n)  
**Space Complexity**: O(1)

### 8. Search in Rotated Sorted Array
**Problem**: Search for a target in a rotated sorted array.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/search-an-element-in-a-sorted-and-pivoted-array)  
**Solution**:
```python
def search(nums, target):
    left, right = 0, len(nums) - 1
    while left <= right:
        mid = left + (right - left) // 2
        if nums[mid] == target:
            return mid
        if nums[left] <= nums[mid]:
            if nums[left] <= target < nums[mid]:
                right = mid - 1
            else:
                left = mid + 1
        else:
            if nums[mid] < target <= nums[right]:
                left = mid + 1
            else:
                right = mid - 1
    return -1

# Example
nums = [4, 5, 6, 7, 0, 1, 2]
print(search(nums, 0))  # Output: 4
```
**Explanation**: Use binary search, adjusting for rotation by checking which half is sorted.  
**Time Complexity**: O(log n)  
**Space Complexity**: O(1)

### 9. 3 Sum
**Problem**: Find all triplets summing to zero.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/find-triplets-array-whose-sum-equal-zero)  
**Solution**:
```python
def three_sum(nums):
    nums.sort()
    result = []
    for i in range(len(nums) - 2):
        if i > 0 and nums[i] == nums[i - 1]:
            continue
        left, right = i + 1, len(nums) - 1
        while left < right:
            total = nums[i] + nums[left] + nums[right]
            if total == 0:
                result.append([nums[i], nums[left], nums[right]])
                left += 1
                right -= 1
                while left < right and nums[left] == nums[left - 1]:
                    left += 1
                while left < right and nums[right] == nums[right + 1]:
                    right -= 1
            elif total < 0:
                left += 1
            else:
                right -= 1
    return result

# Example
nums = [-1, 0, 1, 2, -1, -4]
print(three_sum(nums))  # Output: [[-1, -1, 2], [-1, 0, 1]]
```
**Explanation**: Sort the array and use two pointers to find triplets. Skip duplicates for uniqueness.  
**Time Complexity**: O(n²)  
**Space Complexity**: O(1) (excluding output)

### 10. Container With Most Water
**Problem**: Find two lines that hold the maximum water.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/container-with-most-water)  
**Solution**:
```python
def max_area(height):
    left, right = 0, len(height) - 1
    max_water = 0
    while left < right:
        max_water = max(max_water, min(height[left], height[right]) * (right - left))
        if height[left] < height[right]:
            left += 1
        else:
            right -= 1
    return max_water

# Example
height = [1, 8, 6, 2, 5, 4, 8, 3, 7]
print(max_area(height))  # Output: 49
```
**Explanation**: Use two pointers to maximize area, moving the shorter line inward.  
**Time Complexity**: O(n)  
**Space Complexity**: O(1)

### 11. Factorial of a Large Number
**Problem**: Compute the factorial of a large number.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/factorial-large-number)  
**Solution**:
```python
def factorial(n):
    result = [1]
    for i in range(2, n + 1):
        carry = 0
        for j in range(len(result)):
            product = result[j] * i + carry
            result[j] = product % 10
            carry = product // 10
        while carry:
            result.append(carry % 10)
            carry //= 10
    return ''.join(map(str, result[::-1]))

# Example
print(factorial(20))  # Output: 2432902008176640000
```
**Explanation**: Store digits in an array and multiply iteratively, handling carry for large numbers.  
**Time Complexity**: O(n log n)  
**Space Complexity**: O(log n!)

### 12. Trapping Rain Water
**Problem**: Compute the water trapped by bars.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/trapping-rain-water)  
**Solution**:
```python
def trap(height):
    left, right = 0, len(height) - 1
    left_max = right_max = water = 0
    while left < right:
        if height[left] < height[right]:
            left_max = max(left_max, height[left])
            water += left_max - height[left]
            left += 1
        else:
            right_max = max(right_max, height[right])
            water += right_max - height[right]
            right -= 1
    return water

# Example
height = [0, 1, 0, 2, 1, 0, 1, 3, 2, 1, 2, 1]
print(trap(height))  # Output: 6
```
**Explanation**: Use two pointers to track maximum heights from both sides, calculating trapped water.  
**Time Complexity**: O(n)  
**Space Complexity**: O(1)

### 13. Chocolate Distribution Problem
**Problem**: Minimize the difference between max and min chocolates given to m students.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/chocolate-distribution-problem)  
**Solution**:
```python
def min_diff(arr, m):
    arr.sort()
    min_diff = float('inf')
    for i in range(len(arr) - m + 1):
        min_diff = min(min_diff, arr[i + m - 1] - arr[i])
    return min_diff

# Example
arr = [7, 3, 2, 4, 9, 12, 56]
m = 3
print(min_diff(arr, m))  # Output: 2
```
**Explanation**: Sort the array and find the minimum difference between max and min in each window of size m.  
**Time Complexity**: O(n log n)  
**Space Complexity**: O(1)

### 14. Insert Interval
**Problem**: Insert a new interval into a sorted list of non-overlapping intervals.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/insert-in-sorted-and-non-overlapping-interval-array)  
**Solution**:
```python
def insert_interval(intervals, new_interval):
    result = []
    i = 0
    n = len(intervals)
    while i < n and intervals[i][1] < new_interval[0]:
        result.append(intervals[i])
        i += 1
    while i < n and intervals[i][0] <= new_interval[1]:
        new_interval = [min(new_interval[0], intervals[i][0]), max(new_interval[1], intervals[i][1])]
        i += 1
    result.append(new_interval)
    while i < n:
        result.append(intervals[i])
        i += 1
    return result

# Example
intervals = [[1, 3], [6, 9]]
new_interval = [2, 5]
print(insert_interval(intervals, new_interval))  # Output: [[1, 5], [6, 9]]
```
**Explanation**: Merge overlapping intervals while inserting the new interval.  
**Time Complexity**: O(n)  
**Space Complexity**: O(1) (excluding output)

### 15. Merge Intervals
**Problem**: Merge overlapping intervals.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/merging-intervals)  
**Solution**:
```python
def merge_intervals(intervals):
    intervals.sort(key=lambda x: x[0])
    result = []
    current = intervals[0]
    for interval in intervals[1:]:
        if interval[0] <= current[1]:
            current[1] = max(current[1], interval[1])
        else:
            result.append(current)
            current = interval
    result.append(current)
    return result

# Example
intervals = [[1, 3], [2, 6], [8, 10], [15, 18]]
print(merge_intervals(intervals))  # Output: [[1, 6], [8, 10], [15, 18]]
```
**Explanation**: Sort intervals by start time and merge overlapping ones.  
**Time Complexity**: O(n log n)  
**Space Complexity**: O(1) (excluding output)

### 16. Non-overlapping Intervals
**Problem**: Remove the minimum number of intervals to make the rest non-overlapping.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/find-non-overlapping-intervals-among-a-given-set-of-intervals)  
**Solution**:
```python
def erase_overlap_intervals(intervals):
    intervals.sort(key=lambda x: x[1])
    count = 0
    prev_end = intervals[0][1]
    for start, end in intervals[1:]:
        if start < prev_end:
            count += 1
            prev_end = min(prev_end, end)
        else:
            prev_end = end
    return count

# Example
intervals = [[1, 2], [2, 3], [3, 4], [1, 3]]
print(erase_overlap_intervals(intervals))  # Output: 1
```
**Explanation**: Sort by end time and count intervals that overlap with the previous one.  
**Time Complexity**: O(n log n)  
**Space Complexity**: O(1)

---

## Matrix (4 Questions)

### 17. Set Matrix Zeroes
**Problem**: Set entire row and column to zero if an element is zero.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/a-boolean-matrix-question)  
**Solution**:
```python
def set_zeroes(matrix):
    m, n = len(matrix), len(matrix[0])
    first_row, first_col = False, False
    for j in range(n):
        if matrix[0][j] == 0:
            first_row = True
    for i in range(m):
        if matrix[i][0] == 0:
            first_col = True
    for i in range(1, m):
        for j in range(1, n):
            if matrix[i][j] == 0:
                matrix[i][0] = matrix[0][j] = 0
    for i in range(1, m):
        if matrix[i][0] == 0:
            for j in range(n):
                matrix[i][j] = 0
    for j in range(1, n):
        if matrix[0][j] == 0:
            for i in range(m):
                matrix[i][j] = 0
    if first_row:
        for j in range(n):
            matrix[0][j] = 0
    if first_col:
        for i in range(m):
            matrix[i][0] = 0

# Example
matrix = [[1, 1, 1], [1, 0, 1], [1, 1, 1]]
set_zeroes(matrix)
print(matrix)  # Output: [[1, 0, 1], [0, 0, 0], [1, 0, 1]]
```
**Explanation**: Use the first row and column as markers to avoid extra space.  
**Time Complexity**: O(m*n)  
**Space Complexity**: O(1)

### 18. Spiral Matrix
**Problem**: Return elements of a matrix in spiral order.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/print-a-given-matrix-in-spiral-form)  
**Solution**:
```python
def spiral_order(matrix):
    if not matrix:
        return []
    result = []
    top, bottom = 0, len(matrix) - 1
    left, right = 0, len(matrix[0]) - 1
    while top <= bottom and left <= right:
        for j in range(left, right + 1):
            result.append(matrix[top][j])
        top += 1
        for i in range(top, bottom + 1):
            result.append(matrix[i][right])
        right -= 1
        if top <= bottom:
            for j in range(right, left - 1, -1):
                result.append(matrix[bottom][j])
            bottom -= 1
        if left <= right:
            for i in range(bottom, top - 1, -1):
                result.append(matrix[i][left])
            left += 1
    return result

# Example
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
print(spiral_order(matrix))  # Output: [1, 2, 3, 6, 9, 8, 7, 4, 5]
```
**Explanation**: Traverse the matrix layer by layer in a spiral pattern.  
**Time Complexity**: O(m*n)  
**Space Complexity**: O(1) (excluding output)

### 19. Transpose of a Matrix
**Problem**: Compute the transpose of a matrix.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/program-to-find-transpose-of-a-matrix)  
**Solution**:
```python
def transpose(matrix):
    n = len(matrix)
    for i in range(n):
        for j in range(i + 1, n):
            matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]

# Example
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
transpose(matrix)
print(matrix)  # Output: [[1, 4, 7], [2, 5, 8], [3, 6, 9]]
```
**Explanation**: Swap elements across the main diagonal for a square matrix.  
**Time Complexity**: O(n²)  
**Space Complexity**: O(1)

### 20. Word Search
**Problem**: Find if a word exists in a 2D grid.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/search-a-word-in-a-2d-grid-of-characters)  
**Solution**:
```python
def exist(board, word):
    def dfs(i, j, k):
        if k == len(word):
            return True
        if i < 0 or i >= len(board) or j < 0 or j >= len(board[0]) or board[i][j] != word[k]:
            return False
        temp = board[i][j]
        board[i][j] = '#'
        result = dfs(i + 1, j, k + 1) or dfs(i - 1, j, k + 1) or dfs(i, j + 1, k + 1) or dfs(i, j - 1, k + 1)
        board[i][j] = temp
        return result
    
    for i in range(len(board)):
        for j in range(len(board[0])):
            if board[i][j] == word[0] and dfs(i, j, 0):
                return True
    return False

# Example
board = [["A", "B", "C", "E"], ["S", "F", "C", "S"], ["A", "D", "E", "E"]]
word = "ABCCED"
print(exist(board, word))  # Output: True
```
**Explanation**: Use DFS to explore all paths, marking visited cells to avoid reuse.  
**Time Complexity**: O(m*n*4^len(word))  
**Space Complexity**: O(len(word)) (recursion stack)

---

## String (10 Questions)

### 21. Longest Substring Without Repeating Characters
**Problem**: Find the length of the longest substring without repeating characters.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/length-of-the-longest-substring-without-repeating-characters)  
**Solution**:
```python
def length_of_longest_substring(s):
    seen = {}
    max_length = start = 0
    for end in range(len(s)):
        if s[end] in seen and seen[s[end]] >= start:
            start = seen[s[end]] + 1
        else:
            max_length = max(max_length, end - start + 1)
        seen[s[end]] = end
    return max_length

# Example
s = "abcabcbb"
print(length_of_longest_substring(s))  # Output: 3 ("abc")
```
**Explanation**: Use a sliding window with a hash map to track character positions.  
**Time Complexity**: O(n)  
**Space Complexity**: O(min(m, n)) (m is charset size)

### 22. Longest Repeating Character Replacement
**Problem**: Replace at most k characters to get the longest substring with the same letter.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/maximum-consecutive-repeating-character-string)  
**Solution**:
```python
def character_replacement(s, k):
    count = {}
    max_length = max_count = 0
    left = 0
    for right in range(len(s)):
        count[s[right]] = count.get(s[right], 0) + 1
        max_count = max(max_count, count[s[right]])
        if right - left + 1 - max_count > k:
            count[s[left]] -= 1
            left += 1
        max_length = max(max_length, right - left + 1)
    return max_length

# Example
s = "AABABBA"
k = 1
print(character_replacement(s, k))  # Output: 4
```
**Explanation**: Use a sliding window to track the most frequent character, ensuring replacements don’t exceed k.  
**Time Complexity**: O(n)  
**Space Complexity**: O(m) (m is charset size)

### 23. Smallest Window Containing All Characters
**Problem**: Find the smallest substring containing all characters of another string.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/find-the-smallest-window-in-a-string-containing-all-characters-of-another-string)  
**Solution**:
```python
def min_window(s, t):
    if not t or not s:
        return ""
    t_count = {}
    for char in t:
        t_count[char] = t_count.get(char, 0) + 1
    required = len(t_count)
    formed = 0
    window_counts = {}
    left = right = 0
    min_len = float('inf')
    min_window_substr = ""
    while right < len(s):
        char = s[right]
        window_counts[char] = window_counts.get(char, 0) + 1
        if char in t_count and window_counts[char] == t_count[char]:
            formed += 1
        while left <= right and formed == required:
            char = s[left]
            if right - left + 1 < min_len:
                min_len = right - left + 1
                min_window_substr = s[left:right + 1]
            window_counts[char] -= 1
            if char in t_count and window_counts[char] < t_count[char]:
                formed -= 1
            left += 1
        right += 1
    return min_window_substr if min_len != float('inf') else ""

# Example
s = "ADOBECODEBANC"
t = "ABC"
print(min_window(s, t))  # Output: "BANC"
```
**Explanation**: Use a sliding window to find the smallest substring covering all characters in t.  
**Time Complexity**: O(n)  
**Space Complexity**: O(m) (m is charset size)

### 24. Check for Anagram
**Problem**: Check if two strings are anagrams.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/check-whether-two-strings-are-anagram-of-each-other)  
**Solution**:
```python
def is_anagram(s, t):
    if len(s) != len(t):
        return False
    count = [0] * 26
    for c1, c2 in zip(s, t):
        count[ord(c1) - ord('a')] += 1
        count[ord(c2) - ord('a')] -= 1
    return all(c == 0 for c in count)

# Example
s = "anagram"
t = "nagaram"
print(is_anagram(s, t))  # Output: True
```
**Explanation**: Use a frequency array to compare character counts.  
**Time Complexity**: O(n)  
**Space Complexity**: O(1) (fixed-size array)

### 25. Print All Anagrams Together
**Problem**: Group anagrams from a list of strings.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/given-a-sequence-of-words-print-all-anagrams-together)  
**Solution**:
```python
def group_anagrams(strs):
    anagram_map = {}
    for s in strs:
        sorted_s = ''.join(sorted(s))
        if sorted_s not in anagram_map:
            anagram_map[sorted_s] = []
        anagram_map[sorted_s].append(s)
    return list(anagram_map.values())

# Example
strs = ["eat", "tea", "tan", "ate", "nat", "bat"]
print(group_anagrams(strs))  # Output: [["eat", "tea", "ate"], ["tan", "nat"], ["bat"]]
```
**Explanation**: Sort each string to use as a key in a hash map, grouping anagrams.  
**Time Complexity**: O(n*k*log k) (k is max string length)  
**Space Complexity**: O(n*k)

### 26. Check Balanced Parentheses
**Problem**: Check if a string of parentheses is balanced.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/check-if-given-parentheses-expression-is-balanced-or-not)  
**Solution**:
```python
def is_valid(s):
    stack = []
    brackets = {')': '(', '}': '{', ']': '['}
    for char in s:
        if char in brackets.values():
            stack.append(char)
        elif char in brackets:
            if not stack or stack.pop() != brackets[char]:
                return False
    return not stack

# Example
s = "({[]})"
print(is_valid(s))  # Output: True
```
**Explanation**: Use a stack to match opening and closing brackets.  
**Time Complexity**: O(n)  
**Space Complexity**: O(n)

### 27. Sentence Palindrome
**Problem**: Check if a sentence is a palindrome, ignoring spaces and punctuation.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/sentence-palindrome-palindrome-removing-spaces-dots-etc)  
**Solution**:
```python
def is_sentence_palindrome(s):
    s = ''.join(c.lower() for c in s if c.isalnum())
    left, right = 0, len(s) - 1
    while left < right:
        if s[left] != s[right]:
            return False
        left += 1
        right -= 1
    return True

# Example
s = "A man, a plan, a canal: Panama"
print(is_sentence_palindrome(s))  # Output: True
```
**Explanation**: Clean the string and check if it’s a palindrome using two pointers.  
**Time Complexity**: O(n)  
**Space Complexity**: O(n)

### 28. Longest Palindromic Substring
**Problem**: Find the longest palindromic substring.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/longest-palindromic-substring)  
**Solution**:
```python
def longest_palindrome(s):
    n = len(s)
    start = max_len = 0
    for i in range(n):
        left, right = i, i
        while left >= 0 and right < n and s[left] == s[right]:
            if right - left + 1 > max_len:
                start = left
                max_len = right - left + 1
            left -= 1
            right += 1
        left, right = i, i + 1
        while left >= 0 and right < n and s[left] == s[right]:
            if right - left + 1 > max_len:
                start = left
                max_len = right - left + 1
            left -= 1
            right += 1
    return s[start:start + max_len]

# Example
s = "babad"
print(longest_palindrome(s))  # Output: "bab" or "aba"
```
**Explanation**: Expand around each center to find the longest palindrome.  
**Time Complexity**: O(n²)  
**Space Complexity**: O(1)

### 29. Palindromic Substrings
**Problem**: Count all palindromic substrings.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/count-palindrome-sub-strings-string)  
**Solution**:
```python
def count_palindromes(s):
    count = 0
    n = len(s)
    for i in range(n):
        left, right = i, i
        while left >= 0 and right < n and s[left] == s[right]:
            count += 1
            left -= 1
            right += 1
        left, right = i, i + 1
        while left >= 0 and right < n and s[left] == s[right]:
            count += 1
            left -= 1
            right += 1
    return count

# Example
s = "aba"
print(count_palindromes(s))  # Output: 4 ("a", "b", "a", "aba")
```
**Explanation**: Expand around each center to count all palindromic substrings.  
**Time Complexity**: O(n²)  
**Space Complexity**: O(1)

### 30. Longest Common Prefix
**Problem**: Find the longest common prefix among an array of strings.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/longest-common-prefix-using-sorting)  
**Solution**:
```python
def longest_common_prefix(strs):
    if not strs:
        return ""
    if len(strs) == 1:
        return strs[0]
    strs.sort()
    result = ""
    for i in range(len(strs[0])):
        if i < len(strs[-1]) and strs[0][i] == strs[-1][i]:
            result += strs[0][i]
        else:
            break
    return result

# Example
strs = ["flower", "flow", "flight"]
print(longest_common_prefix(strs))  # Output: "fl"
```
**Explanation**: Sort strings and compare the first and last strings to find the common prefix.  
**Time Complexity**: O(n*log n + m) (m is min string length)  
**Space Complexity**: O(1)

---

## Linked List (9 Questions)

### 31. Reverse a Linked List
**Problem**: Reverse a singly linked list.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/reverse-a-linked-list)  
**Solution**:
```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def reverse_list(head):
    prev = None
    current = head
    while current:
        next_node = current.next
        current.next = prev
        prev = current
        current = next_node
    return prev

# Example
head = ListNode(1, ListNode(2, ListNode(3)))
reversed_head = reverse_list(head)
while reversed_head:
    print(reversed_head.val, end=" ")  # Output: 3 2 1
    reversed_head = reversed_head.next
```
**Explanation**: Reverse pointers iteratively by adjusting the `next` pointer of each node.  
**Time Complexity**: O(n)  
**Space Complexity**: O(1)

### 32. Detect Cycle in a Linked List
**Problem**: Detect if a linked list has a cycle.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/detect-loop-in-a-linked-list)  
**Solution**:
```python
def has_cycle(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            return True
    return False

# Example
head = ListNode(1, ListNode(2, ListNode(3)))
head.next.next.next = head  # Create cycle
print(has_cycle(head))  # Output: True
```
**Explanation**: Use Floyd’s cycle detection (two pointers) to identify a cycle.  
**Time Complexity**: O(n)  
**Space Complexity**: O(1)

### 33. Merge Two Sorted Lists
**Problem**: Merge two sorted linked lists.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/merge-two-sorted-linked-lists)  
**Solution**:
```python
def merge_two_lists(l1, l2):
    dummy = ListNode(0)
    current = dummy
    while l1 and l2:
        if l1.val <= l2.val:
            current.next = l1
            l1 = l1.next
        else:
            current.next = l2
            l2 = l2.next
        current = current.next
    current.next = l1 if l1 else l2
    return dummy.next

# Example
l1 = ListNode(1, ListNode(3))
l2 = ListNode(2, ListNode(4))
merged = merge_two_lists(l1, l2)
while merged:
    print(merged.val, end=" ")  # Output: 1 2 3 4
    merged = merged.next
```
**Explanation**: Merge lists by comparing nodes and linking the smaller value.  
**Time Complexity**: O(n + m)  
**Space Complexity**: O(1)

### 34. Merge K Sorted Lists
**Problem**: Merge k sorted linked lists.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/merge-k-sorted-linked-lists)  
**Solution**:
```python
from heapq import heappush, heappop

def merge_k_lists(lists):
    heap = []
    dummy = ListNode(0)
    current = dummy
    for i, head in enumerate(lists):
        if head:
            heappush(heap, (head.val, i, head))
    while heap:
        val, i, node = heappop(heap)
        current.next = node
        current = current.next
        if node.next:
            heappush(heap, (node.next.val, i, node.next))
    return dummy.next

# Example
lists = [ListNode(1, ListNode(4)), ListNode(2, ListNode(5)), ListNode(3)]
merged = merge_k_lists(lists)
while merged:
    print(merged.val, end=" ")  # Output: 1 2 3 4 5
    merged = merged.next
```
**Explanation**: Use a min-heap to select the smallest node from k lists.  
**Time Complexity**: O(n*log k) (n is total nodes, k is number of lists)  
**Space Complexity**: O(k)

### 35. Remove Nth Node From End of List
**Problem**: Remove the nth node from the end of a linked list.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/remove-nth-node-from-end-of-the-linked-list)  
**Solution**:
```python
def remove_nth_from_end(head, n):
    dummy = ListNode(0, head)
    slow = fast = dummy
    for _ in range(n):
        fast = fast.next
    while fast.next:
        slow = slow.next
        fast = fast.next
    slow.next = slow.next.next
    return dummy.next

# Example
head = ListNode(1, ListNode(2, ListNode(3, ListNode(4))))
new_head = remove_nth_from_end(head, 2)
while new_head:
    print(new_head.val, end=" ")  # Output: 1 2 4
    new_head = new_head.next
```
**Explanation**: Use two pointers with a gap of n to locate the node to remove.  
**Time Complexity**: O(n)  
**Space Complexity**: O(1)

### 36. Reorder List
**Problem**: Reorder list as L0→Ln→L1→Ln-1→L2→….  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/reorder-list/)  
**Solution**:
```python
def reorder_list(head):
    if not head or not head.next:
        return
    slow = fast = head
    while fast.next and fast.next.next:
        slow = slow.next
        fast = fast.next.next
    second = slow.next
    slow.next = None
    prev = None
    while second:
        next_node = second.next
        second.next = prev
        prev = second
        second = next_node
    first = head
    while prev:
        next_first = first.next
        next_prev = prev.next
        first.next = prev
        prev.next = next_first
        first = next_first
        prev = next_prev

# Example
head = ListNode(1, ListNode(2, ListNode(3, ListNode(4))))
reorder_list(head)
while head:
    print(head.val, end=" ")  # Output: 1 4 2 3
    head = head.next
```
**Explanation**: Split list, reverse second half, and merge alternately.  
**Time Complexity**: O(n)  
**Space Complexity**: O(1)

### 37. Add 1 to a Number Represented as Linked List
**Problem**: Add 1 to a number represented by a linked list.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/add-1-number-represented-linked-list)  
**Solution**:
```python
def add_one(head):
    def reverse(head):
        prev = None
        current = head
        while current:
            next_node = current.next
            current.next = prev
            prev = current
            current = next_node
        return prev
    
    head = reverse(head)
    current = head
    carry = 1
    while current and carry:
        total = current.val + carry
        current.val = total % 10
        carry = total // 10
        if not current.next and carry:
            current.next = ListNode(carry)
            carry = 0
        current = current.next
    return reverse(head)

# Example
head = ListNode(9, ListNode(9))
new_head = add_one(head)
while new_head:
    print(new_head.val, end=" ")  # Output: 1 0 0
    new_head = new_head.next
```
**Explanation**: Reverse list, add 1 with carry, and reverse back.  
**Time Complexity**: O(n)  
**Space Complexity**: O(1)

### 38. Middle of a Given Linked List
**Problem**: Find the middle node of a linked list.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/write-a-c-function-to-print-the-middle-of-the-linked-list)  
**Solution**:
```python
def middle_node(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    return slow

# Example
head = ListNode(1, ListNode(2, ListNode(3, ListNode(4))))
middle = middle_node(head)
print(middle.val)  # Output: 3
```
**Explanation**: Use two pointers; slow moves one step, fast moves two.  
**Time Complexity**: O(n)  
**Space Complexity**: O(1)

### 39. Delete Last Occurrence from Linked List
**Problem**: Delete the last occurrence of a key in a linked list.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/delete-last-occurrence-of-an-item-from-linked-list)  
**Solution**:
```python
def delete_last_occurrence(head, key):
    dummy = ListNode(0, head)
    last = None
    current = dummy
    while current.next:
        if current.next.val == key:
            last = current
        current = current.next
    if last:
        last.next = last.next.next
    return dummy.next

# Example
head = ListNode(1, ListNode(2, ListNode(6, ListNode(3, ListNode(6)))))
new_head = delete_last_occurrence(head, 6)
while new_head:
    print(new_head.val, end=" ")  # Output: 1 2 6 3
    new_head = new_head.next
```
**Explanation**: Track the last occurrence of the key and remove it.  
**Time Complexity**: O(n)  
**Space Complexity**: O(1)

---

## Stack & Queue (8 Questions)

### 40. Infix to Postfix Expression
**Problem**: Convert an infix expression to postfix.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/convert-infix-expression-to-postfix-expression)  
**Solution**:
```python
def infix_to_postfix(infix):
    precedence = {'+': 1, '-': 1, '*': 2, '/': 2, '^': 3}
    stack = []
    result = []
    for char in infix:
        if char.isalnum():
            result.append(char)
        elif char == '(':
            stack.append(char)
        elif char == ')':
            while stack and stack[-1] != '(':
                result.append(stack.pop())
            stack.pop()
        else:
            while stack and stack[-1] != '(' and precedence.get(char, 0) <= precedence.get(stack[-1], 0):
                result.append(stack.pop())
            stack.append(char)
    while stack:
        result.append(stack.pop())
    return ''.join(result)

# Example
infix = "A+B*(C^D-E)"
print(infix_to_postfix(infix))  # Output: "ABCD^E-*+"
```
**Explanation**: Use a stack to handle operator precedence and parentheses.  
**Time Complexity**: O(n)  
**Space Complexity**: O(n)

### 41. Next Greater Element
**Problem**: Find the next greater element for each element in an array.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/next-greater-element)  
**Solution**:
```python
def next_greater_element(arr):
    stack = []
    result = [-1] * len(arr)
    for i in range(len(arr)):
        while stack and arr[stack[-1]] < arr[i]:
            result[stack.pop()] = arr[i]
        stack.append(i)
    return result

# Example
arr = [1, 3, 2, 4]
print(next_greater_element(arr))  # Output: [3, 4, 4, -1]
```
**Explanation**: Use a stack to find the next larger element for each position.  
**Time Complexity**: O(n)  
**Space Complexity**: O(n)

### 42. Delete Middle Element of a Stack
**Problem**: Delete the middle element of a stack.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/delete-middle-element-stack)  
**Solution**:
```python
def delete_middle(stack, k):
    if k == 1:
        stack.pop()
        return
    temp = stack.pop()
    delete_middle(stack, k - 1)
    stack.append(temp)

def delete_middle_stack(stack):
    if not stack:
        return
    k = (len(stack) + 1) // 2
    delete_middle(stack, k)

# Example
stack = [1, 2, 3, 4, 5]
delete_middle_stack(stack)
print(stack)  # Output: [1, 2, 4, 5]
```
**Explanation**: Use recursion to remove the middle element by popping and restoring elements.  
**Time Complexity**: O(n)  
**Space Complexity**: O(n) (recursion stack)

### 43. Check Mirror in N-ary Tree
**Problem**: Check if two n-ary trees are mirrors.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/check-mirror-n-ary-tree)  
**Solution**:
```python
class Node:
    def __init__(self, val=0, children=None):
        self.val = val
        self.children = children if children else []

def are_mirrors(root1, root2):
    if not root1 and not root2:
        return True
    if not root1 or not root2 or root1.val != root2.val:
        return False
    if len(root1.children) != len(root2.children):
        return False
    for i in range(len(root1.children)):
        if not are_mirrors(root1.children[i], root2.children[len(root2.children) - 1 - i]):
            return False
    return True

# Example (simplified)
root1 = Node(1, [Node(2), Node(3)])
root2 = Node(1, [Node(3), Node(2)])
print(are_mirrors(root1, root2))  # Output: True
```
**Explanation**: Recursively check if children are mirrored in reverse order.  
**Time Complexity**: O(n)  
**Space Complexity**: O(h) (h is tree height)

### 44. The Celebrity Problem
**Problem**: Find the celebrity in a party (knows no one, everyone knows them).  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/the-celebrity-problem)  
**Solution**:
```python
def find_celebrity(n, knows):
    candidate = 0
    for i in range(1, n):
        if knows[candidate][i]:
            candidate = i
    for i in range(n):
        if i != candidate and (knows[candidate][i] or not knows[i][candidate]):
            return -1
    return candidate

# Example (knows is a matrix or function)
# Assume knows[i][j] returns True if i knows j
```
**Explanation**: Find a candidate by eliminating non-celebrities, then verify.  
**Time Complexity**: O(n)  
**Space Complexity**: O(1)

### 45. Length of the Longest Valid Substring
**Problem**: Find the length of the longest valid parentheses substring.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/length-of-the-longest-valid-substring)  
**Solution**:
```python
def longest_valid_parentheses(s):
    stack = [-1]
    max_length = 0
    for i in range(len(s)):
        if s[i] == '(':
            stack.append(i)
        else:
            stack.pop()
            if not stack:
                stack.append(i)
            else:
                max_length = max(max_length, i - stack[-1])
    return max_length

# Example
s = "(()()"
print(longest_valid_parentheses(s))  # Output: 4
```
**Explanation**: Use a stack to track indices of unmatched parentheses and compute valid lengths.  
**Time Complexity**: O(n)  
**Space Complexity**: O(n)

### 46. Print Right View of a Binary Tree
**Problem**: Print the rightmost node at each level of a binary tree.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/print-right-view-binary-tree-2)  
**Solution**:
```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def right_view(root):
    if not root:
        return []
    result = []
    queue = [root]
    while queue:
        level_size = len(queue)
        for i in range(level_size):
            node = queue.pop(0)
            if i == level_size - 1:
                result.append(node.val)
            if node.left:
                queue.append(node.left)
            if node.right:
                queue.append(node.right)
    return result

# Example
root = TreeNode(1, TreeNode(2), TreeNode(3, TreeNode(4)))
print(right_view(root))  # Output: [1, 3, 4]
```
**Explanation**: Use level-order traversal and record the last node at each level.  
**Time Complexity**: O(n)  
**Space Complexity**: O(w) (w is max width)

### 47. Find the First Circular Tour that Visits All
**Problem**: Find the starting point for a circular tour visiting all petrol pumps.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/find-a-tour-that-visits-all-stations)  
**Solution**:
```python
def circular_tour(petrol, distance):
    start = balance = deficit = 0
    for i in range(len(petrol)):
        balance += petrol[i] - distance[i]
        if balance < 0:
            deficit += balance
            start = i + 1
            balance = 0
    return start if balance + deficit >= 0 else -1

# Example
petrol = [4, 6, 7, 4]
distance = [6, 5, 3, 5]
print(circular_tour(petrol, distance))  # Output: 1
```
**Explanation**: Track fuel balance and adjust starting point if deficit occurs.  
**Time Complexity**: O(n)  
**Space Complexity**: O(1)

---

## Tree (13 Questions)

### 48. Maximum Depth of Binary Tree
**Problem**: Find the maximum depth of a binary tree.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/find-the-maximum-depth-or-height-of-a-tree)  
**Solution**:
```python
def max_depth(root):
    if not root:
        return 0
    left_depth = max_depth(root.left)
    right_depth = max_depth(root.right)
    return max(left_depth, right_depth) + 1

# Example
root = TreeNode(1, TreeNode(2, TreeNode(4)), TreeNode(3))
print(max_depth(root))  # Output: 3
```
**Explanation**: Recursively compute the maximum depth of left and right subtrees.  
**Time Complexity**: O(n)  
**Space Complexity**: O(h) (h is tree height)

### 49. Check if Two Trees Have Same Structure
**Problem**: Check if two trees have the same structure.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/check-if-two-trees-have-same-structure)  
**Solution**:
```python
def same_structure(root1, root2):
    if not root1 and not root2:
        return True
    if not root1 or not root2:
        return False
    return same_structure(root1.left, root2.left) and same_structure(root1.right, root2.right)

# Example
root1 = TreeNode(1, TreeNode(2), TreeNode(3))
root2 = TreeNode(4, TreeNode(5), TreeNode(6))
print(same_structure(root1, root2))  # Output: True
```
**Explanation**: Recursively compare the structure of left and right subtrees.  
**Time Complexity**: O(n)  
**Space Complexity**: O(h)

### 50. Invert/Flip Binary Tree
**Problem**: Invert a binary tree (swap left and right children).  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/flip-binary-tree)  
**Solution**:
```python
def invert_tree(root):
    if not root:
        return root
    root.left, root.right = invert_tree(root.right), invert_tree(root.left)
    return root

# Example
root = TreeNode(4, TreeNode(2, TreeNode(1), TreeNode(3)), TreeNode(7))
inverted = invert_tree(root)
# Inorder traversal to verify: 7 4 2 3 1
```
**Explanation**: Recursively swap left and right children for each node.  
**Time Complexity**: O(n)  
**Space Complexity**: O(h)

### 51. Binary Tree Maximum Path Sum
**Problem**: Find the maximum path sum in a binary tree.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/find-maximum-path-sum-in-a-binary-tree)  
**Solution**:
```python
def max_path_sum(root):
    max_sum = float('-inf')
    def path_sum(node):
        nonlocal max_sum
        if not node:
            return 0
        left = max(path_sum(node.left), 0)
        right = max(path_sum(node.right), 0)
        max_sum = max(max_sum, left + right + node.val)
        return max(left, right) + node.val
    path_sum(root)
    return max_sum

# Example
root = TreeNode(10, TreeNode(2, TreeNode(20), TreeNode(1)), TreeNode(-25))
print(max_path_sum(root))  # Output: 42 (20 + 2 + 10)
```
**Explanation**: Recursively compute max path sums, considering paths through the root.  
**Time Complexity**: O(n)  
**Space Complexity**: O(h)

### 52. Binary Tree Level Order Traversal
**Problem**: Return the level order traversal of a binary tree.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/level-order-tree-traversal)  
**Solution**:
```python
def level_order(root):
    if not root:
        return []
    result = []
    queue = [root]
    while queue:
        level = []
        for _ in range(len(queue)):
            node = queue.pop(0)
            level.append(node.val)
            if node.left:
                queue.append(node.left)
            if node.right:
                queue.append(node.right)
        result.append(level)
    return result

# Example
root = TreeNode(1, TreeNode(2), TreeNode(3, TreeNode(4)))
print(level_order(root))  # Output: [[1], [2, 3], [4]]
```
**Explanation**: Use a queue for BFS to collect nodes level by level.  
**Time Complexity**: O(n)  
**Space Complexity**: O(w)

### 53. Serialize and Deserialize Binary Tree
**Problem**: Serialize and deserialize a binary tree.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/serialize-deserialize-binary-tree)  
**Solution**:
```python
def serialize(root):
    if not root:
        return "null"
    return f"{root.val},{serialize(root.left)},{serialize(root.right)}"

def deserialize(data):
    def dfs():
        val = next(vals)
        if val == "null":
            return None
        node = TreeNode(int(val))
        node.left = dfs()
        node.right = dfs()
        return node
    vals = iter(data.split(','))
    return dfs()

# Example
root = TreeNode(1, TreeNode(2), TreeNode(3))
serialized = serialize(root)
deserialized = deserialize(serialized)
print(level_order(deserialized))  # Output: [[1], [2, 3]]
```
**Explanation**: Serialize using preorder traversal; deserialize using DFS.  
**Time Complexity**: O(n)  
**Space Complexity**: O(n)

### 54. Subtree of Another Tree
**Problem**: Check if a tree is a subtree of another tree.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/check-if-a-binary-tree-is-subtree-of-another-binary-tree)  
**Solution**:
```python
def is_subtree(root, sub_root):
    def is_same(tree1, tree2):
        if not tree1 and not tree2:
            return True
        if not tree1 or not tree2:
            return False
        return tree1.val == tree2.val and is_same(tree1.left, tree2.left) and is_same(tree1.right, tree2.right)
    
    if not sub_root:
        return True
    if not root:
        return False
    return is_same(root, sub_root) or is_subtree(root.left, sub_root) or is_subtree(root.right, sub_root)

# Example
root = TreeNode(3, TreeNode(4, TreeNode(1)), TreeNode(5))
sub_root = TreeNode(4, TreeNode(1))
print(is_subtree(root, sub_root))  # Output: True
```
**Explanation**: Check if trees are identical or if sub_root is a subtree of left/right subtrees.  
**Time Complexity**: O(m*n)  
**Space Complexity**: O(h)

### 55. Construct Binary Tree from Preorder and Inorder Traversal
**Problem**: Construct a binary tree from preorder and inorder traversals.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/construct-tree-from-given-inorder-and-preorder-traversal)  
**Solution**:
```python
def build_tree(preorder, inorder):
    if not preorder or not inorder:
        return None
    inorder_map = {val: i for i, val in enumerate(inorder)}
    def build(pre_start, pre_end, in_start, in_end):
        if pre_start > pre_end:
            return None
        root_val = preorder[pre_start]
        root = TreeNode(root_val)
        inorder_idx = inorder_map[root_val]
        left_size = inorder_idx - in_start
        root.left = build(pre_start + 1, pre_start + left_size, in_start, inorder_idx - 1)
        root.right = build(pre_start + left_size + 1, pre_end, inorder_idx + 1, in_end)
        return root
    return build(0, len(preorder) - 1, 0, len(inorder) - 1)

# Example
preorder = [3, 9, 20, 15, 7]
inorder = [9, 3, 15, 20, 7]
root = build_tree(preorder, inorder)
print(level_order(root))  # Output: [[3], [9, 20], [15, 7]]
```
**Explanation**: Use preorder for root and inorder to split left/right subtrees.  
**Time Complexity**: O(n)  
**Space Complexity**: O(n)

### 56. Validate Binary Search Tree
**Problem**: Check if a binary tree is a valid BST.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/a-program-to-check-if-a-binary-tree-is-bst-or-not)  
**Solution**:
```python
def is_valid_bst(root):
    def validate(node, min_val, max_val):
        if not node:
            return True
        if node.val <= min_val or node.val >= max_val:
            return False
        return validate(node.left, min_val, node.val) and validate(node.right, node.val, max_val)
    
    return validate(root, float('-inf'), float('inf'))

# Example
root = TreeNode(2, TreeNode(1), TreeNode(3))
print(is_valid_bst(root))  # Output: True
```
**Explanation**: Recursively check if each node’s value is within valid bounds.  
**Time Complexity**: O(n)  
**Space Complexity**: O(h)

### 57. Kth Smallest Element in a BST
**Problem**: Find the kth smallest element in a BST.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/find-k-th-smallest-element-in-bst-order-statistics-in-bst)  
**Solution**:
```python
def kth_smallest(root, k):
    def inorder(node):
        nonlocal k
        if not node:
            return None
        left = inorder(node.left)
        if left is not None:
            return left
        k -= 1
        if k == 0:
            return node.val
        return inorder(node.right)
    
    return inorder(root)

# Example
root = TreeNode(3, TreeNode(1), TreeNode(4, None, TreeNode(2)))
k = 1
print(kth_smallest(root, k))  # Output: 1
```
**Explanation**: Perform inorder traversal to find the kth smallest element.  
**Time Complexity**: O(n)  
**Space Complexity**: O(h)

### 58. Lowest Common Ancestor of BST
**Problem**: Find the lowest common ancestor in a BST.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/lowest-common-ancestor-in-a-binary-search-tree/)  
**Solution**:
```python
def lowest_common_ancestor(root, p, q):
    while root:
        if root.val > p.val and root.val > q.val:
            root = root.left
        elif root.val < p.val and root.val < q.val:
            root = root.right
        else:
            return root
    return None

# Example
root = TreeNode(6, TreeNode(2, TreeNode(0), TreeNode(4)), TreeNode(8))
p = root.left
q = root.right
lca = lowest_common_ancestor(root, p, q)
print(lca.val)  # Output: 6
```
**Explanation**: Use BST properties to navigate to the LCA.  
**Time Complexity**: O(h)  
**Space Complexity**: O(1)

### 59. Construct Binary Tree from Inorder and Postorder Traversal
**Problem**: Construct a binary tree from inorder and postorder traversals.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/construct-a-binary-tree-from-postorder-and-inorder/)  
**Solution**:
```python
def build_tree(inorder, postorder):
    if not inorder or not postorder:
        return None
    inorder_map = {val: i for i, val in enumerate(inorder)}
    def build(post_start, post_end, in_start, in_end):
        if post_start > post_end:
            return None
        root_val = postorder[post_end]
        root = TreeNode(root_val)
        inorder_idx = inorder_map[root_val]
        left_size = inorder_idx - in_start
        root.left = build(post_start, post_start + left_size - 1, in_start, inorder_idx - 1)
        root.right = build(post_start + left_size, post_end - 1, inorder_idx + 1, in_end)
        return root
    return build(0, len(postorder) - 1, 0, len(inorder) - 1)

# Example
inorder = [9, 3, 15, 20, 7]
postorder = [9, 15, 7, 20, 3]
root = build_tree(inorder, postorder)
print(level_order(root))  # Output: [[3], [9, 20], [15, 7]]
```
**Explanation**: Use postorder for root and inorder to split subtrees.  
**Time Complexity**: O(n)  
**Space Complexity**: O(n)

### 60. Construct Binary Tree from Preorder and Postorder Traversal
**Problem**: Construct a binary tree from preorder and postorder traversals.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/construct-a-binary-tree-from-postorder-and-preorder/)  
**Solution**:
```python
def construct_tree(preorder, postorder):
    if not preorder or not postorder:
        return None
    pre_idx = [0]
    post_map = {val: i for i, val in enumerate(postorder)}
    def build(pre_start, pre_end, post_start, post_end):
        if pre_start > pre_end:
            return None
        root = TreeNode(preorder[pre_start])
        pre_idx[0] += 1
        if pre_start == pre_end:
            return root
        next_val = preorder[pre_idx[0]]
        post_idx = post_map[next_val]
        left_size = post_idx - post_start + 1
        root.left = build(pre_idx[0], pre_start + left_size, post_start, post_idx)
        root.right = build(pre_idx[0] + left_size, pre_end, post_idx + 1, post_end - 1)
        return root
    return build(0, len(preorder) - 1, 0, len(postorder) - 1)

# Example
preorder = [1, 2, 4, 5, 3, 6]
postorder = [4, 5, 2, 6, 3, 1]
root = construct_tree(preorder, postorder)
print(level_order(root))  # Output: [[1], [2, 3], [4, 5, 6]]
```
**Explanation**: Use preorder for root and postorder to determine subtree boundaries.  
**Time Complexity**: O(n)  
**Space Complexity**: O(n)

---

## Heap (4 Questions)

### 61. Top K Frequent Elements
**Problem**: Find the k most frequent elements in an array.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/find-k-frequent-elements-stream-elements/)  
**Solution**:
```python
from collections import Counter
from heapq import heappush, heappop

def top_k_frequent(nums, k):
    count = Counter(nums)
    heap = []
    for num, freq in count.items():
        heappush(heap, (-freq, num))
    result = []
    for _ in range(k):
        result.append(heappop(heap)[1])
    return result

# Example
nums = [1, 1, 1, 2, 2, 3]
k = 2
print(top_k_frequent(nums, k))  # Output: [1, 2]
```
**Explanation**: Use a max heap to extract the k most frequent elements.  
**Time Complexity**: O(n log n)  
**Space Complexity**: O(n)

### 62. Find Median from Data Stream
**Problem**: Find the median of a data stream.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/median-of-stream-of-integers-running-integers/)  
**Solution**:
```python
from heapq import heappush, heappop

class MedianFinder:
    def __init__(self):
        self.small = []  # max heap
        self.large = []  # min heap

    def add_num(self, num):
        if len(self.small) == 0 or num < -self.small[0]:
            heappush(self.small, -num)
        else:
            heappush(self.large, num)
        if len(self.small) > len(self.large) + 1:
            heappush(self.large, -heappop(self.small))
        elif len(self.large) > len(self.small):
            heappush(self.small, -heappop(self.large))

    def find_median(self):
        if len(self.small) > len(self.large):
            return -self.small[0]
        return (-self.small[0] + self.large[0]) / 2

# Example
mf = MedianFinder()
mf.add_num(1)
mf.add_num(2)
print(mf.find_median())  # Output: 1.5
```
**Explanation**: Use two heaps to maintain balance and compute the median.  
**Time Complexity**: O(log n) per insertion, O(1) for median  
**Space Complexity**: O(n)

### 63. Largest Triplet Product in a Stream
**Problem**: Find the largest product of three numbers in a stream.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/largest-triplet-product-stream/)  
**Solution**:
```python
from heapq import heappush, heappop

def largest_triplet_product(nums):
    heap = []
    result = []
    for num in nums:
        heappush(heap, num)
        if len(heap) > 3:
            heappop(heap)
        if len(heap) == 3:
            temp = heap[:]
            product = 1
            for _ in range(3):
                product *= heappop(temp)
            result.append(product)
        else:
            result.append(-1)
    return result

# Example
nums = [1, 2, 3, 4, 5]
print(largest_triplet_product(nums))  # Output: [-1, -1, 6, 24, 60]
```
**Explanation**: Maintain a min-heap of size 3 to track the largest three numbers.  
**Time Complexity**: O(n log n)  
**Space Complexity**: O(1)

### 64. Sliding Window Maximum
**Problem**: Find the maximum in each sliding window of size k.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/sliding-window-maximum-maximum-of-all-subarrays-of-size-k/)  
**Solution**:
```python
from collections import deque

def max_sliding_window(nums, k):
    result = []
    dq = deque()
    for i in range(len(nums)):
        while dq and dq[0] <= i - k:
            dq.popleft()
        while dq and nums[dq[-1]] <= nums[i]:
            dq.pop()
        dq.append(i)
        if i >= k - 1:
            result.append(nums[dq[0]])
    return result

# Example
nums = [1, 3, -1, -3, 5, 3, 6, 7]
k = 3
print(max_sliding_window(nums, k))  # Output: [3, 3, 5, 5, 6, 7]
```
**Explanation**: Use a deque to maintain indices of potential maximums in the window, removing outdated or smaller elements.  
**Time Complexity**: O(n)  
**Space Complexity**: O(k)

---

## Graph (13 Questions)

### 65. Clone Graph
**Problem**: Clone an undirected graph.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/clone-an-undirected-graph/)  
**Solution**:
```python
class Node:
    def __init__(self, val=0, neighbors=None):
        self.val = val
        self.neighbors = neighbors if neighbors else []

def clone_graph(node):
    if not node:
        return None
    visited = {}
    def dfs(old_node):
        if old_node in visited:
            return visited[old_node]
        new_node = Node(old_node.val)
        visited[old_node] = new_node
        for neighbor in old_node.neighbors:
            new_node.neighbors.append(dfs(neighbor))
        return new_node
    return dfs(node)

# Example
# Graph: 1--2, 2--3, 3--1
node1 = Node(1)
node2 = Node(2)
node3 = Node(3)
node1.neighbors = [node2, node3]
node2.neighbors = [node1, node3]
node3.neighbors = [node1, node2]
cloned = clone_graph(node1)
print(cloned.val)  # Output: 1 (cloned graph)
```
**Explanation**: Use DFS to recursively clone nodes and their neighbors, tracking visited nodes to avoid cycles.  
**Time Complexity**: O(V + E) (V is vertices, E is edges)  
**Space Complexity**: O(V)

### 66. Course Schedule
**Problem**: Determine if all courses can be finished given prerequisites.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/find-whether-it-is-possible-to-finish-all-tasks-or-not-from-given-dependencies/)  
**Solution**:
```python
from collections import defaultdict, deque

def can_finish(num_courses, prerequisites):
    graph = defaultdict(list)
    indegree = [0] * num_courses
    for dest, src in prerequisites:
        graph[src].append(dest)
        indegree[dest] += 1
    queue = deque([i for i in range(num_courses) if indegree[i] == 0])
    count = 0
    while queue:
        course = queue.popleft()
        count += 1
        for neighbor in graph[course]:
            indegree[neighbor] -= 1
            if indegree[neighbor] == 0:
                queue.append(neighbor)
    return count == num_courses

# Example
num_courses = 2
prerequisites = [[1, 0]]
print(can_finish(num_courses, prerequisites))  # Output: True
```
**Explanation**: Use topological sort with Kahn’s algorithm to detect cycles in the prerequisite graph.  
**Time Complexity**: O(V + E)  
**Space Complexity**: O(V)

### 67. Pacific Atlantic Water Flow
**Problem**: Find cells where water can flow to both Pacific and Atlantic oceans.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/water-flow-problem/)  
**Solution**:
```python
def pacific_atlantic(heights):
    if not heights:
        return []
    m, n = len(heights), len(heights[0])
    pacific = set()
    atlantic = set()
    
    def dfs(i, j, visited, prev_height):
        if i < 0 or i >= m or j < 0 or j >= n or (i, j) in visited or heights[i][j] < prev_height:
            return
        visited.add((i, j))
        for di, dj in [(0, 1), (1, 0), (0, -1), (-1, 0)]:
            dfs(i + di, j + dj, visited, heights[i][j])
    
    for i in range(m):
        dfs(i, 0, pacific, float('-inf'))
        dfs(i, n - 1, atlantic, float('-inf'))
    for j in range(n):
        dfs(0, j, pacific, float('-inf'))
        dfs(m - 1, j, atlantic, float('-inf'))
    
    return list(pacific & atlantic)

# Example
heights = [[1, 2, 2, 3, 5], [3, 2, 3, 4, 4], [2, 4, 5, 3, 1]]
print(pacific_atlantic(heights))  # Output: [[0, 4], [1, 3], [1, 4], [2, 2], [3, 0], [3, 1], [4, 0]]
```
**Explanation**: Use DFS from Pacific and Atlantic borders to find cells reachable by both.  
**Time Complexity**: O(m*n)  
**Space Complexity**: O(m*n)

### 68. Number of Islands
**Problem**: Count the number of islands in a 2D grid.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/find-number-of-islands/)  
**Solution**:
```python
def num_islands(grid):
    if not grid:
        return 0
    m, n = len(grid), len(grid[0])
    def dfs(i, j):
        if i < 0 or i >= m or j < 0 or j >= n or grid[i][j] != '1':
            return
        grid[i][j] = '#'
        dfs(i + 1, j)
        dfs(i - 1, j)
        dfs(i, j + 1)
        dfs(i, j - 1)
    
    islands = 0
    for i in range(m):
        for j in range(n):
            if grid[i][j] == '1':
                dfs(i, j)
                islands += 1
    return islands

# Example
grid = [
    ["1", "1", "0", "0", "0"],
    ["1", "1", "0", "0", "0"],
    ["0", "0", "1", "0", "0"],
    ["0", "0", "0", "1", "1"]
]
print(num_islands(grid))  # Output: 3
```
**Explanation**: Use DFS to mark connected land cells and count distinct islands.  
**Time Complexity**: O(m*n)  
**Space Complexity**: O(m*n) (recursion stack)

### 69. Alien Dictionary
**Problem**: Find the order of characters in an alien language.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/given-sorted-dictionary-find-precedence-characters/)  
**Solution**:
```python
from collections import defaultdict, deque

def alien_order(words):
    graph = defaultdict(set)
    indegree = {}
    for word in words:
        for char in word:
            indegree[char] = 0
    for i in range(len(words) - 1):
        w1, w2 = words[i], words[i + 1]
        for j in range(len(w1)):
            if j >= len(w2):
                return ""
            if w1[j] != w2[j]:
                if w2[j] not in graph[w1[j]]:
                    graph[w1[j]].add(w2[j])
                    indegree[w2[j]] += 1
                break
    queue = deque([c for c in indegree if indegree[c] == 0])
    result = []
    while queue:
        char = queue.popleft()
        result.append(char)
        for neighbor in graph[char]:
            indegree[neighbor] -= 1
            if indegree[neighbor] == 0:
                queue.append(neighbor)
    return ''.join(result) if len(result) == len(indegree) else ""

# Example
words = ["wrt", "wrf", "er", "ett", "rftt"]
print(alien_order(words))  # Output: "wertf"
```
**Explanation**: Build a graph from word pairs and use topological sort to find character order.  
**Time Complexity**: O(C) (C is total characters)  
**Space Complexity**: O(U) (U is unique characters)

### 70. Word Ladder
**Problem**: Find the shortest transformation sequence from beginWord to endWord.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/word-ladder-length-of-shortest-chain-to-reach-a-target-word/)  
**Solution**:
```python
from collections import deque, defaultdict

def ladder_length(begin_word, end_word, word_list):
    if end_word not in word_list:
        return 0
    word_set = set(word_list)
    queue = deque([(begin_word, 1)])
    while queue:
        word, level = queue.popleft()
        if word == end_word:
            return level
        for i in range(len(word)):
            for c in 'abcdefghijklmnopqrstuvwxyz':
                new_word = word[:i] + c + word[i + 1:]
                if new_word in word_set:
                    word_set.remove(new_word)
                    queue.append((new_word, level + 1))
    return 0

# Example
begin_word = "hit"
end_word = "cog"
word_list = ["hot", "dot", "dog", "lot", "log", "cog"]
print(ladder_length(begin_word, end_word, word_list))  # Output: 5
```
**Explanation**: Use BFS to find the shortest path by transforming one character at a time.  
**Time Complexity**: O(26*N*W) (N is word length, W is number of words)  
**Space Complexity**: O(W)

### 71. Word Ladder II
**Problem**: Find all shortest transformation sequences from beginWord to endWord.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/word-ladder-doublets-word-squares-word-morphing/)  
**Solution**:
```python
from collections import defaultdict, deque

def find_ladders(begin_word, end_word, word_list):
    if end_word not in word_list:
        return []
    word_set = set(word_list)
    level = {begin_word: [[begin_word]]}
    graph = defaultdict(list)
    queue = deque([begin_word])
    seen = {begin_word}
    while queue:
        next_level = defaultdict(list)
        for word in queue:
            if word == end_word:
                continue
            for i in range(len(word)):
                for c in 'abcdefghijklmnopqrstuvwxyz':
                    new_word = word[:i] + c + word[i + 1:]
                    if new_word in word_set:
                        graph[word].append(new_word)
                        if new_word not in seen:
                            next_level[new_word].extend([path + [new_word] for path in level[word]])
                            seen.add(new_word)
        queue = deque(next_level.keys())
        level.update(next_level)
        word_set -= set(next_level.keys())
    return level.get(end_word, [])

# Example
begin_word = "hit"
end_word = "cog"
word_list = ["hot", "dot", "dog", "lot", "log", "cog"]
print(find_ladders(begin_word, end_word, word_list))  
# Output: [["hit", "hot", "dot", "dog", "cog"], ["hit", "hot", "lot", "log", "cog"]]
```
**Explanation**: Use BFS to build a graph and track all shortest paths.  
**Time Complexity**: O(26*N*W)  
**Space Complexity**: O(W*2^W)

### 72. Redundant Connection
**Problem**: Find an edge that can be removed to make a graph a tree.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/find-cycle-in-undirected-graph-using-disjoint-set/)  
**Solution**:
```python
def find_redundant_connection(edges):
    parent = {}
    def find(x):
        if x not in parent:
            parent[x] = x
        if parent[x] != x:
            parent[x] = find(parent[x])
        return parent[x]
    
    def union(x, y):
        parent[find(x)] = find(y)
    
    for u, v in edges:
        if find(u) == find(v):
            return [u, v]
        union(u, v)
    return []

# Example
edges = [[1, 2], [1, 3], [2, 3]]
print(find_redundant_connection(edges))  # Output: [2, 3]
```
**Explanation**: Use Union-Find to detect a cycle, returning the edge causing it.  
**Time Complexity**: O(N*α(N)) (α is inverse Ackermann)  
**Space Complexity**: O(N)

### 73. Evaluate Division
**Problem**: Solve division queries given equations.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/evaluate-division/)  
**Solution**:
```python
from collections import defaultdict

def calc_equation(equations, values, queries):
    graph = defaultdict(dict)
    for (a, b), val in zip(equations, values):
        graph[a][b] = val
        graph[b][a] = 1 / val
    
    def dfs(start, end, visited):
        if start not in graph or end not in graph:
            return -1.0
        if start == end:
            return 1.0
        visited.add(start)
        for neighbor in graph[start]:
            if neighbor not in visited:
                result = dfs(neighbor, end, visited)
                if result != -1.0:
                    return graph[start][neighbor] * result
        return -1.0
    
    return [dfs(a, b, set()) for a, b in queries]

# Example
equations = [["a", "b"], ["b", "c"]]
values = [2.0, 3.0]
queries = [["a", "c"], ["b", "a"]]
print(calc_equation(equations, values, queries))  # Output: [6.0, 0.5]
```
**Explanation**: Build a graph and use DFS to compute division paths.  
**Time Complexity**: O(V*Q) (Q is queries, V is vertices)  
**Space Complexity**: O(V²)

### 74. Shortest Path in Binary Matrix
**Problem**: Find the shortest path from top-left to bottom-right in a binary matrix.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/shortest-path-in-a-binary-maze/)  
**Solution**:
```python
from collections import deque

def shortest_path_binary_matrix(grid):
    if not grid or grid[0][0] == 1:
        return -1
    n = len(grid)
    queue = deque([(0, 0, 1)])
    grid[0][0] = 1
    directions = [(-1, -1), (-1, 0), (-1, 1), (0, -1), (0, 1), (1, -1), (1, 0), (1, 1)]
    while queue:
        i, j, dist = queue.popleft()
        if i == n - 1 and j == n - 1:
            return dist
        for di, dj in directions:
            ni, nj = i + di, j + dj
            if 0 <= ni < n and 0 <= nj < n and grid[ni][nj] == 0:
                grid[ni][nj] = 1
                queue.append((ni, nj, dist + 1))
    return -1

# Example
grid = [[0, 1], [1, 0]]
print(shortest_path_binary_matrix(grid))  # Output: 2
```
**Explanation**: Use BFS to find the shortest path in an 8-directional grid.  
**Time Complexity**: O(n²)  
**Space Complexity**: O(n²)

### 75. Minimum Spanning Tree (Kruskal’s Algorithm)
**Problem**: Find the minimum spanning tree of a graph.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/kruskals-minimum-spanning-tree-algorithm-greedy-algo-2/)  
**Solution**:
```python
def minimum_spanning_tree(n, edges):
    parent = {}
    rank = {}
    def find(x):
        if x not in parent:
            parent[x] = x
            rank[x] = 0
        if parent[x] != x:
            parent[x] = find(parent[x])
        return parent[x]
    
    def union(x, y):
        px, py = find(x), find(y)
        if px == py:
            return
        if rank.get(px, 0) < rank.get(py, 0):
            px, py = py, px
        parent[py] = px
        if rank.get(px, 0) == rank.get(py, 0):
            rank[px] = rank.get(px, 0) + 1
    
    edges.sort(key=lambda x: x[2])
    total_weight = 0
    for u, v, w in edges:
        if find(u) != find(v):
            union(u, v)
            total_weight += w
    return total_weight

# Example
n = 4
edges = [[0, 1, 10], [0, 2, 6], [0, 3, 5], [1, 3, 15], [2, 3, 4]]
print(minimum_spanning_tree(n, edges))  # Output: 19
```
**Explanation**: Use Kruskal’s algorithm with Union-Find to build the MST.  
**Time Complexity**: O(E log E)  
**Space Complexity**: O(V)

### 76. Dijkstra’s Algorithm
**Problem**: Find the shortest path from a source to all vertices.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/dijkstras-shortest-path-algorithm-greedy-algo-7/)  
**Solution**:
```python
from heapq import heappush, heappop
from collections import defaultdict

def dijkstra(n, edges, src):
    graph = defaultdict(list)
    for u, v, w in edges:
        graph[u].append((v, w))
        graph[v].append((u, w))
    
    distances = [float('inf')] * n
    distances[src] = 0
    heap = [(0, src)]
    while heap:
        dist, u = heappop(heap)
        if dist > distances[u]:
            continue
        for v, w in graph[u]:
            if distances[u] + w < distances[v]:
                distances[v] = distances[u] + w
                heappush(heap, (distances[v], v))
    return distances

# Example
n = 4
edges = [[0, 1, 4], [0, 2, 8], [1, 2, 2], [1, 3, 5], [2, 3, 5]]
print(dijkstra(n, edges, 0))  # Output: [0, 4, 6, 9]
```
**Explanation**: Use a min-heap to greedily select the shortest path.  
**Time Complexity**: O((V + E) log V)  
**Space Complexity**: O(V)

### 77. Bellman-Ford Algorithm
**Problem**: Find shortest paths from a source, handling negative weights.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/bellman-ford-algorithm-dp-23/)  
**Solution**:
```python
def bellman_ford(n, edges, src):
    distances = [float('inf')] * n
    distances[src] = 0
    for _ in range(n - 1):
        for u, v, w in edges:
            if distances[u] != float('inf') and distances[u] + w < distances[v]:
                distances[v] = distances[u] + w
    for u, v, w in edges:
        if distances[u] != float('inf') and distances[u] + w < distances[v]:
            return []  # Negative cycle
    return distances

# Example
n = 5
edges = [[0, 1, -1], [0, 2, 4], [1, 2, 3], [1, 3, 2], [1, 4, 2], [3, 2, 5], [3, 1, 1], [4, 3, -3]]
print(bellman_ford(n, edges, 0))  # Output: [0, -1, 2, -2, 1]
```
**Explanation**: Relax edges n-1 times and check for negative cycles.  
**Time Complexity**: O(V*E)  
**Space Complexity**: O(V)

---

## Dynamic Programming (18 Questions)

### 78. Count Ways to Reach the N’th Stair
**Problem**: Count ways to reach the nth stair with 1 or 2 steps.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/count-ways-reach-nth-stair/)  
**Solution**:
```python
def count_ways(n):
    if n <= 1:
        return 1
    dp = [0] * (n + 1)
    dp[0] = dp[1] = 1
    for i in range(2, n + 1):
        dp[i] = dp[i - 1] + dp[i - 2]
    return dp[n]

# Example
n = 4
print(count_ways(n))  # Output: 5
```
**Explanation**: Use DP to compute Fibonacci-like sequence for steps.  
**Time Complexity**: O(n)  
**Space Complexity**: O(n)

### 79. Coin Change
**Problem**: Find the minimum number of coins to make a given amount.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/coin-change-dp-7/)  
**Solution**:
```python
def coin_change(coins, amount):
    dp = [float('inf')] * (amount + 1)
    dp[0] = 0
    for i in range(1, amount + 1):
        for coin in coins:
            if coin <= i:
                dp[i] = min(dp[i], dp[i - coin] + 1)
    return dp[amount] if dp[amount] != float('inf') else -1

# Example
coins = [1, 5, 10, 25]
amount = 30
print(coin_change(coins, amount))  # Output: 3
```
**Explanation**: Use DP to find the minimum coins for each amount up to target.  
**Time Complexity**: O(amount * len(coins))  
**Space Complexity**: O(amount)

### 80. 0/1 Knapsack Problem
**Problem**: Maximize value in a knapsack with weight constraints.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/0-1-knapsack-problem-dp-10/)  
**Solution**:
```python
def knapsack(values, weights, capacity):
    n = len(values)
    dp = [[0] * (capacity + 1) for _ in range(n + 1)]
    for i in range(1, n + 1):
        for w in range(capacity + 1):
            if weights[i - 1] <= w:
                dp[i][w] = max(dp[i - 1][w], dp[i - 1][w - weights[i - 1]] + values[i - 1])
            else:
                dp[i][w] = dp[i - 1][w]
    return dp[n][capacity]

# Example
values = [60, 100, 120]
weights = [10, 20, 30]
capacity = 50
print(knapsack(values, weights, capacity))  # Output: 220
```
**Explanation**: Use 2D DP to decide whether to include each item.  
**Time Complexity**: O(n * capacity)  
**Space Complexity**: O(n * capacity)

### 81. Longest Common Subsequence
**Problem**: Find the length of the longest common subsequence.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/longest-common-subsequence-dp-4/)  
**Solution**:
```python
def longest_common_subsequence(text1, text2):
    m, n = len(text1), len(text2)
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if text1[i - 1] == text2[j - 1]:
                dp[i][j] = dp[i - 1][j - 1] + 1
            else:
                dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])
    return dp[m][n]

# Example
text1 = "ABCDGH"
text2 = "AEDFHR"
print(longest_common_subsequence(text1, text2))  # Output: 3
```
**Explanation**: Use 2D DP to compute the longest common subsequence length.  
**Time Complexity**: O(m*n)  
**Space Complexity**: O(m*n)

### 82. Longest Increasing Subsequence
**Problem**: Find the length of the longest increasing subsequence.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/longest-increasing-subsequence-dp-3/)  
**Solution**:
```python
def length_of_lis(nums):
    if not nums:
        return 0
    dp = [1] * len(nums)
    for i in range(1, len(nums)):
        for j in range(i):
            if nums[i] > nums[j]:
                dp[i] = max(dp[i], dp[j] + 1)
    return max(dp)

# Example
nums = [10, 9, 2, 5, 3, 7, 101, 18]
print(length_of_lis(nums))  # Output: 4
```
**Explanation**: Use DP to track the longest increasing subsequence ending at each index.  
**Time Complexity**: O(n²)  
**Space Complexity**: O(n)

### 83. Edit Distance
**Problem**: Find the minimum operations to transform one string to another.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/edit-distance-dp-5/)  
**Solution**:
```python
def min_distance(word1, word2):
    m, n = len(word1), len(word2)
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    for i in range(m + 1):
        dp[i][0] = i
    for j in range(n + 1):
        dp[0][j] = j
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if word1[i - 1] == word2[j - 1]:
                dp[i][j] = dp[i - 1][j - 1]
            else:
                dp[i][j] = min(dp[i - 1][j - 1], dp[i - 1][j], dp[i][j - 1]) + 1
    return dp[m][n]

# Example
word1 = "horse"
word2 = "ros"
print(min_distance(word1, word2))  # Output: 3
```
**Explanation**: Use 2D DP to compute insert, delete, or replace operations.  
**Time Complexity**: O(m*n)  
**Space Complexity**: O(m*n)

### 84. Regular Expression Matching
**Problem**: Check if a string matches a pattern with wildcards.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/wildcard-pattern-matching/)  
**Solution**:
```python
def is_match(s, p):
    m, n = len(s), len(p)
    dp = [[False] * (n + 1) for _ in range(m + 1)]
    dp[0][0] = True
    for j in range(1, n + 1):
        if p[j - 1] == '*':
            dp[0][j] = dp[0][j - 1]
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if p[j - 1] == '*':
                dp[i][j] = dp[i][j - 1] or dp[i - 1][j]
            elif p[j - 1] == '?' or s[i - 1] == p[j - 1]:
                dp[i][j] = dp[i - 1][j - 1]
    return dp[m][n]

# Example
s = "aa"
p = "a*"
print(is_match(s, p))  # Output: True
```
**Explanation**: Use 2D DP to handle wildcards (‘*’ and ‘?’) in pattern matching.  
**Time Complexity**: O(m*n)  
**Space Complexity**: O(m*n)

### 85. Burst Balloons
**Problem**: Maximize coins by bursting balloons in an array.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/burst-balloon-to-maximize-coins/)  
**Solution**:
```python
def max_coins(nums):
    nums = [1] + nums + [1]
    n = len(nums)
    dp = [[0] * n for _ in range(n)]
    for length in range(2, n):
        for left in range(n - length):
            right = left + length
            for i in range(left + 1, right):
                dp[left][right] = max(dp[left][right], 
                                      nums[left] * nums[i] * nums[right] + dp[left][i] + dp[i][right])
    return dp[0][n - 1]

# Example
nums = [3, 1, 5, 8]
print(max_coins(nums))  # Output: 167
```
**Explanation**: Use 2D DP to compute max coins by bursting balloons in intervals.  
**Time Complexity**: O(n³)  
**Space Complexity**: O(n²)

### 86. Interleaving String
**Problem**: Check if a string is an interleaving of two other strings.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/find-if-a-string-is-interleaved-of-two-other-strings-dp-33/)  
**Solution**:
```python
def is_interleave(s1, s2, s3):
    if len(s1) + len(s2) != len(s3):
        return False
    dp = [[False] * (len(s2) + 1) for _ in range(len(s1) + 1)]
    dp[0][0] = True
    for i in range(1, len(s1) + 1):
        dp[i][0] = dp[i - 1][0] and s1[i - 1] == s3[i - 1]
    for j in range(1, len(s2) + 1):
        dp[0][j] = dp[0][j - 1] and s2[j - 1] == s3[j - 1]
    for i in range(1, len(s1) + 1):
        for j in range(1, len(s2) + 1):
            if s1[i - 1] == s3[i + j - 1]:
                dp[i][j] |= dp[i - 1][j]
            if s2[j - 1] == s3[i + j - 1]:
                dp[i][j] |= dp[i][j - 1]
    return dp[len(s1)][len(s2)]

# Example
s1 = "aabcc"
s2 = "dbbca"
s3 = "aadbbcbcac"
print(is_interleave(s1, s2, s3))  # Output: True
```
**Explanation**: Use 2D DP to check if s3 can be formed by interleaving s1 and s2.  
**Time Complexity**: O(m*n)  
**Space Complexity**: O(m*n)

### 87. Decode Ways
**Problem**: Count the number of ways to decode a string of digits.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/count-possible-decodings-of-a-given-digit-sequence/)  
**Solution**:
```python
def num_decodings(s):
    if not s or s[0] == '0':
        return 0
    dp = [0] * (len(s) + 1)
    dp[0] = 1
    dp[1] = 1
    for i in range(2, len(s) + 1):
        if s[i - 1] != '0':
            dp[i] += dp[i - 1]
        if 10 <= int(s[i - 2:i]) <= 26:
            dp[i] += dp[i - 2]
    return dp[len(s)]

# Example
s = "226"
print(num_decodings(s))  # Output: 3
```
**Explanation**: Use DP to count valid decodings by considering single and double digits.  
**Time Complexity**: O(n)  
**Space Complexity**: O(n)

### 88. Unique Paths
**Problem**: Count unique paths from top-left to bottom-right in a grid.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/count-possible-paths-top-left-bottom-right-nxm-matrix/)  
**Solution**:
```python
def unique_paths(m, n):
    dp = [[1] * n for _ in range(m)]
    for i in range(1, m):
        for j in range(1, n):
            dp[i][j] = dp[i - 1][j] + dp[i][j - 1]
    return dp[m - 1][n - 1]

# Example
m, n = 3, 7
print(unique_paths(m, n))  # Output: 28
```
**Explanation**: Use 2D DP to sum paths from above and left.  
**Time Complexity**: O(m*n)  
**Space Complexity**: O(m*n)

### 89. Unique Paths II
**Problem**: Count unique paths in a grid with obstacles.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/unique-paths-in-a-grid-with-obstacles/)  
**Solution**:
```python
def unique_paths_with_obstacles(obstacle_grid):
    if obstacle_grid[0][0] == 1:
        return 0
    m, n = len(obstacle_grid), len(obstacle_grid[0])
    dp = [[0] * n for _ in range(m)]
    dp[0][0] = 1
    for i in range(m):
        for j in range(n):
            if obstacle_grid[i][j] == 1:
                continue
            if i > 0:
                dp[i][j] += dp[i - 1][j]
            if j > 0:
                dp[i][j] += dp[i][j - 1]
    return dp[m - 1][n - 1]

# Example
obstacle_grid = [[0, 0, 0], [0, 1, 0], [0, 0, 0]]
print(unique_paths_with_obstacles(obstacle_grid))  # Output: 2
```
**Explanation**: Use 2D DP, skipping obstacles and summing valid paths.  
**Time Complexity**: O(m*n)  
**Space Complexity**: O(m*n)

### 90. Palindrome Partitioning
**Problem**: Find the minimum cuts to partition a string into palindromes.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/palindrome-partitioning-dp-17/)  
**Solution**:
```python
def min_palindrome_partition(s):
    n = len(s)
    dp = [float('inf')] * n
    is_pal = [[False] * n for _ in range(n)]
    for i in range(n):
        is_pal[i][i] = True
    for length in range(2, n + 1):
        for start in range(n - length + 1):
            end = start + length - 1
            if length == 2:
                is_pal[start][end] = s[start] == s[end]
            else:
                is_pal[start][end] = s[start] == s[end] and is_pal[start + 1][end - 1]
    dp[0] = 0
    for i in range(n):
        if is_pal[0][i]:
            dp[i] = 0
        else:
            for j in range(i):
                if is_pal[j + 1][i]:
                    dp[i] = min(dp[i], dp[j] + 1)
    return dp[n - 1]

# Example
s = "aab"
print(min_palindrome_partition(s))  # Output: 1
```
**Explanation**: Use DP to find minimum cuts by checking palindromic substrings.  
**Time Complexity**: O(n²)  
**Space Complexity**: O(n²)

### 91. Word Break
**Problem**: Check if a string can be segmented into words from a dictionary.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/word-break-problem-dp-32/)  
**Solution**:
```python
def word_break(s, word_dict):
    word_set = set(word_dict)
    dp = [False] * (len(s) + 1)
    dp[0] = True
    for i in range(1, len(s) + 1):
        for j in range(i):
            if dp[j] and s[j:i] in word_set:
                dp[i] = True
                break
    return dp[len(s)]

# Example
s = "leetcode"
word_dict = ["leet", "code"]
print(word_break(s, word_dict))  # Output: True
```
**Explanation**: Use DP to check if prefixes can be segmented into dictionary words.  
**Time Complexity**: O(n²)  
**Space Complexity**: O(n)

### 92. Minimum Path Sum
**Problem**: Find the minimum path sum from top-left to bottom-right in a grid.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/min-cost-path-dp-6/)  
**Solution**:
```python
def min_path_sum(grid):
    if not grid:
        return 0
    m, n = len(grid), len(grid[0])
    dp = [[0] * n for _ in range(m)]
    dp[0][0] = grid[0][0]
    for i in range(1, m):
        dp[i][0] = dp[i - 1][0] + grid[i][0]
    for j in range(1, n):
        dp[0][j] = dp[0][j - 1] + grid[0][j]
    for i in range(1, m):
        for j in range(1, n):
            dp[i][j] = min(dp[i - 1][j], dp[i][j - 1]) + grid[i][j]
    return dp[m - 1][n - 1]

# Example
grid = [[1, 3, 1], [1, 5, 1], [4, 2, 1]]
print(min_path_sum(grid))  # Output: 7
```
**Explanation**: Use 2D DP to compute the minimum path sum from above or left.  
**Time Complexity**: O(m*n)  
**Space Complexity**: O(m*n)

### 93. House Robber
**Problem**: Maximize the amount robbed without robbing adjacent houses.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/find-maximum-possible-stolen-value-houses/)  
**Solution**:
```python
def rob(nums):
    if not nums:
        return 0
    if len(nums) == 1:
        return nums[0]
    dp = [0] * len(nums)
    dp[0] = nums[0]
    dp[1] = max(nums[0], nums[1])
    for i in range(2, len(nums)):
        dp[i] = max(dp[i - 1], dp[i - 2] + nums[i])
    return dp[-1]

# Example
nums = [2, 7, 9, 3, 1]
print(rob(nums))  # Output: 12
```
**Explanation**: Use DP to choose between robbing the current house or skipping it.  
**Time Complexity**: O(n)  
**Space Complexity**: O(n)

### 94. House Robber II
**Problem**: Maximize amount robbed in a circular arrangement of houses.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/maximum-money-can-robbed-circular-arrangement-houses/)  
**Solution**:
```python
def rob_circle(nums):
    if not nums:
        return 0
    if len(nums) == 1:
        return nums[0]
    def rob_linear(arr):
        if not arr:
            return 0
        if len(arr) == 1:
            return arr[0]
        dp = [0] * len(arr)
        dp[0] = arr[0]
        dp[1] = max(arr[0], arr[1])
        for i in range(2, len(arr)):
            dp[i] = max(dp[i - 1], dp[i - 2] + arr[i])
        return dp[-1]
    
    return max(rob_linear(nums[:-1]), rob_linear(nums[1:]))

# Example
nums = [2, 3, 2]
print(rob_circle(nums))  # Output: 3
```
**Explanation**: Solve for two cases (excluding first or last house) and take the maximum.  
**Time Complexity**: O(n)  
**Space Complexity**: O(n)

### 95. Longest Valid Parentheses
**Problem**: Find the length of the longest valid parentheses substring.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/length-of-the-longest-valid-substring/)  
**Solution**:
```python
def longest_valid_parentheses(s):
    dp = [0] * len(s)
    max_length = 0
    for i in range(1, len(s)):
        if s[i] == ')':
            if s[i - 1] == '(':
                dp[i] = (dp[i - 2] if i >= 2 else 0) + 2
            elif i - dp[i - 1] - 1 >= 0 and s[i - dp[i - 1] - 1] == '(':
                dp[i] = dp[i - 1] + 2 + (dp[i - dp[i - 1] - 2] if i - dp[i - 1] - 2 >= 0 else 0)
            max_length = max(max_length, dp[i])
    return max_length

# Example
s = "(()()"
print(longest_valid_parentheses(s))  # Output: 4
```
**Explanation**: Use DP to track the length of valid parentheses ending at each index.  
**Time Complexity**: O(n)  
**Space Complexity**: O(n)

---

## Bit Manipulations (5 Questions)

### 96. Number of 1 Bits
**Problem**: Count the number of 1 bits in an integer.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/count-set-bits-in-an-integer/)  
**Solution**:
```python
def hamming_weight(n):
    count = 0
    while n:
        count += n & 1
        n >>= 1
    return count

# Example
n = 11  # Binary: 1011
print(hamming_weight(n))  # Output: 3
```
**Explanation**: Use bitwise AND and right shift to count 1 bits.  
**Time Complexity**: O(32) = O(1)  
**Space Complexity**: O(1)

### 97. Counting Bits
**Problem**: Count the number of 1 bits for all numbers up to n.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/count-total-set-bits-in-all-numbers-from-1-to-n/)  
**Solution**:
```python
def count_bits(n):
    dp = [0] * (n + 1)
    for i in range(1, n + 1):
        dp[i] = dp[i >> 1] + (i & 1)
    return dp

# Example
n = 5
print(count_bits(n))  # Output: [0, 1, 1, 2, 1, 2]
```
**Explanation**: Use DP with the fact that i’s bit count is related to i/2 plus the last bit.  
**Time Complexity**: O(n)  
**Space Complexity**: O(n)

### 98. Missing Number
**Problem**: Find the missing number in an array of 0 to n.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/find-the-missing-number/)  
**Solution**:
```python
def missing_number(nums):
    result = len(nums)
    for i in range(len(nums)):
        result ^= i ^ nums[i]
    return result

# Example
nums = [3, 0, 1]
print(missing_number(nums))  # Output: 2
```
**Explanation**: Use XOR to cancel out paired numbers, leaving the missing one.  
**Time Complexity**: O(n)  
**Space Complexity**: O(1)

### 99. Reverse Bits
**Problem**: Reverse the bits of a 32-bit integer.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/reverse-bits/)  
**Solution**:
```python
def reverse_bits(n):
    result = 0
    for _ in range(32):
        result = (result << 1) | (n & 1)
        n >>= 1
    return result

# Example
n = 43261596  # Binary: 00000010100101000001111010011100
print(reverse_bits(n))  # Output: 964176192 (00111001011110000010100101000000)
```
**Explanation**: Shift and build the reversed bits using bitwise operations.  
**Time Complexity**: O(32) = O(1)  
**Space Complexity**: O(1)

### 100. Find XOR of All Subsets
**Problem**: Find the XOR of all subsets of an array.  
**Link**: [GeeksforGeeks](https://www.geeksforgeeks.org/sum-xor-possible-subsets/)  
**Solution**:
```python
def subset_xor_sum(nums):
    if not nums:
        return 0
    result = 0
    for num in nums:
        result |= num
    return result * (1 << (len(nums) - 1))

# Example
nums = [1, 3]
print(subset_xor_sum(nums))  # Output: 8
```
**Explanation**: Each number appears in 2^(n-1) subsets, and the OR of all numbers gives the XOR sum.  
**Time Complexity**: O(n)  
**Space Complexity**: O(1)

---

## How to Use This Resource

- **Study by Topic**: Focus on one topic at a time (e.g., Arrays or Linked Lists) and solve all questions in that category.
- **Practice Regularly**: Aim to solve 2-3 questions daily to build problem-solving skills.
- **Understand Solutions**: After attempting a question, review the provided solution and GeeksforGeeks link for alternative approaches and optimizations.
- **Mock Interviews**: Use platforms like LeetCode or HackerRank to simulate interview conditions and improve coding speed.

## 🌟 Tips for Success

- **Explain Your Approach**: During interviews, articulate your thought process before coding.
- **Handle Edge Cases**: Consider edge cases like empty inputs, single elements, or maximum input sizes.
- **Optimize Solutions**: After solving, explore ways to reduce time or space complexity.
- **Practice Consistently**: Dedicate daily time to coding practice to master DSA.

Happy Coding and Good Luck with Your Interviews! ✨

> “The only way to learn a new programming language is by writing programs in it.” – Dennis Ritchie  
> Start coding, start learning, and let’s conquer DSA! 🚀