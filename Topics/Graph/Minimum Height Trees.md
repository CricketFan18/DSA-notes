## Visualization
![[Pasted image 20260316171849.png]]
### Intuition

Suppose there are beads connected by string. To form the minimum height, you would want to pickup the bead which lies at the center. The branches spread out more evenly and the distance to each node is minimized.
There could not be more than 2 centers because, if there are 3 nodes, then the node in the middle of 3, will be the most centered node among them.

_In graph theory, the longest path between any two nodes is called the **diameter**. The nodes that could serve as roots for a Minimum Height Tree are the midpoints of that diameter._

**Example:** Suppose a group of small towns want to construct a hospital so that distance from each town to hospital is minimized. To make sure the ambulance reaches the most furthest town in minimum possible time, the hospital should be built at the most central town.

### Approach: Peeling the Onion

The most effective way to find the center is to work from the outside in.

1. **Identify the Leaves:** Find all nodes that only have one connection (degree 1).
    
2. **Trim the Layers:** Remove all those leaf nodes simultaneously.
    
3. **Repeat:** Once the outer layer is gone, new nodes will now become "leaves" (because their connections were cut).
    
4. **The Core:** Keep "peeling" these layers until you are left with only **one or two nodes**. These remaining nodes are your centroids—the roots of your Minimum Height Trees.
    

---

### Technical Deep Dive: Topological Sort Variation

While we often use BFS for shortest paths, MHT is solved using a strategy similar to **Kahn’s Algorithm** (Topological Sort), but applied to an undirected graph.

#### 1. The Degree Constraint

In an undirected tree, a leaf is any node with `degree == 1`. We track the degree of every node using an adjacency list.

#### 2. The Trimming Process

We use a queue to store all current leaves. We then process the queue level by level:

- For each leaf, find its only neighbor.
    
- Decrement the neighbor's degree.
    
- If the neighbor's degree becomes 1, it is now a leaf for the next "layer" and is added to a new queue.
    

#### 3. The Termination Logic

A tree can have at most **two** centroids. If you have more than two nodes remaining, you haven't reached the center yet. We continue the process until `total_nodes <= 2`.
    

---

### Key Takeaways in the Approach

- **Distance Minimization:** The problem is a "Minimax" problem—you are minimizing the maximum distance to any leaf.
    
- **Convergence from Boundaries:** Instead of starting from a random node and searching outward (which would be $O(N^2)$ if done for every node), we start from all boundaries and converge inward ($O(N)$).
    
- **Centroid Limit:** A critical realization is that a tree can only have **one or two** middle points. If it had three in a line, the middle of those three would be a better root than the other two.
    
- **Degree Tracking:** The "degree" of a node is the mechanical lever used to identify when a node has become peripheral.
