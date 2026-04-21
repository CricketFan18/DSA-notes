## The Blueprint for Solving Any DSA Problem

Never jump straight into coding.

1. **Comprehend and Clarify:** Read the problem twice. Identify the exact input and output formats. Are there negative numbers? Can the array be empty? Are there duplicates?
    
2. **Check the Constraints:** Look at the maximum value of $N$ (the input size). This tells you the exact time complexity the platform expects.
    
3. **Brainstorm the Naive Approach (Brute Force):** Always start here. Figuring out the $O(N^2)$ or $O(2^N)$ solution helps you understand the core mechanics of the problem.
    
4. **Optimize:** Look at the bottlenecks in your brute-force solution. Are you doing repeated work? Are you searching linearly?
    
5. **Dry Run:** Test your optimized logic on a small, tricky test case on paper before writing a single line of code.
    
6. **Implementation (Coding):** Translate your logic into code. Keep it clean and modular. Write separate helper functions. Write clear comparators. Stick to standard variable names (`left`, `right`, `curr`, `prev`).
    
7. **Edge Case Testing & Complexity Verification:** Before you hit submit, manually run your code through the danger zones.
    
    - **Empty inputs:** What if the array or string is empty?
        
    - **Minimum/Maximum bounds:** What if $N = 1$ or $N = 10^5$? Will integer overflow occur?
        
    - **Duplicates:** Does your logic break if all elements are the same?
        
    - **Verify Complexity:** If constraints say $N = 10^5$, ensure you haven't accidentally written an $O(N^2)$ operation inside a loop.
        

---

## Decoding the Constraints (The $10^8$ Rule)

Modern judging platforms can perform roughly $10^8$ operations per second. Use the maximum input size ($N$) to reverse-engineer the required time complexity.

|**Input Size (N)**|**Target Complexity**|**Likely Algorithmic Paradigms**|
|---|---|---|
|$N \le 10 \dots 12$|$O(N!)$|Pure Recursion, Factorial Backtracking|
|$N \le 20 \dots 25$|$O(2^N)$|Subset Generation, Bitmasking, Exponential Backtracking|
|$N \le 100$|$O(N^3)$ or $O(N^4)$|3D Dynamic Programming, Matrix Exponentiation, All-Pairs Shortest Path|
|$N \le 1000$|$O(N^2)$|2D Dynamic Programming, Dense Graph Algorithms|
|$N \le 10^5$|$O(N \log N)$|Advanced Sorting, Binary Search, Divide & Conquer, Min/Max Heaps, Segment Trees|
|$N \le 10^6$|$O(N)$|Linear Scans, Two Pointers, Sliding Window, Hash Mapping, Prefix Arrays, Linear DP, Graph BFS/DFS|
|$N \ge 10^9$|$O(\log N)$|Binary Search on Answer Space, Logarithmic Math Formulas, Euclidean Algorithms|
|$N \ge 10^9$|$O(1)$|Pure Mathematics, Bitwise Arithmetic, Greedy Heuristics|

---

## Exhaustive Algorithm & Pattern Recognition Guide

#### 1. Math & Number Theory

**Complexity Range:** $O(1)$ – $O(\log N)$

Pure math algorithms operate on number properties. No dynamic data structures are needed.

- **Sieve of Eratosthenes:** For bulk prime generation.
    
- **Segmented Sieve:** For generating primes in a specific range.
    
- **Trial Division:** For single-integer primality testing.
    
- **Euclidean Algorithm:** For finding the Greatest Common Divisor (GCD).
    
- **Extended Euclidean Algorithm:** For finding coefficients of Bézout's identity.
    
- **Matrix Exponentiation:** For solving linear recurrences in logarithmic time.
    
- **Modular Exponentiation:** For calculating large powers under a modulo.
    
- **Modular Multiplicative Inverse:** Using Fermat's Little Theorem.
    
- **Pascal's Identity (Combinatorics):** For generating combinations (${n \choose k}$).
    
- **Inclusion-Exclusion Principle:** For combinatorial overlap counting.
    
- **Prime Factorization:** Using smallest prime factors (SPF).
    
- **Pigeonhole Principle:** Theoretical logic for constraint limits.
    

#### 2. Array

**Complexity Range:** $O(N)$ – $O(N \log N)$

- **Hash Map Frequency Counting:** Constant time lookups for pairing and counting.
    
- **Array Rotation / Reversal Algorithm:** Modifying array states in $O(1)$ space.
    
- **Prefix Sum / Suffix Sum Array:** Precomputing cumulative sums for $O(1)$ range queries.
    
- **Prefix Product / Suffix Product:** Precomputing bounds excluding self.
    
- **Kadane's Algorithm:** Finding maximum contiguous subarray sums.
    
- **Moore's Voting Algorithm:** Finding the majority element in linear time.
    
- **Three-Way Partitioning (Dutch National Flag Algorithm):** Sorting strict sets of 3 distinct values.
    
- **In-Place Cycle Sort:** Sorting elements strictly in the range $1$ to $N$.
    
- **Line Sweep Algorithm:** Processing points/events along a 1D line iteratively.
    

#### 3. String

**Complexity Range:** $O(N)$ – $O(N^2)$

- **Frequency Mapping (Character Arrays):** Utilizing fixed-size arrays (size 26 or 256) for constant time hashing.
    
- **Palindrome Expansion (Expand Around Center):** Expanding outward from iterative indices.
    
- **Manacher's Algorithm:** Finding the longest palindromic substring in strictly $O(N)$ time.
    
- **KMP Algorithm (Knuth-Morris-Pratt):** Linear time pattern matching using a Longest Prefix Suffix (LPS) array.
    
- **Rabin-Karp Algorithm:** Pattern matching using Rolling Hashes.
    
- **Z-Algorithm:** Linear time pattern matching constructing a Z-array.
    
- **Aho-Corasick Algorithm:** String searching across a finite state machine (dictionary matching).
    
- **Suffix Array / Suffix Tree Construction:** Advanced lexicographical string sorting.
    

#### 4. Bit Manipulation

**Complexity Range:** $O(1)$ – $O(N)$

- **XOR Cancellation:** Utilizing $A \oplus A = 0$ and $A \oplus 0 = A$.
    
- **Brian Kernighan's Algorithm:** Clearing the lowest set bit using `n & (n - 1)`.
    
- **Bitwise Shift Operations:** For fast multiplication/division and masking.
    
- **Bitmask Subset Generation:** Iterating from $0$ to $2^N - 1$ to map all combinations.
    

#### 5. Binary Search

**Complexity Range:** $O(\log N)$

- **Classic Binary Search:** Halving a strictly sorted contiguous space.
    
- **Lower Bound / Upper Bound Search:** Finding the insertion point of a duplicate or missing element.
    
- **Binary Search on Answer (Predicate Search):** Searching an abstract monotonic optimization space using an `isValid()` function.
    
- **Binary Search on Rotated Arrays:** Halving arrays pivoted at an unknown index.
    
- **Ternary Search:** Finding the minimum/maximum of a strictly unimodal function.
    
- **Fractional Cascading:** Speeding up binary searches across multiple sorted arrays.
    

#### 6. Sliding Window & Two Pointers

**Complexity Range:** $O(N)$

- **Fixed-Size Sliding Window:** Moving a uniform frame across an iterable.
    
- **Variable-Size Sliding Window:** Expanding a `right` pointer to ingest, shrinking a `left` pointer to validate constraints.
    
- **Two Pointers Converging:** Pointers starting at both ends and moving inward based on comparison logic.
    
- **Two Pointers Same Direction (Fast/Slow Pointers):** Often used for in-place array modification or cycle detection.
    

#### 7. Backtracking

**Complexity Range:** $O(2^N)$ – $O(N!)$

- **State-Space Tree Traversal:** The core `Choose -> Explore -> Un-choose` template.
    
- **Permutation Generation:** Swapping indices iteratively.
    
- **Combination / Subset Generation:** Binary inclusion/exclusion recursion.
    
- **Backtracking with Pruning:** Terminating recursion branches early based on localized constraint checks.
    
- **Grid Backtracking:** Traversing a 2D matrix while maintaining a visited state structure.
    

#### 8. Stack

**Complexity Range:** $O(N)$

- **Standard Stack (LIFO):** For state history, bracket matching, and depth tracking.
    
- **Monotonic Increasing Stack:** Strictly maintaining ascending order to find the next smaller element.
    
- **Monotonic Decreasing Stack:** Strictly maintaining descending order to find the next greater element.
    
- **Shunting-Yard Algorithm:** Parsing mathematical expressions (Infix to Postfix).
    

#### 9. Queue

**Complexity Range:** $O(N)$

- **Standard Queue (FIFO):** The core mechanism for Level-Order states.
    
- **Double-Ended Queue (Deque):** Allowing $O(1)$ operations at both boundaries.
    
- **Monotonic Deque:** Maintaining a sliding maximum/minimum.
    
- **Circular Queue:** Buffer tracking via modulo capacity operations.
    

#### 10. Linked List

**Complexity Range:** $O(N)$

- **Floyd's Cycle-Finding Algorithm (Tortoise and Hare):** Cycle detection and finding convergence nodes.
    
- **Dummy Head Pattern:** Creating a structural anchor to prevent null reference errors on shifting heads.
    
- **In-Place Pointer Reversal:** Overriding pointer trajectories using `prev`, `curr`, and `next`.
    
- **Skip List Traversal:** Probabilistic multi-level searching.
    

#### 11. Heap / Priority Queue

**Complexity Range:** $O(N \log K)$

- **Min-Heap / Max-Heap Operations:** Maintaining root-level minimums or maximums.
    
- **Heapify Algorithm:** Structuring an unsorted array into a heap in $O(N)$ time.
    
- **Two-Heap Pattern:** Balancing a Max-Heap and Min-Heap to isolate medians dynamically.
    
- **K-Way Merge Pattern:** Utilizing a Min-Heap to interleave multiple sorted datasets.
    

#### 12. Tree

**Complexity Range:** $O(N)$ – $O(N \log N)$

- **Preorder / Inorder / Postorder Traversal:** Standard DFS implementations.
    
- **Level-Order Traversal:** Standard BFS implementation.
    
- **Morris Traversal:** Inorder traversal achieving $O(1)$ space by threading temporary pointers.
    
- **Binary Lifting (Lowest Common Ancestor):** Using $2^i$ jumps to find ancestors logarithmically.
    
- **Tree Diameter Algorithm:** Recursive depth maximization.
    
- **Centroid Decomposition:** Breaking a tree into a centroid tree for path querying.
    
- **Heavy-Light Decomposition (HLD):** Breaking tree paths into contiguous segments for segment tree integration.
    

#### 13. Graph

**Complexity Range:** $O(V + E)$ – $O(V^3)$

- **Breadth-First Search (BFS):** Shortest path in unweighted graphs.
    
- **Depth-First Search (DFS):** Path exploration and connected components.

- **Bipartite Graph Checking:** Utilizing two-color graph traversal.
    
- **Dijkstra's Algorithm:** Shortest path in non-negative weighted graphs (using a Min-Heap).
    
- **Bellman-Ford Algorithm:** Shortest path handling negative weights; negative cycle detection.
    
- **Floyd-Warshall Algorithm:** All-pairs shortest path ($O(V^3)$).
    
- **Kahn's Algorithm (Topological Sort):** Using in-degree arrays to order dependencies.
    
- **DFS Topological Sort:** Using post-order traversal reversal.

- **Disjoint Set Union (DSU) / Union-Find:** Tracking disjoint subsets using Path Compression and Union by Rank.
    
- **Kruskal's Algorithm:** Minimum Spanning Tree using edge sorting and DSU.
    
- **Prim's Algorithm:** Minimum Spanning Tree using node expansion via Min-Heap.
    
- **Tarjan's Algorithm:** Finding Strongly Connected Components (SCCs).
    
- **Kosaraju's Algorithm:** Alternative, two-pass DFS for finding SCCs.
    
- **Hierholzer's Algorithm:** Finding Eulerian Paths and Circuits.
    
-  **Hopcraft-Tarjan Algorithm:** Finding Bridges, and Articulation Points in a network.
    
- **Hopcroft-Karp Algorithm:** Finding maximum matching in a bipartite graph.
    

#### 14. Greedy

**Complexity Range:** $O(N \log N)$

- **Interval Scheduling Algorithm:** Sorting temporal datasets by end times.
    
- **Greedy Simulation:** Progressing linearly based on localized maximum/minimum utility.
    
- **Huffman Coding:** Constructing prefix-free binary trees for compression.
    

#### 15. Dynamic Programming (DP)

**Complexity Range:** $O(N)$ – $O(N^3)$

- **1D / 2D Tabulation:** Bottom-up iterative optimization.
    
- **Memoization:** Top-down recursive caching.
    
- **0/1 Knapsack Pattern:** Limited availability optimization.
    
- **Unbounded Knapsack Pattern:** Infinite availability optimization.
    
- **Longest Common Subsequence (LCS) Pattern:** 2D grid character matching recurrence.
    
- **Longest Increasing Subsequence (LIS) Pattern:** DP often optimized with Binary Search.
    
- **Edit Distance Pattern:** Minimizing operational transformations.
    
- **Interval DP:** Recursively splitting sequences into partitions.
    
- **Bitmask DP:** Solving state problems over sub-graphs utilizing binary subset representations.
    
- **State Machine DP:** Incorporating complex sequential restrictions (e.g., cooldowns).
    
- **Tree DP:** Computing subproblem states passing up tree edges.
    
- **Digit DP:** Counting numbers in a range fulfilling arbitrary digit conditions.
    
- **Knuth Optimization:** Speeding up specific Interval DP recurrences.
    
- **Convex Hull Trick (CHT):** Optimizing DP intersecting linear functions.
    

#### 16. Trie (Prefix Tree)

**Complexity Range:** $O(L)$ per query (where $L$ is sequence length)

- **Standard Trie Insertion / Search:** Node traversal via character mapping.
    
- **Binary Trie:** Traversing bit structures to maximize/minimize XOR operations.
    
- **Compressed Trie / Radix Tree:** Optimizing memory by merging single-child nodes.