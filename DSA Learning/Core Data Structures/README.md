# Core Data Structures

Welcome to the **Core Data Structures** section of your DSA Interview Preparation repository! This README provides detailed explanations of fundamental data structures commonly tested in coding interviews. Each data structure includes a definition, key operations with their time complexities, a Python implementation example, and common interview problems to help you master the concepts.

## Introduction
Data structures are the building blocks of efficient programming, enabling you to store, organize, and manipulate data effectively. For AI/ML freshers, understanding these structures is crucial for cracking technical interviews, even if they’re not part of your daily work. This guide covers the most important data structures, with clear explanations and practical examples to make learning accessible.

---

## 1. Arrays

### Definition
An array is a linear data structure that stores elements of the same type in contiguous memory locations. Elements are accessed using indices, making arrays ideal for quick lookups.

### Key Operations and Time Complexities
- **Access**: O(1) – Direct index-based access.
- **Search**: O(n) – Linear search for an element.
- **Insertion**: O(n) – Requires shifting elements.
- **Deletion**: O(n) – Requires shifting elements.

### Python Example
```python
# Creating an array
arr = [1, 2, 3, 4, 5]

# Accessing an element
print(arr[2])  # Output: 3

# Searching for an element
if 3 in arr:
    print("Found")  # Output: Found

# Insertion
arr.insert(2, 10)  # Insert 10 at index 2
print(arr)  # Output: [1, 2, 10, 3, 4, 5]

# Deletion
arr.pop(2)  # Remove element at index 2
print(arr)  # Output: [1, 2, 3, 4, 5]
```

### Common Interview Problems
- **Two Sum**: Find two numbers that sum to a target ([LeetCode](https://leetcode.com/problems/two-sum/)).
- **Maximum Subarray Sum**: Use Kadane’s algorithm to find the largest sum.
- **Rotate Array**: Rotate elements by k positions.
- **Move Zeros**: Move all zeros to the end of the array.

---

## 2. Linked Lists

### Definition
A linked list is a linear data structure where each element (node) contains data and a reference to the next node. Unlike arrays, linked lists use non-contiguous memory, allowing efficient insertions and deletions.

### Types
- **Singly Linked List**: Each node points to the next.
- **Doubly Linked List**: Nodes point to both next and previous nodes.
- **Circular Linked List**: Last node points to the first.

### Key Operations (Singly Linked List)
- **Insertion at beginning**: O(1)
- **Insertion at end**: O(n)
- **Deletion at beginning**: O(1)
- **Deletion at end**: O(n)
- **Search**: O(n)

### Python Example
```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    def append(self, data):
        new_node = Node(data)
        if not self.head:
            self.head = new_node
            return
        current = self.head
        while current.next:
            current = current.next
        current.next = new_node

    def display(self):
        current = self.head
        while current:
            print(current.data, end=" -> ")
            current = current.next
        print("None")

# Example usage
ll = LinkedList()
ll.append(1)
ll.append(2)
ll.append(3)
ll.display()  # Output: 1 -> 2 -> 3 -> None
```

### Common Interview Problems
- **Reverse Linked List**: Reverse the order of nodes ([LeetCode](https://leetcode.com/problems/reverse-linked-list/)).
- **Detect Cycle**: Check if a cycle exists using Floyd’s algorithm.
- **Merge Two Sorted Lists**: Combine two sorted linked lists.
- **Find Middle**: Locate the middle node using two pointers.

---

## 3. Stacks

### Definition
A stack is a linear data structure that follows the Last In, First Out (LIFO) principle. Elements are added (pushed) and removed (popped) from the top.

### Key Operations
- **Push**: O(1) – Add an element to the top.
- **Pop**: O(1) – Remove the top element.
- **Peek**: O(1) – View the top element.
- **isEmpty**: O(1) – Check if the stack is empty.

### Python Example
```python
class Stack:
    def __init__(self):
        self.items = []

    def push(self, item):
        self.items.append(item)

    def pop(self):
        if not self.is_empty():
            return self.items.pop()
        return None

    def peek(self):
        if not self.is_empty():
            return self.items[-1]
        return None

    def is_empty(self):
        return len(self.items) == 0

# Example usage
stack = Stack()
stack.push(1)
stack.push(2)
print(stack.pop())  # Output: 2
print(stack.peek())  # Output: 1
```

### Common Interview Problems
- **Valid Parentheses**: Check if parentheses are balanced ([LeetCode](https://leetcode.com/problems/valid-parentheses/)).
- **Reverse Polish Notation**: Evaluate expressions in postfix notation.
- **Implement Stack Using Queues**: Use queues to mimic stack behavior.

---

## 4. Queues

### Definition
A queue is a linear data structure that follows the First In, First Out (FIFO) principle. Elements are added (enqueued) at the rear and removed (dequeued) from the front.

### Key Operations
- **Enqueue**: O(1) – Add an element to the rear.
- **Dequeue**: O(1) – Remove the front element.
- **Peek**: O(1) – View the front element.
- **isEmpty**: O(1) – Check if the queue is empty.

### Python Example
```python
class Queue:
    def __init__(self):
        self.items = []

    def enqueue(self, item):
        self.items.append(item)

    def dequeue(self):
        if not self.is_empty():
            return self.items.pop(0)
        return None

    def peek(self):
        if not self.is_empty():
            return self.items[0]
        return None

    def is_empty(self):
        return len(self.items) == 0

# Example usage
queue = Queue()
queue.enqueue(1)
queue.enqueue(2)
print(queue.dequeue())  # Output: 1
print(queue.peek())  # Output: 2
```

### Common Interview Problems
- **Implement Queue Using Stacks**: Use stacks to mimic queue behavior ([LeetCode](https://leetcode.com/problems/implement-queue-using-stacks/)).
- **Sliding Window Maximum**: Find maximum in each window.
- **First Non-Repeating Character**: Find the first unique character in a stream.

---

## 5. Hash Tables

### Definition
A hash table (or hash map) stores key-value pairs and uses a hash function to compute an index for fast insertion, deletion, and lookup. Collisions are handled using techniques like chaining.

### Key Operations
- **Insert**: O(1) average
- **Delete**: O(1) average
- **Search**: O(1) average
- **Space**: O(n)

### Python Example
```python
class HashTable:
    def __init__(self):
        self.size = 10
        self.table = [[] for _ in range(self.size)]

    def _hash(self, key):
        return hash(key) % self.size

    def insert(self, key, value):
        h = self._hash(key)
        for pair in self.table[h]:
            if pair[0] == key:
                pair[1] = value
                return
        self.table[h].append([key, value])

    def get(self, key):
        h = self._hash(key)
        for pair in self.table[h]:
            if pair[0] == key:
                return pair[1]
        return None

# Example usage
ht = HashTable()
ht.insert("name", "Alice")
print(ht.get("name"))  # Output: Alice
```

### Common Interview Problems
- **Design a HashMap**: Implement a hash map from scratch ([LeetCode](https://leetcode.com/problems/design-hashmap/)).
- **Two Sum**: Use a hash table to find pairs summing to a target.
- **Group Anagrams**: Group strings that are anagrams.

---

## 6. Trees

### Definition
A tree is a non-linear data structure with a hierarchical structure of nodes, where each node has zero or more child nodes. The top node is the root, and nodes with no children are leaves.

### Types
- **Binary Tree**: Each node has at most two children.
- **Binary Search Tree (BST)**: Left subtree has smaller values, right has larger.
- **AVL Tree**: Self-balancing BST.

### Key Operations (BST)
- **Insert**: O(log n) average
- **Search**: O(log n) average
- **Delete**: O(log n) average

### Python Example (BST)
```python
class Node:
    def __init__(self, key):
        self.left = None
        self.right = None
        self.val = key

def insert(root, key):
    if root is None:
        return Node(key)
    else:
        if root.val < key:
            root.right = insert(root.right, key)
        else:
            root.left = insert(root.left, key)
    return root

def inorder(root):
    if root:
        inorder(root.left)
        print(root.val, end=" ")
        inorder(root.right)

# Example usage
root = None
root = insert(root, 50)
insert(root, 30)
insert(root, 20)
insert(root, 40)
insert(root, 70)
inorder(root)  # Output: 20 30 40 50 70
```

### Common Interview Problems
- **Validate BST**: Check if a tree is a valid BST ([LeetCode](https://leetcode.com/problems/validate-binary-search-tree/)).
- **Lowest Common Ancestor**: Find the LCA in a binary tree.
- **Serialize/Deserialize Tree**: Convert tree to/from string.

---

## 7. Heaps

### Definition
A heap is a complete binary tree that satisfies the heap property: in a max heap, each node’s value is greater than or equal to its children; in a min heap, it’s smaller.

### Key Operations
- **Insert**: O(log n)
- **Delete**: O(log n)
- **Extract Max/Min**: O(log n)

### Python Example (Max Heap)
```python
import heapq

# Creating a max heap
heap = []
heapq.heappush(heap, -1)  # Use negative for max heap
heapq.heappush(heap, -3)
heapq.heappush(heap, -2)
print(heapq.heappop(heap))  # Output: -3 (max value)
```

### Common Interview Problems
- **Kth Largest Element**: Find the kth largest element in an unsorted array ([LeetCode](https://leetcode.com/problems/kth-largest-element-in-an-array/)).
- **Merge K Sorted Lists**: Merge k sorted lists into one sorted list.
- **Top K Frequent Elements**: Find the top k frequent elements in an array.

---

## 8. Graphs

### Definition
A graph is a non-linear data structure consisting of nodes (vertices) connected by edges. Graphs can be directed or undirected and may be weighted or unweighted.

### Representations
- **Adjacency List**: List of lists or dictionary where each index/key represents a vertex and its value is a list of connected vertices.
- **Adjacency Matrix**: 2D matrix where rows and columns represent vertices, and entries indicate edges.

### Key Operations
- **Traversal**: DFS (Depth-First Search), BFS (Breadth-First Search)
- **Shortest Path**: Dijkstra’s, Bellman-Ford
- **Minimum Spanning Tree**: Kruskal’s, Prim’s

### Python Example (Adjacency List)
```python
class Graph:
    def __init__(self):
        self.graph = {}

    def add_edge(self, u, v):
        if u in self.graph:
            self.graph[u].append(v)
        else:
            self.graph[u] = [v]

    def dfs(self, start, visited=None):
        if visited is None:
            visited = set()
        visited.add(start)
        print(start, end=' ')
        for neighbor in self.graph.get(start, []):
            if neighbor not in visited:
                self.dfs(neighbor, visited)

# Example usage
g = Graph()
g.add_edge(0, 1)
g.add_edge(0, 2)
g.add_edge(1, 2)
g.add_edge(2, 0)
g.add_edge(2, 3)
g.add_edge(3, 3)
g.dfs(2)  # Output: 2 0 1 3
```

### Common Interview Problems
- **Number of Islands**: Count islands in a 2D grid ([LeetCode](https://leetcode.com/problems/number-of-islands/)).
- **Course Schedule**: Detect cycle in a graph (course prerequisites).
- **Word Ladder**: Find the shortest transformation sequence from beginWord to endWord.

---

## 9. Tries

### Definition
A trie (prefix tree) is a tree-like data structure used to store a dynamic set of strings. Each node represents a prefix, and edges represent the next character.

### Key Operations
- **Insert**: O(m), where m is the length of the string
- **Search**: O(m)
- **Delete**: O(m)

### Python Example
```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.is_end_of_word = False

class Trie:
    def __init__(self):
        self.root = TrieNode()

    def insert(self, word):
        node = self.root
        for char in word:
            if char not in node.children:
                node.children[char] = TrieNode()
            node = node.children[char]
        node.is_end_of_word = True

    def search(self, word):
        node = self.root
        for char in word:
            if char not in node.children:
                return False
            node = node.children[char]
        return node.is_end_of_word

# Example usage
trie = Trie()
trie.insert("hello")
print(trie.search("hello"))  # Output: True
print(trie.search("hell"))   # Output: False
```

### Common Interview Problems
- **Implement Trie (Prefix Tree)**: Design a trie with insert, search, and startsWith methods ([LeetCode](https://leetcode.com/problems/implement-trie-prefix-tree/)).
- **Word Search II**: Find all words in a 2D grid that exist in a trie.
- **Design Add and Search Words Data Structure**: Implement a word dictionary with addWord and search methods.