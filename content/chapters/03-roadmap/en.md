# Chapter 3: Learning Roadmap for Algorithms & Data Structures

[Tiếng Việt](index.md)

## Overview of the Learning Roadmap

The roadmap is divided into key topics and techniques to help you build a solid foundation for mastering programming problems and technical interviews:

---

### 1. Basic Data Structures

**Array**
- **Definition:** An array is a data structure that stores elements in contiguous memory, allowing direct access by index.
- **Pros:** O(1) random access, simple, memory efficient.
- **Cons:** Fixed size, inserting/deleting in the middle is O(n).
- **When to use?**
  - When you need fast index-based access.
  - When the number of elements is known or rarely changes.
  - When working with sequences, character arrays, or continuous data.
- **Example:**
```python
arr = [1, 2, 3, 4, 5]
print(arr[2])  # 3
arr.append(6)  # Add to end
arr.pop(1)     # Remove at index 1
```

**String**
- **Definition:** A string is a sequence of characters, used to store and process text.
- **Pros:** Supports many operations (slice, join, search, compare), easy to use.
- **Cons:** Immutable, concatenating many large strings can be inefficient.
- **When to use?**
  - When storing or processing text or character data.
  - When solving substring, reverse, search, or pattern matching problems.
- **Example:**
```python
s = "hello"
print(s[::-1])  # Reverse: 'olleh'
print("ell" in s)  # True
```

**Two Pointers**
- **Definition:** Use two pointers to traverse arrays/strings, often for finding pairs, subarrays, or reversing.
- **Pros:** Optimizes time, reduces complexity from O(n^2) to O(n), easy to implement.
- **Cons:** Only applies to problems with suitable properties (sorted arrays, continuous substrings).
- **When to use?**
  - When finding pairs, continuous subarrays, or processing continuous data.
  - When optimizing nested loops.
- **Example:**
```python
# Reverse array with two pointers
arr = [1,2,3,4,5]
l, r = 0, len(arr)-1
while l < r:
    arr[l], arr[r] = arr[r], arr[l]
    l += 1
    r -= 1
print(arr)
```

**Sliding Window**
- **Definition:** A technique using a moving window on arrays/strings to solve subarray/substring problems.
- **Pros:** Optimizes for sum, length, or frequency problems, reduces complexity from O(n^2) to O(n).
- **Cons:** Only applies to problems with continuous segments.
- **When to use?**
  - When finding subarrays/substrings with optimal sum/length/frequency.
- **Example:**
```python
# Max sum of subarray of length k
arr = [1,3,-1,-3,5,3,6,7]
k = 3
max_sum = sum(arr[:k])
cur_sum = max_sum
for i in range(k, len(arr)):
    cur_sum += arr[i] - arr[i-k]
    max_sum = max(max_sum, cur_sum)
print(max_sum)
```

**String Processing**
- **Definition:** Includes reversing, substring search, palindrome check, etc.
- **Pros:** Easy to use, many built-in Python functions.
- **Cons:** Some complex operations can be slow if not optimized.
- **When to use?**
  - When checking substrings, reversing, palindrome, or text processing.
- **Example:**
```python
# Palindrome check
s = "abccba"
print(s == s[::-1])  # True
# Substring check
print("abc" in "abcdef")  # True
```

---

### 2. Stack, Queue, Set, Map, Deque

**Stack**
- **Definition:** LIFO (Last In First Out) structure, only allows push/pop at one end (the top).
- **Pros:** Easy to implement, O(1) operations, useful for tree traversal, parentheses checking, undo/redo.
- **Cons:** No random access, can cause stack overflow with deep recursion.
- **When to use?**
  - When storing temporary states (tree traversal, backtracking).
  - When solving parentheses, undo/redo, backtracking problems.
- **Example:**
```python
stack = []
stack.append(1)
stack.append(2)
print(stack.pop())  # 2
```

**Queue**
- **Definition:** FIFO (First In First Out) structure, add at end and remove from front.
- **Pros:** Process management, BFS, buffering, O(1) with deque.
- **Cons:** No random access.
- **When to use?**
  - When processing data in arrival order (BFS, queues, buffers).
  - When managing tasks, processes, or streaming data.
- **Example:**
```python
from collections import deque
q = deque()
q.append(1)
q.append(2)
print(q.popleft())  # 1
```

**Set**
- **Definition:** Stores unique elements, ignores order.
- **Pros:** O(1) add/remove/check, easy duplicate removal.
- **Cons:** No index access, no order.
- **When to use?**
  - When you need fast existence checks.
  - When removing duplicates from a list.
- **Example:**
```python
s = set()
s.add(1)
s.add(2)
s.add(1)  # No duplicate
print(2 in s)  # True
lst = [1,2,2,3]
unique = set(lst)  # {1,2,3}
```

**Map (Dictionary, Hash Table)**
- **Definition:** Stores key-value pairs, can be nested (2D hashmap).
- **Pros:** O(1) access, add, remove; flexible key types.
- **Cons:** Can use more memory for complex keys, unordered before Python 3.7.
- **When to use?**
  - When storing tabular or multi-dimensional data (matrix, frequency by pair).
  - When fast multi-key access is needed.
- **Example:**
```python
from collections import defaultdict
d = defaultdict(dict)
d['a']['x'] = 1
d['a']['y'] = 2
d['b']['x'] = 3
print(d['a']['y'])  # 2
```

**Deque (Double-ended Queue)**
- **Definition:** Queue that allows O(1) add/remove at both ends.
- **Pros:** Useful for sliding window, double-ended queue, fast head/tail operations.
- **Cons:** No random access.
- **When to use?**
  - When you need to operate at both ends (sliding window, double-ended queue, advanced undo/redo).
  - When optimizing sliding window max/min.
- **Example:**
```python
from collections import deque
dq = deque([1,2,3])
dq.appendleft(0)  # Add to front
dq.append(4)      # Add to end
print(dq.pop())   # 4
print(dq.popleft()) # 0
```

**Hash Table (Dictionary)**
- **Definition:** Stores key-value pairs, allows O(1) average access, add, remove.
- **Pros:** Fast access, efficient existence check, key-value mapping.
- **Cons:** Possible hash collisions, unordered.
- **When to use?**
  - When storing mappings, counting frequency, fast existence check.
  - When solving frequency, duplicate, position, or 2D hashmap problems.
- **Example:**
```python
d = {}
d['a'] = 1
d['b'] = 2
print(d.get('a'))  # 1
from collections import Counter
s = "leetcode"
cnt = Counter(s)
# cnt = {'l':1, 'e':3, 't':1, 'c':1, 'o':1, 'd':1}
```

---

### 3. Recursion & Backtracking

**Recursion**
- **Definition:** A function calls itself to solve a problem by breaking it into subproblems.
- **Pros:** Concise code, natural for divide-and-conquer (trees, sequences, combinations).
- **Cons:** Can cause stack overflow if not careful, inefficient if not optimized (repeated calculations).
- **When to use?**
  - When the problem can be broken into similar subproblems (trees, sequences, combinations, pathfinding).
  - When traversing hierarchical structures (trees, graphs).
- **Example:**
```python
# Factorial with recursion
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n-1)
print(factorial(5))  # 120
```

**Backtracking**
- **Definition:** Try all possibilities, backtrack if a condition is not met; used for generating combinations, permutations, solving sudoku, n-queens.
- **Pros:** Solves combinatorial problems, finds all solutions, generates configurations.
- **Cons:** High complexity (often O(2^n) or more), can be slow if not pruned.
- **When to use?**
  - When listing all valid configurations (subsets, permutations, combination sum, sudoku, n-queens).
  - When no general formula exists, need to try all cases.
- **Example:**
```python
# Generate all subsets with backtracking
res = []
def backtrack(start, path):
    res.append(path[:])
    for i in range(start, len(nums)):
        path.append(nums[i])
        backtrack(i+1, path)
        path.pop()
nums = [1,2,3]
backtrack(0,[])
print(res)
```

---

### 4. Searching & Sorting

**Binary Search**
- **Definition:** Search on a sorted array by repeatedly dividing the search range in half.
- **Pros:** Very fast (O(log n)), easy to implement, efficient for large sorted data.
- **Cons:** Only works on sorted arrays, not suitable for frequently changing data.
- **When to use?**
  - When searching quickly on sorted arrays/lists.
  - When solving optimization problems (binary search on answer).
- **Example:**
```python
arr = [1,3,5,7,9]
target = 5
l, r = 0, len(arr)-1
while l <= r:
    m = (l+r)//2
    if arr[m] == target:
        print(m)
        break
    elif arr[m] < target:
        l = m+1
    else:
        r = m-1
```

**Merge Sort**
- **Definition:** Divide-and-conquer sorting algorithm, splits array into small parts and merges them in order.
- **Pros:** Stable O(n log n) complexity, not affected by input order, good for large data.
- **Cons:** Uses O(n) extra memory, more complex than Bubble Sort.
- **When to use?**
  - When stable sorting is needed, large data, extra memory is not a concern.
  - When sorting complex data structures.
- **Example:**
```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
    mid = len(arr)//2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    res = []
    i = j = 0
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            res.append(left[i])
            i += 1
        else:
            res.append(right[j])
            j += 1
    res.extend(left[i:])
    res.extend(right[j:])
    return res
arr = [5,2,4,6,1,3]
print(merge_sort(arr))
```

**Quick Sort**
- **Definition:** Divide-and-conquer sorting algorithm, picks a pivot and partitions the array into smaller/larger parts.
- **Pros:** Very fast on average (O(n log n)), little extra memory, simple implementation.
- **Cons:** Worst case O(n^2) if pivot is bad, not stable.
- **When to use?**
  - When fast sorting is needed, stability is not required, memory is limited.
  - When data is not already sorted or reversed.
- **Example:**
```python
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr)//2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quick_sort(left) + middle + quick_sort(right)
arr = [3,6,8,10,1,2,1]
print(quick_sort(arr))
```

**Heap (Priority Queue)**
- **Definition:** Special binary tree structure, always keeps the largest (max-heap) or smallest (min-heap) at the root. Priority Queue is a queue based on heap.
- **Pros:** O(1) get min/max, O(log n) add/remove, used for top-k, median, Dijkstra.
- **Cons:** No random access, not fully ordered.
- **When to use?**
  - When you need to get/store the largest/smallest element repeatedly (top-k, median, heap sort, Dijkstra).
  - When managing a priority queue.
- **Example:**
```python
import heapq
arr = [3,1,4,1,5,9]
heapq.heapify(arr)
print(heapq.heappop(arr))  # 1 (min-heap)
heapq.heappush(arr, 2)
print(heapq.nsmallest(3, arr))  # 3 smallest elements
```

---

### 5. Graphs

**BFS (Breadth-First Search)**
- **Definition:** Traverses a graph/grid level by level, visiting the closest nodes first.
- **Pros:** Finds shortest path in unweighted graphs, easy to implement with queue.
- **Cons:** Uses a lot of memory for large graphs, not suitable for weighted graphs.
- **When to use?**
  - When finding shortest path in unweighted graphs/grids.
  - When level order traversal is needed.
- **Example:**
```python
from collections import deque
graph = {0:[1,2], 1:[0,3], 2:[0], 3:[1]}
visited = set()
q = deque([0])
while q:
    node = q.popleft()
    if node in visited: continue
    visited.add(node)
    for nei in graph[node]:
        if nei not in visited:
            q.append(nei)
```

**DFS (Depth-First Search)**
- **Definition:** Traverses a graph/grid as deep as possible before backtracking.
- **Pros:** Easy to implement with recursion or stack, used for cycle check, connected components.
- **Cons:** Can cause stack overflow for large graphs, does not guarantee shortest path.
- **When to use?**
  - When traversing the whole graph, checking cycles, connected components.
  - When solving backtracking problems on graphs/grids.
- **Example:**
```python
graph = {0:[1,2], 1:[0,3], 2:[0], 3:[1]}
visited = set()
def dfs(u):
    if u in visited: return
    visited.add(u)
    for v in graph[u]:
        dfs(v)
dfs(0)
```

**Topological Sort**
- **Definition:** Sorts the nodes of a directed acyclic graph (DAG) so that for every edge u→v, u comes before v.
- **Pros:** Determines task order, checks for cycles in DAG.
- **Cons:** Only applies to DAGs, not for graphs with cycles.
- **When to use?**
  - When determining task order with dependencies.
  - When checking for cycles in a graph.
- **Example (Kahn's algorithm):**
```python
from collections import deque, defaultdict
graph = {0:[1,2], 1:[3], 2:[3], 3:[]}
indegree = defaultdict(int)
for u in graph:
    for v in graph[u]:
        indegree[v] += 1
q = deque([u for u in graph if indegree[u]==0])
order = []
while q:
    u = q.popleft()
    order.append(u)
    for v in graph[u]:
        indegree[v] -= 1
        if indegree[v] == 0:
            q.append(v)
print(order)
```

**Dijkstra (Shortest Path in Weighted Graphs)**
- **Definition:** Finds the shortest path from one node to others in a graph with positive weights.
- **Pros:** Efficient for sparse graphs with positive weights, uses heap for optimization.
- **Cons:** Not for negative weights, more complex than BFS.
- **When to use?**
  - When finding shortest path in weighted graphs with positive weights.
  - When solving network, optimal path problems.
- **Example:**
```python
import heapq
graph = {0:[(1,2),(2,4)], 1:[(3,1)], 2:[(3,1)], 3:[]}
dist = {u:float('inf') for u in graph}
dist[0] = 0
pq = [(0,0)]
while pq:
    d,u = heapq.heappop(pq)
    if d > dist[u]: continue
    for v,w in graph[u]:
        if dist[v] > d+w:
            dist[v] = d+w
            heapq.heappush(pq, (dist[v], v))
print(dist)
```

**Union-Find (Disjoint Set Union - DSU)**
- **Definition:** DSU manages disjoint sets, supports union and find operations.
- **Pros:** O(α(n)) union/find, used for connected components, Kruskal's algorithm.
- **Cons:** Cannot list all elements in a set, only checks representatives.
- **When to use?**
  - When managing dynamic groups/sets (connected components, cycle check, MST).
  - When solving network, undirected graph problems.
- **Example:**
```python
class DSU:
    def __init__(self, n):
        self.parent = list(range(n))
    def find(self, x):
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])
        return self.parent[x]
    def union(self, x, y):
        self.parent[self.find(x)] = self.find(y)
dsu = DSU(5)
dsu.union(0,1)
dsu.union(3,4)
print(dsu.find(0) == dsu.find(1))  # True
```

**Minimum Spanning Tree (Kruskal, Prim)**
- **Definition:** MST is a tree connecting all nodes with the minimum total weight. Kruskal uses DSU, Prim uses heap.
- **Pros:** Finds optimal network connections, used in network, electricity, transportation design.
- **Cons:** Only for connected graphs, complex for large graphs.
- **When to use?**
  - When connecting points optimally (network, roads).
  - When solving connection optimization problems.
- **Example (Kruskal):**
```python
edges = [(1,0,1),(2,1,2),(3,0,2)]  # (weight, u, v)
parent = [i for i in range(3)]
def find(x):
    if parent[x]!=x:
        parent[x]=find(parent[x])
    return parent[x]
res = 0
for w,u,v in sorted(edges):
    if find(u)!=find(v):
        res += w
        parent[find(u)] = find(v)
print(res)
```

---

### 6. Dynamic Programming (DP)

**1D DP**
- **Definition:** Store results of subproblems in a 1D array to avoid repeated calculations.
- **Pros:** Optimizes time for repetitive problems, easy for sequence problems.
- **Cons:** Uses O(n) memory, sometimes hard to define states.
- **When to use?**
  - When the problem can be broken into independent subproblems, and the result depends on smaller subproblems.
  - When solving sequence, optimization, or counting problems.
- **Example:**
```python
# Climbing Stairs
n = 5
dp = [0]*(n+1)
dp[0] = dp[1] = 1
for i in range(2, n+1):
    dp[i] = dp[i-1] + dp[i-2]
print(dp[n])
```

**2D DP**
- **Definition:** Store results of subproblems in a 2D matrix, often for string, grid, or knapsack problems.
- **Pros:** Solves more complex problems like LCS, edit distance, knapsack.
- **Cons:** Uses O(n*m) memory, more complex than 1D DP.
- **When to use?**
  - When the problem state depends on two variables (position, weight, two string lengths).
  - When solving string, grid, or knapsack problems.
- **Example:**
```python
# LCS (Longest Common Subsequence)
s1, s2 = "abcde", "ace"
dp = [[0]*(len(s2)+1) for _ in range(len(s1)+1)]
for i in range(1, len(s1)+1):
    for j in range(1, len(s2)+1):
        if s1[i-1] == s2[j-1]:
            dp[i][j] = dp[i-1][j-1]+1
        else:
            dp[i][j] = max(dp[i-1][j], dp[i][j-1])
print(dp[-1][-1])  # 3
```

**Advanced DP (Bitmask, State Optimization)**
- **Definition:** Optimize DP state with bitmask, sliding window, prefix sum, memoization to reduce memory/time.
- **Pros:** Solves large combinatorial problems, optimizes performance for multi-dimensional DP.
- **Cons:** Requires good state design, more complex implementation.
- **When to use?**
  - When there are many states but can be encoded with bitmask or optimized with prefix sum, sliding window.
  - When solving combinatorial, optimization, or set-based DP problems.
- **Example:**
```python
# DP + Bitmask: Basic Traveling Salesman Problem (TSP)
n = 4
cost = [[0,1,15,6],[2,0,7,3],[9,6,0,12],[10,4,8,0]]
INF = float('inf')
dp = [[INF]*n for _ in range(1<<n)]
dp[1][0] = 0
for mask in range(1<<n):
    for u in range(n):
        if not (mask & (1<<u)): continue
        for v in range(n):
            if mask & (1<<v): continue
            dp[mask|(1<<v)][v] = min(dp[mask|(1<<v)][v], dp[mask][u]+cost[u][v])
print(min(dp[(1<<n)-1][i] for i in range(n)))
```

---

### 7. Trees

**Tree Traversal (Pre/In/Post-order)**
- **Definition:** Visit all nodes of a binary tree in a specific order: before (pre), between (in), or after (post) the root.
- **Pros:** Easy to implement with recursion or stack, used for many tree analysis problems.
- **Cons:** Can cause stack overflow for deep trees if using recursion.
- **When to use?**
  - When processing, printing, or analyzing binary tree structure.
  - When solving aggregation, search, or property check problems.
- **Example:**
```python
# In-order traversal
res = []
def inorder(root):
    if not root: return
    inorder(root.left)
    res.append(root.val)
    inorder(root.right)
```

**Binary Search Tree (BST)**
- **Definition:** A binary tree where for each node, all nodes on the left are smaller, all on the right are larger.
- **Pros:** O(log n) search, insert, delete if balanced, easy to implement.
- **Cons:** If unbalanced, can degrade to O(n).
- **When to use?**
  - When storing ordered data, fast search, insert, delete.
  - When solving dynamic sequence, simple range query problems.
- **Example:**
```python
class Node:
    def __init__(self, val):
        self.val = val
        self.left = self.right = None
# Insert node into BST
def insert(root, val):
    if not root: return Node(val)
    if val < root.val:
        root.left = insert(root.left, val)
    else:
        root.right = insert(root.right, val)
    return root
```

**Lowest Common Ancestor (LCA)**
- **Definition:** The lowest node that is an ancestor of two nodes in a tree.
- **Pros:** Fast ancestor queries, useful in tree analysis, hierarchy systems.
- **Cons:** Needs extra implementation if tree has no parent pointer.
- **When to use?**
  - When finding common relationships between two nodes in a tree.
  - When solving hierarchy, ancestor query problems.
- **Example:**
```python
def lca(root, p, q):
    if not root or root==p or root==q: return root
    left = lca(root.left, p, q)
    right = lca(root.right, p, q)
    if left and right: return root
    return left or right
```

**Segment Tree**
- **Definition:** A binary tree structure for efficient range query and update on arrays.
- **Pros:** O(log n) range query and update, supports many queries (sum, min, max).
- **Cons:** Complex to implement, uses O(n) memory.
- **When to use?**
  - When you need to query/update ranges on dynamic arrays.
  - When solving range query, advanced DP problems.
- **Example:**
```python
class SegmentTree:
    def __init__(self, arr):
        self.n = len(arr)
        self.tree = [0]*(2*self.n)
        for i in range(self.n):
            self.tree[self.n+i] = arr[i]
        for i in range(self.n-1,0,-1):
            self.tree[i] = self.tree[2*i] + self.tree[2*i+1]
    def query(self, l, r):
        res = 0
        l += self.n; r += self.n
        while l < r:
            if l%2:
                res += self.tree[l]
                l += 1
            if r%2:
                r -= 1
                res += self.tree[r]
            l //= 2; r //= 2
        return res
arr = [1,3,5,7,9,11]
st = SegmentTree(arr)
print(st.query(1,4))  # Sum from arr[1] to arr[3]
```

**Fenwick Tree (Binary Indexed Tree - BIT)**
- **Definition:** A binary tree structure for efficient prefix sum and update, more memory efficient than Segment Tree.
- **Pros:** O(log n) prefix sum and update, simpler than Segment Tree, less memory.
- **Cons:** Only supports some queries (sum, min/max not as flexible as Segment Tree).
- **When to use?**
  - When you need prefix sum/range update on dynamic arrays, memory is a concern.
  - When solving prefix sum, inversion count problems.
- **Example:**
```python
class FenwickTree:
    def __init__(self, n):
        self.n = n
        self.tree = [0]*(n+1)
    def update(self, i, delta):
        while i <= self.n:
            self.tree[i] += delta
            i += i & -i
    def query(self, i):
        res = 0
        while i > 0:
            res += self.tree[i]
            i -= i & -i
        return res
ft = FenwickTree(6)
for idx, val in enumerate([1,3,5,7,9,11],1):
    ft.update(idx, val)
print(ft.query(3))  # Sum from 1 to 3
```

---

### 8. Other Techniques

**Greedy**
- **Definition:** Always choose the locally optimal solution at each step, hoping for a global optimum.
- **Pros:** Simple, fast, no state storage.
- **Cons:** Not always optimal, needs proof of correctness.
- **When to use?**
  - When the problem is optimizable and greedy can be proven correct (activity selection, Huffman, Jump Game).
- **Example:**
```python
# Interval Scheduling
intervals = [(1,3),(2,4),(3,5)]
intervals.sort(key=lambda x: x[1])
res, end = 0, -float('inf')
for s,e in intervals:
    if s >= end:
        res += 1
        end = e
print(res)
```

**Sliding Window**
- **Definition:** Use a moving window on arrays/strings to solve subarray/substring problems.
- **Pros:** Optimizes for sum, length, frequency, reduces complexity from O(n^2) to O(n).
- **Cons:** Only for continuous segment problems.
- **When to use?**
  - When finding subarrays/substrings with optimal sum/length/frequency.
- **Example:**
```python
arr = [1,3,-1,-3,5,3,6,7]
k = 3
max_sum = sum(arr[:k])
cur_sum = max_sum
for i in range(k, len(arr)):
    cur_sum += arr[i] - arr[i-k]
    max_sum = max(max_sum, cur_sum)
print(max_sum)
```

**Prefix Sum / Difference Array**
- **Definition:** Prefix sum is a cumulative sum array, difference array is for fast range updates.
- **Pros:** O(1) range sum, fast range updates, reduces complexity for many problems.
- **Cons:** Only for addition/subtraction, not for complex operations.
- **When to use?**
  - When you need to compute range sums or update ranges frequently.
- **Example:**
```python
arr = [1,2,3,4,5]
prefix = [0]*(len(arr)+1)
for i in range(len(arr)):
    prefix[i+1] = prefix[i] + arr[i]
print(prefix[3]-prefix[1])  # Sum from arr[1] to arr[2]
```

**Bit Manipulation**
- **Definition:** Directly operate on the binary bits of integers for speed/memory optimization.
- **Pros:** Very fast, memory efficient, solves special problems (mask, XOR, bit check).
- **Cons:** Code is hard to read, easy to make mistakes.
- **When to use?**
  - When checking, setting, flipping bits, or solving combinatorial/state problems.
- **Example:**
```python
n, k = 10, 2
print((n >> k) & 1)  # 1 if k-th bit is 1
print(5 ^ 3)  # 6
```

**Trie**
- **Definition:** A tree for storing a set of strings, supports fast prefix search.
- **Pros:** O(L) search/insert/check for prefix, useful for dictionary, autocomplete.
- **Cons:** Uses more memory for many long strings, more complex than set/map.
- **When to use?**
  - When checking, storing, searching prefixes, dictionary, autocomplete.
- **Example:**
```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.is_end = False
class Trie:
    def __init__(self):
        self.root = TrieNode()
    def insert(self, word):
        node = self.root
        for c in word:
            if c not in node.children:
                node.children[c] = TrieNode()
            node = node.children[c]
        node.is_end = True
    def search(self, word):
        node = self.root
        for c in word:
            if c not in node.children:
                return False
            node = node.children[c]
        return node.is_end
trie = Trie()
trie.insert("hello")
print(trie.search("hello"))  # True
```

**Two Pointers**
- **Definition:** Use two pointers to traverse arrays/strings, often for finding pairs, subarrays, or reversing.
- **Pros:** Optimizes time, reduces complexity from O(n^2) to O(n), easy to implement.
- **Cons:** Only applies to problems with suitable properties (sorted arrays, continuous substrings).
- **When to use?**
  - When finding pairs, continuous subarrays, or processing continuous data.
  - When optimizing nested loops.
- **Example:**
```python
arr = [1,2,3,4,5]
l, r = 0, len(arr)-1
while l < r:
    arr[l], arr[r] = arr[r], arr[l]
    l += 1
    r -= 1
print(arr)
```

---

### 9. Advanced Techniques

**Monotonic Stack/Queue**
- **Definition:** Stack/queue that only keeps increasing/decreasing elements, used for next greater/smaller element, sliding window max/min.
- **Pros:** Optimizes O(n^2) problems to O(n), easy to implement with stack/queue.
- **Cons:** Only for problems with monotonic properties.
- **When to use?**
  - When finding next greater/smaller element to the left/right, sliding window max/min.
- **Example:**
```python
nums = [2,1,2,4,3]
stack, res = [], [-1]*len(nums)
for i in range(len(nums)):
    while stack and nums[i] > nums[stack[-1]]:
        res[stack.pop()] = nums[i]
    stack.append(i)
print(res)
```

**Line Sweep / Event Sorting**
- **Definition:** Process events in order (often by x-axis), used for interval intersection, calendar, skyline problems.
- **Pros:** Efficient for geometry, calendar, intersection problems.
- **Cons:** Needs event sorting logic, more complex than normal traversal.
- **When to use?**
  - When processing events in order, intersection, calendar, skyline problems.
- **Example:**
```python
intervals = [(1,4),(2,5),(7,9)]
events = []
for s,e in intervals:
    events.append((s,1))
    events.append((e+1,-1))
events.sort()
active, res = 0, []
for x,typ in events:
    active += typ
    res.append((x,active))
print(res)
```

**Binary Search on Answer**
- **Definition:** Use binary search to find the optimal answer value, checking each candidate with a check function.
- **Pros:** Optimizes min/max value problems, reduces complexity.
- **Cons:** Only for problems with monotonic properties (can check if answer is valid).
- **When to use?**
  - When finding optimal (min/max) value that satisfies a condition, answer is not known.
- **Example:**
```python
arr = [7,2,5,10,8]
left, right = max(arr), sum(arr)
def check(k):
    cnt, cur = 1, 0
    for x in arr:
        if cur + x > k:
            cnt += 1
            cur = 0
        cur += x
    return cnt <= 3
while left < right:
    mid = (left+right)//2
    if check(mid):
        right = mid
    else:
        left = mid+1
print(left)
```

**Top-K using Heap**
- **Definition:** Use heap to maintain k largest/smallest elements in a stream or large array.
- **Pros:** Efficient O(n log k) for top-k, no need to sort the whole array.
- **Cons:** No random access, only get top-k.
- **When to use?**
  - When finding k largest/smallest elements in a large array or stream.
- **Example:**
```python
import heapq
arr = [3,1,4,1,5,9,2,6]
k = 3
print(heapq.nlargest(k, arr))  # 3 largest
print(heapq.nsmallest(k, arr)) # 3 smallest
```

**A* Search**
- **Definition:** Finds shortest path in weighted graphs using a heuristic to prioritize promising nodes.
- **Pros:** Faster than Dijkstra with good heuristic, used in AI, games, maps.
- **Cons:** Needs good heuristic, can use a lot of memory if not optimized.
- **When to use?**
  - When finding shortest path in maps, AI, games, problems with good heuristic.
- **Example:**
```python
import heapq
# Assume heuristic is Manhattan distance
def astar(start, goal, neighbors, heuristic):
    heap = [(heuristic(start), 0, start)]
    visited = set()
    while heap:
        est, cost, node = heapq.heappop(heap)
        if node == goal:
            return cost
        if node in visited: continue
        visited.add(node)
        for nei, w in neighbors(node):
            if nei not in visited:
                heapq.heappush(heap, (cost+w+heuristic(nei), cost+w, nei))
# Implement neighbors and heuristic for your problem
```

**Math (GCD, Prime, Combinatorics)**
- **Definition:** Basic math techniques like greatest common divisor (GCD), prime check, combinatorics, divisibility, etc.
- **Pros:** Optimizes math problems, reduces complexity, widely applicable.
- **Cons:** Needs good math understanding, easy to make mistakes.
- **When to use?**
  - When solving divisibility, prime, combinatorics, probability, arithmetic problems.
- **Example:**
```python
import math
print(math.gcd(12, 18))  # 6
n = 17
is_prime = n > 1 and all(n%i for i in range(2, int(n**0.5)+1))
print(is_prime)
def comb(n, k):
    res = 1
    for i in range(1, k+1):
        res = res * (n-i+1) // i
    return res
print(comb(5,2))  # 10
```

## Learning Tips

1. **Regular Practice**
   - Solve at least 1 LeetCode problem daily
   - Rewrite code multiple times
   - Optimize solutions

2. **Group Learning**
   - Discuss with peers
   - Share solutions
   - Code review each other

3. **Learning Resources**
   - LeetCode
   - HackerRank
   - GeeksforGeeks
   - YouTube tutorials

## Conclusion

This learning roadmap is designed to help you build a solid foundation in algorithms and data structures. Stay consistent and practice regularly to achieve the best results.

> "Learning algorithms is not a sprint, but a marathon. Stay consistent and steady."

---

[Previous: Chapter 2 - Overview of Technical Interviews](../02-technical-interviews/index.md) | [Next: Chapter 4 - Key Algorithm Topics](../04-algorithms/index.md) 