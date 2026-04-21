## 1. ArrayList (`java.util.ArrayList`)

A dynamic array that resizes itself automatically.

|**Method**|**Description**|**Time Complexity**|
|---|---|---|
|`add(val)`|Appends an element to the end.|$O(1)$ amortized|
|`add(index, val)`|Inserts an element at the specified index.|$O(n)$|
|`remove(index)`|Removes the element at the index.|$O(n)$|
|`get(index)`|Accesses the element at the index.|$O(1)$|
|`set(index, val)`|Replaces the element at the index.|$O(1)$|
|`size()`|Returns the number of elements.|$O(1)$|
|`isEmpty()`|Checks if the list is empty.|$O(1)$|
|`clear()`|Removes all elements.|$O(n)$|

## 2. String & StringBuilder (`java.lang.String`, `java.lang.StringBuilder`)

**Crucial difference from C++:** Java `String`s are immutable. If you concatenate strings in a loop, it takes $O(n^2)$ time! Always use `StringBuilder` when you need to modify a string frequently.

**String Methods:**

| Method | Description | Time Complexity |
| --- | --- | --- |
| `length()` | Returns the length of the string. | $O(1)$ |
| `charAt(index)` | Returns the character at the index. | $O(1)$ |
| `substring(start, end)` | Returns substring from `start` to `end - 1`. | $O(\text{len})$ |
| `equals(str)` | Compares value (Do NOT use `==` for strings). | $O(n)$ |
| `toCharArray()` | Converts string to a `char[]` array. | $O(n)$ |


**StringBuilder Methods:**

| Method | Description | Time Complexity |
| :--- | :--- | :--- |
| `append(val)` | Appends a value (char, string, int, etc.) to the end. | $O(1)$ amortized |
| `deleteCharAt(index)` | Removes character at the given index. | $O(n)$ |
| `reverse()` | Reverses the sequence of characters. | $O(n)$ |
| `toString()` | Converts the builder back to a standard String. | $O(n)$ |

## 3. Stack (`java.util.Stack`)

A Last-In-First-Out (LIFO) data structure. _(Note: While Java documentation recommends using `ArrayDeque` for stacks, `Stack` remains heavily used in competitive programming for its simple API)._

|**Method**|**Description**|**Time Complexity**|
|---|---|---|
|`push(val)`|Inserts an element at the top.|$O(1)$|
|`pop()`|Removes and returns the top element.|$O(1)$|
|`peek()`|Accesses the top element without removing it.|$O(1)$|
|`size()` / `isEmpty()`|Returns size / checks if empty.|$O(1)$|

## 4. Queue (`java.util.Queue`)

A First-In-First-Out (FIFO) data structure. `Queue` is an interface, so you typically instantiate it using a `LinkedList` or `ArrayDeque`. Example: `Queue<Integer> q = new LinkedList<>();`

|**Method**|**Description**|**Time Complexity**|
|---|---|---|
|`offer(val)`|Inserts an element at the back (same as `add`).|$O(1)$|
|`poll()`|Removes and returns the front element.|$O(1)$|
|`peek()`|Accesses the front element without removing it.|$O(1)$|
|`size()` / `isEmpty()`|Returns size / checks if empty.|$O(1)$|

## 5. PriorityQueue (`java.util.PriorityQueue`)

Provides constant time lookup for the smallest or largest element.

> **Note:** By default, `PriorityQueue<Integer> pq = new PriorityQueue<>();` is a **Min-Heap**. To make a **Max-Heap**, use:
> 
> `PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());`

|**Method**|**Description**|**Time Complexity**|
|---|---|---|
|`offer(val)` / `add(val)`|Inserts an element and maintains heap structure.|$O(\log n)$|
|`poll()`|Removes and returns the top element.|$O(\log n)$|
|`peek()`|Accesses the top element without removing it.|$O(1)$|
|`size()` / `isEmpty()`|Returns size / checks if empty.|$O(1)$|

## 6. HashSet and TreeSet (`java.util.HashSet`, `java.util.TreeSet`)

Collections of unique elements.

- **`HashSet`**: Implemented using a Hash Table. Elements are unsorted.
    
- **`TreeSet`**: Implemented using a Red-Black Tree. Elements are sorted.
    

|**Method**|**Description**|**Complexity (HashSet)**|**Complexity (TreeSet)**|
|---|---|---|---|
|`add(val)`|Adds the element if not already present.|$O(1)$ avg, $O(n)$ worst|$O(\log n)$|
|`remove(val)`|Removes the element from the set.|$O(1)$ avg, $O(n)$ worst|$O(\log n)$|
|`contains(val)`|Returns true if present, false otherwise.|$O(1)$ avg, $O(n)$ worst|$O(\log n)$|
|`ceiling(val)`|Returns least element $\ge$ `val` (like C++ `lower_bound`).|Not Available|$O(\log n)$|
|`higher(val)`|Returns least element $>$ `val` (like C++ `upper_bound`).|Not Available|$O(\log n)$|

## 7. HashMap and TreeMap (`java.util.HashMap`, `java.util.TreeMap`)

Collections of key-value pairs. Keys are unique.

- **`HashMap`**: Unsorted (Hash Table).
    
- **`TreeMap`**: Sorted by keys (Red-Black Tree).
    

|**Method**|**Description**|**Complexity (HashMap)**|**Complexity (TreeMap)**|
|---|---|---|---|
|`put(key, val)`|Inserts or updates the value for a key.|$O(1)$ avg, $O(n)$ worst|$O(\log n)$|
|`get(key)`|Returns the value associated with the key (or `null`).|$O(1)$ avg, $O(n)$ worst|$O(\log n)$|
|`getOrDefault(k, def)`|Returns value for key, or `def` if key doesn't exist.|$O(1)$ avg, $O(n)$ worst|$O(\log n)$|
|`remove(key)`|Removes the key-value mapping.|$O(1)$ avg, $O(n)$ worst|$O(\log n)$|
|`containsKey(key)`|Checks if the key exists.|$O(1)$ avg, $O(n)$ worst|$O(\log n)$|
|`keySet()`|Returns a `Set` view of all keys (used for iterating).|$O(1)$ to get view|$O(1)$ to get view|

---

## The "Pair" Problem in Java

Unlike C++, Java doesn't have a built-in `Pair` class in the standard collections. During interviews and competitive programming, Java developers usually use one of two workarounds:

1. **Custom Class:** `class Pair { int x, y; Pair(int x, int y){ this.x = x; this.y = y; } }`
    
2. **2D Arrays:** Store pairs as `int[]` arrays of size 2. For example, a Queue of pairs: `Queue<int[]> q = new LinkedList<>();` then `q.offer(new int[]{a, b});`
    

---

## Bonus: Utility Classes (`Collections` & `Arrays`)

Instead of C++'s `<algorithm>` header, Java uses static methods in these two utility classes.

- **`Arrays.sort(arr)` / `Collections.sort(list)`**: Sorts in ascending order ($O(n \log n)$).
    
- **`Arrays.fill(arr, val)`**: Fills an entire array with a specific value ($O(n)$). Great for initializing DP tables!
    
- **`Collections.reverse(list)`**: Reverses a List ($O(n)$).
    
- **`Collections.max(list)` / `Collections.min(list)`**: Finds max/min in a List ($O(n)$).
    
---

## Methodologies used in JAVA

### Custom Comparators (The Modern Java Way)

Before Java 8, writing comparators meant creating bulky anonymous inner classes. Now, you should strictly use **Lambda Expressions**. It makes your code clean and concise, which is perfect for interviews.

**Rule of Thumb:** A comparator takes two arguments, `(a, b)`.

- Return a **negative** number if `a` should come before `b`.
    
- Return a **positive** number if `a` should come after `b`.
    
- Return **zero** if they are equal.
    

**Example 1: Sorting a 2D Array (e.g., for "Merge Intervals")**

Let's say you have a 2D array `int[][] intervals` and you want to sort it based on the first element of each row.

Java

```
// Sort by the first element in ascending order
Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));

// Sort by the first element, and if they are equal, sort by the second element descending
Arrays.sort(intervals, (a, b) -> {
    if (a[0] == b[0]) {
        return Integer.compare(b[1], a[1]); 
    }
    return Integer.compare(a[0], b[0]);
});
```

> **Pro Tip:** Always use `Integer.compare(a, b)` instead of simply doing `a - b`. Using `a - b` can cause integer overflow if the numbers are very large and have opposite signs, leading to subtle, hard-to-find bugs.

**Example 2: Custom PriorityQueue (e.g., for Dijkstra's Algorithm or Top K Elements)**

If you want a PriorityQueue to store pairs (as `int[]`) and act as a Min-Heap based on the second value (e.g., the distance or frequency):

Java

```
// Min-Heap based on the second value of the array
PriorityQueue<int[]> pq = new PriorityQueue<>((a, b) -> Integer.compare(a[1], b[1]));
```

---

### Backtracking Pitfall: Reference vs. Value

This is the **number one bug** people write in Java during interviews. In Java, objects are passed by reference value. If you are doing a backtracking problem (like Permutations or Subsets) and you add your temporary list to your final result list, you **must make a deep copy**.

Java

```
// WRONG: You are adding a reference to 'currentPath'. 
// When 'currentPath' changes later, the result inside 'ans' changes too!
ans.add(currentPath); 

// RIGHT: Make a new copy of the list at its current state.
ans.add(new ArrayList<>(currentPath)); 
```

### Fast Input / Output (For Competitive Programming)

If you are doing LeetCode, you don't need to worry about this (they handle I/O for you). But if you are doing Codeforces or HackerRank, `Scanner` and `System.out.print` are too slow and will cause "Time Limit Exceeded" (TLE) errors.

You must use `BufferedReader` and `StringTokenizer` for fast input, and `StringBuilder` or `PrintWriter` for fast output.

Java

```
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
StringTokenizer st = new StringTokenizer(br.readLine());
int n = Integer.parseInt(st.nextToken()); // Fast way to read an integer
```

### Primitives vs. Wrapper Classes

Java has primitives (`int`, `char`, `double`) and their object wrappers (`Integer`, `Character`, `Double`).

- Collections (`List`, `Map`, `Set`, `Queue`) **cannot** hold primitives. You must use `List<Integer>`, not `List<int>`. Java "autoboxes" primitives into wrappers behind the scenes, which adds a slight performance/memory overhead.
    
- **Sorting Gotcha:** `Arrays.sort(arr, Collections.reverseOrder())` **only works on wrapper objects**. It will fail on an `int[]` array. To sort an `int[]` in reverse, you either have to sort it ascending and reverse it manually, or use an `Integer[]` array.
    

### Array Initialization (DP Tables)

For Dynamic Programming, you often need to initialize arrays with specific values (like `-1` or infinity).

- **1D Array:** Use `Arrays.fill(dp, -1);` ($O(n)$ time).
    
- **2D Array:** `Arrays.fill()` doesn't work on the whole 2D grid at once. You have to loop through the rows:
    

Java

```
int[][] dp = new int[n][m];
for (int[] row : dp) {
    Arrays.fill(row, -1);
}
```

### The Math Class

Memorize the static methods in `java.lang.Math`. You will use these constantly:

- `Math.max(a, b)` / `Math.min(a, b)`
    
- `Math.abs(a)` (Absolute value)
    
- `Math.pow(base, exponent)` (Returns a `double`, so cast to `int` if needed: `(int) Math.pow(2, 3)`)
    
- `Math.ceil()` / `Math.floor()`
    
