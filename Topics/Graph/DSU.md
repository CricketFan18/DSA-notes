![[Pasted image 20260316181732.png]]

### Intuition

Imagine a room full of strangers. Initially everyone is their own leader.

* **Union(a, b) :**
  If person A and person B decide to become friends and form a group, then one will make another person his leader. 
  If person A wants to join an already formed group B then person A will follow group B. 
  If group A and group B decide to merge then, smaller group will be merged into bigger group.
* **Find(x) :** Find the ultimate leader of person. Path compression makes it amortized O(1);

---
### Key Takeaways in the Approach

- **Representative Logic:** You don't need to know the full structure of a group; you only need to know who the "boss" is.
    
- **Amortized Efficiency:** DSU is a "lazy" data structure. It doesn't keep everything perfect all the time; it fixes the structure _only when you perform a search_.
    
- **Indirection:** By using an array to store "pointers" to parents, we can represent complex connectivity without a heavy object-oriented graph structure.
    
- **Cycle Detection:** DSU is the go-to tool for detecting cycles in undirected graphs. If you try to `union(x, y)` and find they _already_ have the same root, you’ve found a cycle.


