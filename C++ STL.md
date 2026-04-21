## 1. Vector (`<vector>`)

A dynamic array that can resize itself automatically. This is the most frequently used container in competitive programming.

| **Method**           | **Description**                            | **Time Complexity** |
| -------------------- | ------------------------------------------ | ------------------- |
| `push_back(val)`     | Adds an element to the end.                | $O(1)$ amortized    |
| `pop_back()`         | Removes the last element.                  | $O(1)$              |
| `size()`             | Returns the number of elements.            | $O(1)$              |
| `empty()`            | Checks if the vector is empty.             | $O(1)$              |
| `front()` / `back()` | Accesses the first / last element.         | $O(1)$              |
| `begin()` / `end()`  | Returns an iterator to the start / end.    | $O(1)$              |
| `insert(pos, val)`   | Inserts an element at a specific iterator. | $O(n)$              |
| `erase(pos)`         | Removes an element at a specific iterator. | $O(n)$              |
| `clear()`            | Removes all elements.                      | $O(n)$              |


## 2. String (`<string>`)

A class representing a sequence of characters, functioning very similarly to a vector.

|**Method**|**Description**|**Time Complexity**|
|---|---|---|
|`length()` / `size()`|Returns the length of the string.|$O(1)$|
|`push_back(char)`|Appends a character to the end.|$O(1)$ amortized|
|`pop_back()`|Removes the last character.|$O(1)$|
|`substr(pos, len)`|Returns a substring starting at `pos` of length `len`.|$O(\text{len})$|
|`find(str)`|Finds the first occurrence of `str` (returns `string::npos` if not found).|$O(n \times m)$|
|`append(str)` / `+=`|Appends another string.|$O(\text{len})$|

## 3. Pair (`<utility>`)

Used to store two heterogeneous objects as a single unit. Very useful for graphs, coordinates, and intervals.

|**Method / Property**|**Description**|**Time Complexity**|
|---|---|---|
|`make_pair(a, b)`|Creates a pair with values `a` and `b` (or just use `{a, b}`).|$O(1)$|
|`p.first`|Accesses the first element.|$O(1)$|
|`p.second`|Accesses the second element.|$O(1)$|

## 4. Stack (`<stack>`)

A Container Adaptor operating on a Last-In-First-Out (LIFO) principle.

|**Method**|**Description**|**Time Complexity**|
|---|---|---|
|`push(val)`|Inserts an element at the top.|$O(1)$|
|`pop()`|Removes the top element.|$O(1)$|
|`top()`|Accesses the top element without removing it.|$O(1)$|
|`size()`|Returns the number of elements.|$O(1)$|
|`empty()`|Checks if the stack is empty.|$O(1)$|

## 5. Queue (`<queue>`)

A Container Adaptor operating on a First-In-First-Out (FIFO) principle.

|**Method**|**Description**|**Time Complexity**|
|---|---|---|
|`push(val)`|Inserts an element at the back.|$O(1)$|
|`pop()`|Removes the front element.|$O(1)$|
|`front()`|Accesses the front element.|$O(1)$|
|`back()`|Accesses the last element.|$O(1)$|
|`size()` / `empty()`|Returns size / checks if empty.|$O(1)$|

## 6. Priority Queue (`<queue>`)

A Container Adaptor that provides constant time lookup of the largest (by default) or smallest element. Under the hood, it is a Heap.

> **Note:** By default, `priority_queue<int> pq;` is a **Max-Heap**. To make a **Min-Heap**, use:
> 
> `priority_queue<int, vector<int>, greater<int>> pq;`

|**Method**|**Description**|**Time Complexity**|
|---|---|---|
|`push(val)`|Inserts an element and maintains heap structure.|$O(\log n)$|
|`pop()`|Removes the top (largest/smallest) element.|$O(\log n)$|
|`top()`|Accesses the top element.|$O(1)$|
|`size()` / `empty()`|Returns size / checks if empty.|$O(1)$|

## 7. Deque (`<deque>`)

A Double-Ended Queue that allows fast insertion and deletion at _both_ the front and back.

|**Method**|**Description**|**Time Complexity**|
|---|---|---|
|`push_front(val)` / `push_back(val)`|Inserts element at the front / back.|$O(1)$|
|`pop_front()` / `pop_back()`|Removes element from the front / back.|$O(1)$|
|`front()` / `back()`|Accesses the front / back element.|$O(1)$|

## 8. Set and Unordered Set (`<set>`, `<unordered_set>`)

Collections of unique elements.

- **`set`**: Implemented as a Red-Black Tree. Elements are sorted.
    
- **`unordered_set`**: Implemented as a Hash Table. Elements are unsorted.
    

|**Method**|**Description**|**Complexity (set)**|**Complexity (unordered_set)**|
|---|---|---|---|
|`insert(val)`|Adds the element to the set.|$O(\log n)$|$O(1)$ avg, $O(n)$ worst|
|`erase(val)`|Removes the element from the set.|$O(\log n)$|$O(1)$ avg, $O(n)$ worst|
|`find(val)`|Returns iterator to element, or `end()` if not found.|$O(\log n)$|$O(1)$ avg, $O(n)$ worst|
|`count(val)`|Returns 1 if present, 0 if not (good for checking existence).|$O(\log n)$|$O(1)$ avg, $O(n)$ worst|
|`lower_bound(val)`|Returns iterator to first element $\ge$ `val`.|$O(\log n)$|Not Available|
|`upper_bound(val)`|Returns iterator to first element $>$ `val`.|$O(\log n)$|Not Available|

## 9. Map and Unordered Map (`<map>`, `<unordered_map>`)

Collections of key-value pairs where keys are unique.

- **`map`**: Sorted by keys (Red-Black Tree).
    
- **`unordered_map`**: Unsorted (Hash Table).
    

|**Method**|**Description**|**Complexity (map)**|**Complexity (unordered_map)**|
|---|---|---|---|
|`mp[key] = val`|Inserts or updates the value associated with `key`.|$O(\log n)$|$O(1)$ avg, $O(n)$ worst|
|`insert({k, v})`|Inserts the key-value pair.|$O(\log n)$|$O(1)$ avg, $O(n)$ worst|
|`erase(key)`|Removes the key and its value.|$O(\log n)$|$O(1)$ avg, $O(n)$ worst|
|`find(key)`|Returns iterator to key-value pair, or `end()` if not found.|$O(\log n)$|$O(1)$ avg, $O(n)$ worst|
|`count(key)`|Returns 1 if key exists, 0 otherwise.|$O(\log n)$|$O(1)$ avg, $O(n)$ worst|
|`lower_bound(key)`|Returns iterator to first key $\ge$ `key`.|$O(\log n)$|Not Available|

---

## Bonus: Crucial `<algorithm>` Methods

- **`sort(begin, end)`**: Sorts elements in ascending order ($O(n \log n)$).
    
- **`reverse(begin, end)`**: Reverses the order of elements ($O(n)$).
    
- **`max_element(begin, end)` / `min_element(begin, end)`**: Returns an iterator to the max/min element ($O(n)$).
    
- **`accumulate(begin, end, initial_sum)`**: Sums up all elements ($O(n)$). Requires `<numeric>`.
    
- **`next_permutation(begin, end)`**: Rearranges elements into the next lexicographically greater permutation ($O(n)$).

---
## Methodologies in C++

Here is what else is crucial to master in C++ for DSA.

### Custom Comparators (The C++ Way)

Just like in Java, you will frequently need to sort custom objects or pairs. Modern C++ (C++11 and onward) makes this very clean with **Lambda Expressions**.

**Sorting Vectors/Arrays:**

The lambda takes two arguments. Return `true` if the first argument should go _before_ the second argument.

C++

```cpp
vector<pair<int, int>> intervals = {{1, 3}, {2, 6}, {8, 10}, {15, 18}};

// Sort primarily by the first element ascending, then by second element descending
sort(intervals.begin(), intervals.end(), [](const pair<int, int>& a, const pair<int, int>& b) {
    if (a.first == b.first) {
        return a.second > b.second; // Descending
    }
    return a.first < b.first; // Ascending
});
```

**The Priority Queue Quirk:**

Unlike `sort()`, which takes a function/lambda as a parameter, `priority_queue` requires a **type** for its comparator. You usually have to write a custom `struct` with an overloaded `operator()`.

C++

```
// Comparator for a Min-Heap based on the second value of a pair
struct Compare {
    bool operator()(const pair<int, int>& a, const pair<int, int>& b) {
        // Notice the reversed logic! Return true if 'a' has lower priority than 'b'
        return a.second > b.second; 
    }
};

priority_queue<pair<int, int>, vector<pair<int, int>>, Compare> pq;
```

### Passing by Reference vs. Value (The Biggest Performance Trap)

In C++, if you pass a `vector`, `string`, or `map` into a function standardly, **C++ makes a complete deep copy of it**. This turns an $O(1)$ function call into an $O(n)$ disaster, leading to instant Time Limit Exceeded (TLE) errors.

Always pass large data structures by **reference** using the ampersand (`&`).

C++

```
// BAD: Copies the entire vector every time it's called.
void dfs(int node, vector<int> adj) { ... }

// GOOD: Passes a reference (memory address). Extremely fast.
void dfs(int node, vector<int>& adj) { ... }

// BEST: If you only need to read the data, make it const so you don't accidentally modify it.
void printVector(const vector<int>& v) { ... }
```

### Fast Input / Output (I/O)

If you are doing competitive programming (Codeforces, CodeChef), standard `cin` and `cout` are notoriously slow because they are synchronized with C's `stdio` libraries.

You must put these two magical lines at the very beginning of your `main()` function to speed them up.

C++

```
int main() {
    ios_base::sync_with_stdio(false); // Disables synchronization with C streams
    cin.tie(NULL);                    // Unties cin from cout
    
    // Your code here...
    return 0;
}
```

> **Pro Tip:** Never use `endl` in competitive programming. It flushes the output stream every single time, which is very slow. Use `'\n'` instead (e.g., `cout << ans << '\n';`).

### C++17 Structured Binding (Quality of Life)

If your environment supports C++17 (almost all modern coding platforms do), **Structured Bindings** will make your code infinitely cleaner, especially when dealing with Maps and Pairs.

Instead of typing `p.first` and `p.second` repeatedly:

C++

```
map<int, string> mp = {{1, "A"}, {2, "B"}};

// Old way:
for (auto it : mp) {
    cout << it.first << " " << it.second << '\n';
}

// C++17 Modern way:
for (auto& [key, val] : mp) {
    cout << key << " " << val << '\n';
}
```

### Essential Built-in Functions (GCC Intrinsics)

If you are doing bit manipulation, the GCC compiler (used by standard competitive programming platforms) provides incredibly fast, built-in functions:

- `__builtin_popcount(x)`: Returns the number of set bits (1s) in an integer ($O(1)$). (Use `__builtin_popcountll(x)` for `long long`).
    
- `__builtin_clz(x)`: Counts the leading zeros of an integer.
    
- `__builtin_ctz(x)`: Counts the trailing zeros of an integer.
    

### Number Theory Goodies (`<numeric>`)

Instead of writing your own Greatest Common Divisor (GCD) or Least Common Multiple (LCM) functions, C++17 has them built into the `<numeric>` header:

- `std::gcd(a, b)`: Returns the GCD of `a` and `b`.
    
- `std::lcm(a, b)`: Returns the LCM of `a` and `b`.
    

### Macros and Typedefs (Use with Caution)

You will often see competitive programmers use macros to type faster. While frowned upon in production software engineering, they are standard in DSA contests to save time.

C++

```
using ll = long long; // Much cleaner than typing long long repeatedly
#define pb push_back
#define all(x) (x).begin(), (x).end()

// Usage:
vector<ll> v;
v.pb(10);
sort(all(v)); 
```

