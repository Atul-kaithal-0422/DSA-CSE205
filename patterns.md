# Data Structure Patterns to Crack an SDE Role

> A structured guide to the must-know coding patterns for Software Development Engineer interviews at top tech companies.

---

## Table of Contents

1. [Arrays & Strings](#1-arrays--strings)
2. [Two Pointers](#2-two-pointers)
3. [Sliding Window](#3-sliding-window)
4. [Prefix Sum & Difference Arrays](#4-prefix-sum--difference-arrays)
5. [Hashing & Frequency Counting](#5-hashing--frequency-counting)
6. [Stack & Monotonic Stack](#6-stack--monotonic-stack)
7. [Queue & Monotonic Queue](#7-queue--monotonic-queue)
8. [Linked Lists](#8-linked-lists)
9. [Binary Search](#9-binary-search)
10. [Trees & Binary Trees](#10-trees--binary-trees)
11. [Graphs](#11-graphs)
12. [Heaps & Priority Queues](#12-heaps--priority-queues)
13. [Dynamic Programming (DP)](#13-dynamic-programming-dp)
14. [Backtracking](#14-backtracking)
15. [Tries](#15-tries)
16. [Union-Find (Disjoint Set)](#16-union-find-disjoint-set)
17. [Intervals](#17-intervals)
18. [Bit Manipulation](#18-bit-manipulation)

---

## 1. Arrays & Strings

**Core Idea:** The foundation of almost every interview question. Master in-place manipulation and index tricks.

### Key Patterns
- **In-place rotation / reversal** — Rotate array by k steps using triple reverse
- **Kadane's Algorithm** — Maximum subarray sum in O(n)
- **Dutch National Flag** — 3-way partition (sort 0s, 1s, 2s)
- **Majority Element (Boyer-Moore Voting)** — Find element appearing > n/2 times
- **Trapping Rain Water** — Precompute left/right max arrays

### When to Use
- When asked to do something "in-place" or with O(1) extra space
- Finding contiguous subarrays with a property (max, min, sum)

### Complexity Target
| Operation | Time | Space |
|-----------|------|-------|
| Access | O(1) | — |
| Search | O(n) | O(1) |
| Kadane's | O(n) | O(1) |

### Must-Know Problems
- Maximum Subarray (Kadane's)
- Product of Array Except Self
- Rotate Image (matrix rotation)
- Longest Common Prefix
- Trapping Rain Water

---

## 2. Two Pointers

**Core Idea:** Use two indices moving toward or away from each other to eliminate a nested loop, reducing O(n²) to O(n).

### Key Patterns
- **Opposite ends** — Start left=0, right=n-1; converge based on condition
- **Fast & Slow (same direction)** — One pointer races ahead
- **Read/Write pointers** — In-place deduplication or filtering

### When to Use
- Sorted array problems (pair sum, triplets)
- Palindrome checks
- Removing duplicates in-place

### Template
```python
left, right = 0, len(arr) - 1
while left < right:
    if condition(arr[left], arr[right]):
        # process
        left += 1
        right -= 1
    elif arr[left] + arr[right] < target:
        left += 1
    else:
        right -= 1
```

### Must-Know Problems
- Two Sum II (sorted input)
- 3Sum / 4Sum
- Container With Most Water
- Valid Palindrome
- Remove Duplicates from Sorted Array

---

## 3. Sliding Window

**Core Idea:** Maintain a window [left, right] over a sequence. Expand right, shrink left when a constraint is violated. Avoids recomputation.

### Key Patterns
- **Fixed-size window** — Window size k is constant
- **Variable-size window** — Shrink from left when constraint breaks
- **Window with frequency map** — Track character/element counts inside window

### When to Use
- "Find the longest/shortest subarray/substring with property X"
- Contiguous elements with a sum/count constraint

### Template
```python
left = 0
window = {}  # or a counter

for right in range(len(s)):
    # Add s[right] to window
    window[s[right]] = window.get(s[right], 0) + 1

    # Shrink window when invalid
    while window_is_invalid():
        window[s[left]] -= 1
        left += 1

    # Update answer
    ans = max(ans, right - left + 1)
```

### Must-Know Problems
- Longest Substring Without Repeating Characters
- Minimum Window Substring
- Permutation in String
- Fruit Into Baskets
- Longest Repeating Character Replacement

---

## 4. Prefix Sum & Difference Arrays

**Core Idea:** Precompute cumulative sums so any range sum query is answered in O(1). Difference arrays handle range updates efficiently.

### Key Patterns
- **Prefix Sum** — `prefix[i] = prefix[i-1] + arr[i]`; range sum = `prefix[r] - prefix[l-1]`
- **2D Prefix Sum** — For matrix range queries
- **Difference Array** — Range increment/decrement in O(1) update, reconstruct in O(n)
- **Prefix Sum + HashMap** — Find subarrays with sum = k using `seen[prefix - k]`

### Must-Know Problems
- Subarray Sum Equals K
- Range Sum Query (Immutable)
- Product of Array Except Self
- Count of Range Sum
- Corporate Flight Bookings (difference array)

---

## 5. Hashing & Frequency Counting

**Core Idea:** Trade space for time. Use a hash map/set to get O(1) lookup, reducing complex searches to linear passes.

### Key Patterns
- **Frequency Map** — Count occurrences, find duplicates, anagram checks
- **Complement Lookup** — Store `target - num` for Two Sum-style problems
- **Group by key** — Anagram grouping, isomorphic strings
- **Seen set** — Detect cycles, deduplicate

### When to Use
- "Find if X exists" → Use a set
- "Count occurrences of X" → Use a map
- Problems involving pairs that sum/multiply to a target

### Must-Know Problems
- Two Sum
- Group Anagrams
- Top K Frequent Elements
- Longest Consecutive Sequence
- Isomorphic Strings

---

## 6. Stack & Monotonic Stack

**Core Idea:** A stack enforces LIFO order. A **monotonic stack** keeps elements in increasing or decreasing order — perfect for "next greater/smaller element" problems.

### Key Patterns
- **Balanced parentheses / expression parsing**
- **Monotonic Decreasing Stack** → Next Greater Element
- **Monotonic Increasing Stack** → Next Smaller Element
- **Histogram / rectangle area** — Use stack to track bars

### Template (Next Greater Element)
```python
stack = []
result = [-1] * len(nums)

for i in range(len(nums)):
    while stack and nums[i] > nums[stack[-1]]:
        idx = stack.pop()
        result[idx] = nums[i]
    stack.append(i)
```

### Must-Know Problems
- Valid Parentheses
- Daily Temperatures
- Largest Rectangle in Histogram
- Next Greater Element I & II
- Asteroid Collision

---

## 7. Queue & Monotonic Queue

**Core Idea:** FIFO structure. A **deque** (double-ended queue) enables the sliding window maximum/minimum in O(n).

### Key Patterns
- **BFS traversal** — Level-order tree/graph traversal
- **Monotonic Deque** — Sliding window max/min; front = max, evict from back
- **Circular Queue** design

### Must-Know Problems
- Sliding Window Maximum
- BFS Shortest Path
- Design Circular Queue
- Task Scheduler
- Jump Game VI (DP + deque)

---

## 8. Linked Lists

**Core Idea:** Sequential node-based structure. Most problems rely on pointer manipulation and the fast/slow pointer technique.

### Key Patterns
- **Fast & Slow Pointers** — Detect cycle, find middle, find kth from end
- **Reversal** — Reverse entire list or a sublist in-place
- **Merge** — Merge two sorted lists
- **Dummy Node** — Simplifies edge cases for head manipulation
- **In-place operations** — No extra space

### Must-Know Problems
- Reverse Linked List (iterative & recursive)
- Detect Cycle (Floyd's algorithm)
- Find Middle of Linked List
- Merge Two Sorted Lists
- LRU Cache (doubly linked list + hashmap)
- Reorder List

---

## 9. Binary Search

**Core Idea:** Halve the search space every iteration. Works on any **monotonic** function, not just sorted arrays.

### Key Patterns
- **Classic binary search** — Exact target in sorted array
- **Search on answer** — "Find the minimum X such that condition holds" → binary search on the answer space
- **Rotated sorted array** — Determine which half is sorted
- **First/Last occurrence** — Use `left` or `right` boundary variants

### Template (Search on Answer)
```python
left, right = min_possible, max_possible

while left < right:
    mid = (left + right) // 2
    if feasible(mid):
        right = mid
    else:
        left = mid + 1

return left
```

### Must-Know Problems
- Binary Search (classic)
- Search in Rotated Sorted Array
- Find Minimum in Rotated Sorted Array
- Koko Eating Bananas (search on answer)
- Median of Two Sorted Arrays

---

## 10. Trees & Binary Trees

**Core Idea:** Hierarchical structures. Recursion is the natural fit. Master DFS (pre/in/post-order) and BFS (level-order).

### Key Patterns
- **DFS — Pre/In/Post-order traversal** (recursive & iterative)
- **BFS — Level-order traversal** (queue-based)
- **Binary Search Tree (BST)** — In-order gives sorted sequence; search in O(h)
- **LCA (Lowest Common Ancestor)** — Recurse, return node when found
- **Path problems** — Track path sum, max gain through a node
- **Serialization / Deserialization**

### Must-Know Problems
- Invert Binary Tree
- Maximum Depth / Diameter of Binary Tree
- Lowest Common Ancestor of BST / Binary Tree
- Binary Tree Level Order Traversal
- Validate Binary Search Tree
- Serialize and Deserialize Binary Tree
- Construct Tree from Preorder + Inorder

---

## 11. Graphs

**Core Idea:** Model relationships between entities. Master BFS, DFS, and know when to use which.

### Key Patterns
- **BFS** — Shortest path in unweighted graph, level-order exploration
- **DFS** — Connected components, topological sort, cycle detection
- **Topological Sort** — Kahn's algorithm (BFS) or DFS post-order; for DAGs
- **Union-Find** — Connectivity queries (see section 16)
- **Dijkstra's** — Shortest path in weighted graph (use a min-heap)
- **Grid as Graph** — 4-directional BFS/DFS (islands, mazes)

### Template (BFS Shortest Path)
```python
from collections import deque

queue = deque([(start, 0)])
visited = {start}

while queue:
    node, dist = queue.popleft()
    if node == target:
        return dist
    for neighbor in graph[node]:
        if neighbor not in visited:
            visited.add(neighbor)
            queue.append((neighbor, dist + 1))
```

### Must-Know Problems
- Number of Islands
- Clone Graph
- Course Schedule I & II (topological sort)
- Pacific Atlantic Water Flow
- Shortest Path in Binary Matrix
- Word Ladder
- Network Delay Time (Dijkstra's)

---

## 12. Heaps & Priority Queues

**Core Idea:** A heap gives O(log n) insert/delete and O(1) min/max access. Use Python's `heapq` (min-heap by default; negate values for max-heap).

### Key Patterns
- **Top K elements** — Push all, pop when size > k; or use heap directly
- **Kth Largest/Smallest** — Maintain heap of size k
- **Merge K sorted lists** — Push (val, list_idx) into heap
- **Two heaps** — Max-heap (left half) + Min-heap (right half) for running median
- **Greedy + Heap** — Task scheduling, meeting rooms

### Must-Know Problems
- Kth Largest Element in an Array
- Top K Frequent Elements
- Find Median from Data Stream (two heaps)
- Merge K Sorted Lists
- Task Scheduler
- Reorganize String

---

## 13. Dynamic Programming (DP)

**Core Idea:** Break problems into overlapping subproblems. Store results to avoid recomputation (memoization or tabulation).

### Key Patterns

| Pattern | Example Problems |
|---------|-----------------|
| **Linear DP** | Climbing Stairs, House Robber |
| **Grid/2D DP** | Unique Paths, Minimum Path Sum |
| **Knapsack (0/1)** | Partition Equal Subset Sum, Target Sum |
| **Unbounded Knapsack** | Coin Change, Rod Cutting |
| **LCS / LIS** | Longest Common Subsequence, LIS |
| **Interval DP** | Matrix Chain Multiplication, Burst Balloons |
| **String DP** | Edit Distance, Regex Matching |
| **State Machine DP** | Best Time to Buy/Sell Stock (with cooldown/fee) |
| **DP on Trees** | Diameter, House Robber III |

### Template (Top-Down Memoization)
```python
from functools import lru_cache

@lru_cache(maxsize=None)
def dp(state):
    # base case
    if base_condition(state):
        return base_value
    # recurrence
    return min/max(dp(next_state) for next_state in transitions(state))
```

### Must-Know Problems
- Climbing Stairs / Fibonacci
- Coin Change
- Longest Increasing Subsequence
- Edit Distance
- Unique Paths
- Word Break
- Partition Equal Subset Sum
- Best Time to Buy and Sell Stock (all variants)

---

## 14. Backtracking

**Core Idea:** Explore all possibilities via DFS, and **prune** branches that can't lead to a valid solution. Think: "choose → explore → un-choose."

### Key Patterns
- **Subsets** — Include or exclude each element
- **Permutations** — Swap or use a visited set
- **Combinations** — Pick elements with a start index to avoid repeats
- **Constraint satisfaction** — N-Queens, Sudoku Solver

### Template
```python
def backtrack(start, current):
    if is_solution(current):
        result.append(list(current))
        return

    for choice in choices(start):
        current.append(choice)         # choose
        backtrack(start + 1, current)  # explore
        current.pop()                  # un-choose
```

### Must-Know Problems
- Subsets / Subsets II
- Permutations / Permutations II
- Combination Sum I & II
- N-Queens
- Sudoku Solver
- Word Search

---

## 15. Tries

**Core Idea:** A tree where each node represents a character. Ideal for prefix-matching, autocomplete, and dictionary problems.

### Key Patterns
- **Insert / Search / StartsWith** — Core operations
- **Word dictionary with wildcards** — DFS on trie
- **Maximum XOR** — Build a binary trie
- **Word search on a board** — Trie + backtracking

### Template
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
        for ch in word:
            node = node.children.setdefault(ch, TrieNode())
        node.is_end = True

    def search(self, word):
        node = self.root
        for ch in word:
            if ch not in node.children:
                return False
            node = node.children[ch]
        return node.is_end
```

### Must-Know Problems
- Implement Trie (Prefix Tree)
- Word Search II
- Design Add and Search Words
- Replace Words
- Maximum XOR of Two Numbers in an Array

---

## 16. Union-Find (Disjoint Set)

**Core Idea:** Efficiently group elements into sets and check if two elements belong to the same set. With path compression + union by rank: near O(1) per operation.

### Key Patterns
- **Connected components** in undirected graphs
- **Cycle detection** in undirected graphs
- **Dynamic connectivity** — Elements merging over time
- **Kruskal's MST** — Minimum Spanning Tree

### Template
```python
class UnionFind:
    def __init__(self, n):
        self.parent = list(range(n))
        self.rank = [0] * n

    def find(self, x):
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])  # path compression
        return self.parent[x]

    def union(self, x, y):
        px, py = self.find(x), self.find(y)
        if px == py:
            return False
        if self.rank[px] < self.rank[py]:
            px, py = py, px
        self.parent[py] = px
        if self.rank[px] == self.rank[py]:
            self.rank[px] += 1
        return True
```

### Must-Know Problems
- Number of Connected Components in an Undirected Graph
- Redundant Connection
- Accounts Merge
- Number of Islands II (dynamic)
- Satisfiability of Equality Equations

---

## 17. Intervals

**Core Idea:** Sort by start time, then greedily merge or count overlaps.

### Key Patterns
- **Merge Overlapping Intervals** — Sort by start; merge when `next.start <= prev.end`
- **Insert Interval** — Handle 3 zones: before, overlapping, after
- **Meeting Rooms** — Sort by start; check for overlap with a min-heap of end times
- **Sweep Line** — Convert to events (+1 at start, -1 at end), sort, scan

### Must-Know Problems
- Merge Intervals
- Insert Interval
- Non-overlapping Intervals
- Meeting Rooms II (min-heap)
- Employee Free Time

---

## 18. Bit Manipulation

**Core Idea:** Work directly on binary representations for ultra-fast, constant-space solutions.

### Key Patterns & Tricks

| Operation | Expression |
|-----------|------------|
| Check if bit i is set | `n & (1 << i)` |
| Set bit i | `n \| (1 << i)` |
| Clear bit i | `n & ~(1 << i)` |
| Toggle bit i | `n ^ (1 << i)` |
| Check power of 2 | `n & (n - 1) == 0` |
| Count set bits | `bin(n).count('1')` or Brian Kernighan |
| XOR trick | `a ^ a = 0`, `a ^ 0 = a` → find single number |
| Get lowest set bit | `n & (-n)` |

### Must-Know Problems
- Single Number (XOR)
- Number of 1 Bits (Hamming Weight)
- Reverse Bits
- Missing Number
- Sum of Two Integers (without + operator)
- Counting Bits

---

## Study Roadmap

```
Week 1-2  →  Arrays, Strings, Two Pointers, Sliding Window, Hashing
Week 3-4  →  Stack, Queue, Linked Lists, Binary Search
Week 5-6  →  Trees (BFS + DFS), Heaps, Intervals
Week 7-8  →  Graphs (BFS/DFS/Topo Sort), Union-Find
Week 9-10 →  Dynamic Programming (all patterns)
Week 11   →  Backtracking, Tries
Week 12   →  Bit Manipulation + Mock Interviews + Revision
```

---

## Quick Reference: Pattern Recognition

| Problem Clue | Pattern to Use |
|---|---|
| Sorted array, find pair | Two Pointers |
| Longest/shortest subarray with condition | Sliding Window |
| Subarray sum equals k | Prefix Sum + HashMap |
| Next greater/smaller element | Monotonic Stack |
| Shortest path in unweighted graph | BFS |
| All possible combinations/subsets | Backtracking |
| Top K / Kth largest | Heap |
| Overlapping subproblems, optimal value | Dynamic Programming |
| Prefix matching, autocomplete | Trie |
| Connected components, cycle detection | Union-Find |
| Binary on answer space | Binary Search |
| Involves intervals, scheduling | Interval / Sweep Line |
| Duplicate detection, pair finding | Hashing |
| Count set bits, XOR operations | Bit Manipulation |

---

*Master the pattern, not just the problem. Every hard problem is a combination of two or more patterns above.*
