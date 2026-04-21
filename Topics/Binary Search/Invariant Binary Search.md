# The `[T, T, F, F]` Template #binary-search

## 1. Core Philosophy

Traditional binary search looks for a **specific target value**. Invariant Binary Search looks for a **boundary between two states**.

Instead of asking _"Is this element equal to X?"_, you ask _"Does this element satisfy a specific condition?"_ This splits your search space into two contiguous blocks — a block of `True` and a block of `False`. The goal is to find where `True` turns into `False` (or vice versa).

---

## 2. The Universal Template (C++)

cpp

```cpp
// 1. Define the search space safely OUTSIDE the possible valid indices/values
long long low  = MIN_POSSIBLE_VALUE - 1;
long long high = MAX_POSSIBLE_VALUE + 1;

// 2. The invariant loop
while (high - low > 1) {
    long long mid = low + (high - low) / 2;

    // 3. The predicate function
    if (isGood(mid)) {
        low = mid;   // mid is 'Good' — move the Good pointer here
    } else {
        high = mid;  // mid is 'Bad'  — move the Bad pointer here
    }
}

// 4. Extract the answer
// low  → boundary element of the 'Good' state
// high → boundary element of the 'Bad' state
return low; // (or return high, depending on what the question asks)
```

---

## 3. When to Use It

If a problem contains any of these phrases, it is almost certainly a Binary Search on Answer problem:

- **"Find the maximum of the minimums..."** — e.g., maximize the minimum distance between cows in stalls.
- **"Find the minimum of the maximums..."** — e.g., minimize the maximum pages a student reads.
- **"Find the first / last occurrence..."** — in a sorted array.
- **"What is the minimum time/cost to achieve X?"** — where more time/cost always guarantees achieving X.

---

## 4. How to Identify the States

Map the problem to a boolean array. Write out 5 dummy elements to see the pattern before coding.

### Scenario A — "Last Valid" (`T T T F F`)

> _Example:_ You can carry up to W weight. What is the heaviest item you can pick from a sorted list?
> 
> Array: `[Can Carry, Can Carry, Can Carry, Cannot Carry, Cannot Carry]`

- `low` tracks `True` (Can Carry), `high` tracks `False` (Cannot Carry).
- You want the **last `True`**, so return `low`.

### Scenario B — "First Valid" (`F F F T T`)

> _Example:_ You need at least K power to defeat a boss. What is the weakest weapon strong enough from a sorted inventory?
> 
> Array: `[Too Weak, Too Weak, Too Weak, Strong Enough, Strong Enough]`

- `low` tracks `False` (Too Weak), `high` tracks `True` (Strong Enough).
- You want the **first `True`**, so return `high`.

---

## 5. Golden Rules of Initialization

- **Never initialize `low = 0` or `high = n-1` without manually verifying those boundary values.**
- Always initialize out of bounds — e.g., `low = -1`, `high = n` for an array of size N.
- **Why?** If the entire array is `[False, False, False]`, setting `low = 0` falsely assumes index 0 is `True`. Setting `low = -1` lets the pointers resolve safely without a false positive.

---

## 6. When NOT to Use It

### Non-monotonic search spaces

If `isGood()` evaluates to `[True, False, True, False]`, binary search will fail — the states **must** be contiguous. You usually need to sort first, or switch to a different algorithm (e.g., Ternary Search for peaks/valleys on a parabola).

### Predicate function is too slow

If `isGood(mid)` is O(N²) and your search space is 10⁹, total complexity becomes O(N² log 10⁹) — this will TLE on HackerEarth. Your `isGood()` needs to be O(N) or O(1). Precompute a prefix sum array or use a hashmap to make verification fast.

### Floating-point precision problems

If the answer requires exact decimal precision (e.g., a radius to 10⁻⁶), the condition `while (high - low > 1)` breaks down because decimals don't take integer steps. Use a fixed-iteration loop instead:

cpp

```cpp
for (int i = 0; i < 100; i++) {
    double mid = low + (high - low) / 2.0;
    // ... rest of logic
}
```