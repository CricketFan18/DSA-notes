## The "Never Get TLE" Boilerplate


```cpp
#include <bits/stdc++.h>
using namespace std;

// Fast I/O
void fast_io() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    cout.tie(NULL);
}

int main() {
    fast_io();
    int t;
    cin >> t;
    while (t--) {
        // Your logic here
    }
    return 0;
}
```

---

## Invariant Binary Search (`[T, T, F, F]`)

Use this when you need to find the boundary of a condition (e.g., maximum of minimums, last valid element).

```cpp
long long low = -1; // Dummy True
long long high = n; // Dummy False

// Change this function based on the problem's condition
bool isGood(long long mid, vector<long long>& arr) {
    return arr[mid] <= target; // Example condition
}

while (high - low > 1) {
    long long mid = low + (high - low) / 2;
    if (isGood(mid, arr)) {
        low = mid; // Mid is True
    } else {
        high = mid; // Mid is False
    }
}
// 'low' is the last True index. 'high' is the first False index.
```

---

## Variable-Size Sliding Window

Use this to find the longest/shortest contiguous subarray that meets a specific condition.

```cpp
int left = 0, right = 0;
long long current_sum = 0; // Or a frequency map: unordered_map<int, int> freq;
int max_len = 0;

while (right < n) {
    // 1. Add arr[right] to the current state
    current_sum += arr[right]; 
    
    // 2. If the state is invalid, shrink from the left until it becomes valid
    while (current_sum > limit) { // Example invalid condition
        current_sum -= arr[left];
        left++;
    }
    
    // 3. State is now valid. Update your answer.
    max_len = max(max_len, right - left + 1);
    
    // 4. Expand the window
    right++;
}
```

---

## Graph Traversal (BFS & DFS)

For finding connected components or shortest paths in an unweighted graph.

**Setup & DFS:**

```cpp
const int N = 1e5 + 5;
vector<int> adj[N];
bool visited[N];

void dfs(int node) {
    visited[node] = true;
    for (int neighbor : adj[node]) {
        if (!visited[neighbor]) {
            dfs(neighbor);
        }
    }
}
```

**Shortest Path (BFS):**

```cpp
vector<int> dist(n + 1, -1); // -1 means unvisited
queue<int> q;

q.push(start_node);
dist[start_node] = 0;

while (!q.empty()) {
    int curr = q.front();
    q.pop();
    
    for (int neighbor : adj[curr]) {
        if (dist[neighbor] == -1) { // If not visited
            dist[neighbor] = dist[curr] + 1;
            q.push(neighbor);
        }
    }
}
```

---

## Tree Traversal (No `visited` array needed)

Trees don't have cycles, so you don't need a `visited` array. You just pass the `parent` to avoid going backward.

```cpp
vector<int> tree[N];
int subtree_size[N];

void dfs_tree(int node, int parent) {
    subtree_size[node] = 1; // Count itself
    
    for (int child : tree[node]) {
        if (child != parent) { // Don't go back up
            dfs_tree(child, node);
            // Process child results as they bubble up
            subtree_size[node] += subtree_size[child]; 
        }
    }
}
// Call it with: dfs_tree(root, 0); // Assuming 1-based indexing
```

---

## Bit Manipulation Cheat Codes

Quick one-liners for when you need to mask or check states.

C++

```
// Check if the i-th bit of N is set (1)
bool isSet = (N & (1 << i)) != 0;

// Set the i-th bit of N to 1
N = N | (1 << i);

// Flip the i-th bit of N
N = N ^ (1 << i);

// Count how many bits are set to 1 in N
int count = __builtin_popcount(N); // Use __builtin_popcountll(N) for long long

// Iterate through all subsets of an array of size K (where K <= 20)
for (int mask = 0; mask < (1 << K); mask++) {
    for (int i = 0; i < K; i++) {
        if (mask & (1 << i)) {
            // The i-th element is included in this subset
        }
    }
}
```
