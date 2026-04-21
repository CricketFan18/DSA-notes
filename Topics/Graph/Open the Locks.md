![[Pasted image 20260317170028.png]]
## Simplified Intuition: The "Ripples in a Pond"

Imagine you drop a stone into a still pond. The water creates a circular ripple that expands outward.

- The **center** where the stone hit is your starting combination `"0000"`.
    
- The **first ripple** represents every combination you can reach in exactly **1 move**.
    
- The **second ripple** represents every combination reachable in **2 moves**, and so on.
    

Because the ripple expands uniformly, the **first time** the water touches a specific leaf or rock (your `target`), you know for a fact that is the shortest distance the water had to travel to get there. It didn't "wander" around; it took the most direct route outward.

### The "Deadends" Analogy

In this pond, the **deadends** are like wooden posts sticking out of the water. The ripples can't pass through them. The water has to flow _around_ the posts to reach the target, which might make the "shortest path" longer than it would be in an empty pond.

---

## Technical Explanation

In technical terms, you are treating the lock as an **Unweighted Undirected Graph**.

- **Nodes:** All 10,000 possible strings from `"0000"` to `"9999"`.
    
- **Edges:** An edge exists between two nodes if they differ by exactly one "click" of one wheel (accounting for the $0 \leftrightarrow 9$ wrap-around).
    
- **Shortest Path:** Since every edge has a "weight" of 1, **Breadth-First Search (BFS)** is the optimal algorithm. Unlike Depth-First Search (DFS), which explores one branch as deep as possible, BFS explores all neighbors at the current depth before moving deeper.
    

### The "State Space" Search

The collection of all possible combinations is called the **State Space**. Your algorithm is a "State Space Search." You move from the current state to a neighboring state using a transition function (`generateNeighbours`).

---

## 3. Real-World Example: GPS Navigation

Think of your BFS like a GPS calculating a route through a city grid:

1. **Current Location:** `"0000"`
    
2. **Target Destination:** `"3008"`
    
3. **Roadblocks:** `deadends` (Construction zones)
    
4. **The Engine:** The GPS doesn't just guess one road; it looks at all immediate intersections, then all intersections connected to those, until it finds the destination.
    

---

## 4. Key Takeaways of this Approach

|**Concept**|**Why it Matters in this Problem**|
|---|---|
|**Optimality**|BFS guarantees the **shortest path** in unweighted graphs. If you find the target, you stop immediately.|
|**Cycle Detection**|Using a `visited` set is critical. Without it, you'd rotate wheel 1 up, then down, then up, infinitely looping between `"0000"` and `"1000"`.|
|**Layered Exploration**|By processing the queue level by level (using the distance `d` in your `Node`), you ensure you don't skip over a closer path.|
|**Early Exit**|Checking the `target` as soon as you "poll" a node allows you to exit the search as early as possible.|
|**Deadend Pre-processing**|Treating deadends as "already visited" nodes is a clever trick to simplify the logic—it turns a "restriction" into a standard "graph boundary."|
