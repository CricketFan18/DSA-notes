When you read a problem statement, look for these specific triggers. If you see them, your brain should immediately switch to "DP Mode."

- **The Optimization Trigger:** The problem asks for the **maximum**, **minimum**, **longest**, or **shortest** of something, BUT the rules have weird constraints that prevent you from just sorting the array or picking the biggest numbers.
    
- **The Combinatorics Trigger:** The problem asks for the **"number of ways"** to do something or reach a goal. (Bonus clue: If it says _"Output the answer modulo 10^9 + 7"_, it is almost guaranteed to be a DP or advanced math problem because the answer is too massive to fit in a 64-bit integer).
    
- **The "No Going Back" Trigger:** The problem forces you to move in a specific direction (e.g., left to right through an array, top-left to bottom-right in a grid, or time moving forward). DP relies on moving in one direction so you can build on past answers.
    

## The Constraint Cheat Code

In competitive programming, the input constraints (`N`) practically give away the required time complexity, which tells you exactly what kind of DP array you need to build.

- **If N is around 100,000 (10^5):** * You need an $O(N)$ solution.
    
    - **The Pattern:** This is almost always a **1D DP**. You will likely need a single array `dp[N]` and a single `for` loop, exactly like _Boredom_ and _Cut Ribbon_.
        
- **If N is around 1,000 to 5,000:**
    
    - You need an $O(N^2)$ solution.
        
    - **The Pattern:** This is usually a **2D DP**. You will need a matrix `dp[N][N]` and nested `for` loops. Example: "Given two strings of length 1000, find the longest common subsequence."
        
- **If N is tiny (like 15 to 20):**
    
    - You need an $O(2^N)$ solution.
        
    - **The Pattern:** This is **Bitmask DP**. You use binary numbers to represent which items you have taken/visited.
        

---

## The Three Basic DP Archetypes

At the 1300–1500 rating level, almost every DP problem is just one of these three classic patterns wearing a disguise.

#### Archetype A: "Take it or Leave it" (0/1 Knapsack variations)

- **The Setup:** You are iterating through an array. At every single index, you must make a binary choice: Do I include this item or skip it?
    
- **The Catch:** Taking an item costs a resource (weight, money) or triggers a penalty (like deleting neighbors in _Boredom_).
    
- **The DP State:** `dp[i]` = the maximum profit using only items from index 1 to `i`.
    
- **The Transition:** `dp[i] = max(dp[i-1] /* skip */, dp[i-2] + value[i] /* take */)`
    

#### Archetype B: "The Pathfinder" (Number of Ways)

- **The Setup:** You are navigating a grid or a set of stairs. You want to know how many distinct ways you can reach the end.
    
- **The Catch:** Some squares are broken/blocked, or you can only move right and down.
    
- **The DP State:** `dp[i][j]` = the number of ways to reach cell `(i, j)`.
    
- **The Transition:** Since you can only arrive at `(i, j)` from the top or the left, the number of ways to get there is just the sum of the ways to get to the adjacent cells: `dp[i][j] = dp[i-1][j] + dp[i][j-1]`.
    

#### Archetype C: "The Builder / Breaker" (Unbounded Knapsack)

- **The Setup:** You have a total capacity `N`, and you can use an unlimited amount of specific pieces to build or break it perfectly.
    
- **The Catch:** You must reach exactly `N` without going over or leaving remainders (like _Cut Ribbon_).
    
- **The DP State:** `dp[i]` = the best answer for exactly capacity `i`.
    
- **The Transition:** Look back at your valid pieces. `dp[i] = max(dp[i-a], dp[i-b], dp[i-c]) + 1`.
    

---

## Your Contest Execution Blueprint

When the contest clock is ticking and you suspect DP, **do not touch your keyboard yet**. Grab a piece of paper and answer these three questions strictly in English. If you can't say it in English, you can't code it in C++.

1. **Define the State (The English Dictionary):** Write down exactly what `dp[i]` means.
    
    - _Good:_ "dp[i] is the minimum cost to reach stair i."
        
    - _Bad:_ "dp[i] is the answer." (Too vague, you will confuse yourself).
        
2. **Find the Base Case (The Anchor):** What is the absolute smallest, most trivial version of the problem?
    
    - "If I am at stair 0, the cost is 0." -> `dp[0] = 0`.
        
3. **Find the Transition (The Time Machine):** Pretend you are sitting at index `i`. Assume, by pure magic, that all previous `dp` values (`i-1`, `i-2`, etc.) are already perfectly correct. How do you calculate `i` using only those past answers?
    

Once you write those three things on paper, the C++ practically writes itself. You just wrap a `for` loop around your transition formula.

Start looking at the 1400-1500 rated problems with the "dp" tag. Try to just read the problems and guess which of the 3 Archetypes they belong to before you even try to solve them!