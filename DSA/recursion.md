# 📝 Recursion & Backtracking Notes for Interviews

---

## 1. **Recursion Basics**

- **Recursion** = a function calls itself with smaller subproblems until a base case is reached.
    
- Typical problems:
    
    - Factorial, Fibonacci
        
    - Tree traversal
        
    - Divide & conquer (binary search, merge sort)

![[Pasted image 20250912065029.png]]
## 2. **Backtracking**

- Backtracking = recursion + undo step.
    
- Used when we **explore all possible paths** but need to **revert decisions**.
    
- Common in:
    
    - Subsets / subsequences
        
    - Permutations / combinations
        
    - N-Queens, Sudoku
        
    - Word search in grid
![[Pasted image 20250912065054.png]]
## 3. **Key Patterns in Recursion & Backtracking**

### 🔹 Pattern 1: **Subsequence / Subset Generation**

- **Question Type**: “Find all subsequences/subsets.”
    
- Idea: At each index → choose **include** or **exclude**.
    
- **Template**:
- ![[Pasted image 20250912065113.png]]
- **Examples**:
    
    - Subsets (LeetCode 78)
        
    - Subsets II (with duplicates, LeetCode 90)
        
    - Subsequences sum to K (classic)
        

---

### 🔹 Pattern 2: **Combinations (Choose k out of n)**

- **Question Type**: “Pick k numbers / combination sum.”
    
- Idea: Explore with a start index, choose or skip.
    
- **Template**:![[Pasted image 20250912065135.png]]
- **Examples**:
    
    - Combinations (LeetCode 77)
        
    - Combination Sum (LeetCode 39, 40)
        

---

### 🔹 Pattern 3: **Permutations**

- **Question Type**: “Find all arrangements/orderings.”
    
- Idea: Use visited[] array or swap elements.
    
- **Template (visited array)**:![[Pasted image 20250912065158.png]]
- **Examples**:
    
    - Permutations (LeetCode 46)
        
    - Permutations II (with duplicates, LeetCode 47)
        
    - Letter Tile Possibilities (LeetCode 1079)
        

---

### 🔹 Pattern 4: **Grid/Matrix Search (DFS Backtracking)**

- **Question Type**: “Find path in grid / word search.”
    
- Idea: At each cell, explore 4 directions, mark visited, backtrack.
    
- **Template**:![[Pasted image 20250912065222.png]]
- - **Examples**:
    
    - Word Search (LeetCode 79)
        
    - Rat in a Maze
        
    - N-Queens (chessboard)
        

---

### 🔹 Pattern 5: **Partitioning / Palindrome Problems**

- **Question Type**: “Partition string into valid parts.”
    
- Idea: Try cutting string at every index, check validity, recurse.
    
- **Template**:
![[Pasted image 20250912065242.png]]
- **Examples**:
    
    - Palindrome Partitioning (LeetCode 131)
        
    - Restore IP Addresses (LeetCode 93)
        

---

## 4. **When to Apply Recursion/Backtracking**

Use it if:

1. You need **all possible solutions** (not just one).
    
2. The problem involves:
    
    - Generating subsequences/subsets/combinations/permutations.
        
    - Traversing trees/graphs/grid in **all possible paths**.
        
    - Constraint satisfaction problems (N-Queens, Sudoku).
        
    - String partitioning/cutting problems.
        

---

## 5. **Interview Tips**

- Always **define base case** clearly.
    
- Think in terms of **“Choose → Explore → Un-choose”**.
    
- Use **pruning** to cut unnecessary paths (e.g., if sum > target).
    
- Dry run on a small example before coding.
- ![[Pasted image 20250912065317.png]]
# 📘 Notes on Pick / Non-Pick Pattern in Recursion (Java Focus)

---

## 🔑 Core Idea

- At **each index**, we have **two choices**:
    
    1. **Pick** → include the current element in the subsequence.
        
    2. **Not Pick** → exclude the current element from the subsequence.
        
- This results in a **binary recursion tree** → 2n2^n2n subsequences for an array/string of length `n`.
    
- This is the **foundation** for solving:
    
    - **Subsequences**
        
    - **Subsets (Power Set)**
        
    - **Subset Sum / Target Sum**
        
    - **Knapsack variations**
        
    - **Partition problems**
        
    - **String subsequence problems**
        

---

## 🌳 Recursion Tree Example

For `arr = [1,2]`
![[Pasted image 20250912210852.png]]

![[Pasted image 20250912210908.png]]


## 📝 Types of Problems (and Java Examples)

### 1. **Print All Subsequences**

👉 Direct template above.

![[Pasted image 20250912210929.png]]

![[Pasted image 20250912210942.png]]

![[Pasted image 20250912210955.png]]


![[Pasted image 20250912211005.png]]

## 🧠 Time Complexity

- **O(2^n)** calls (each element → pick or not pick).
    
- Printing each subsequence adds **O(n)**, so worst-case printing = **O(n·2^n)**.
    

---

## 🎯 Common Interview Variations

1. **Basic subsequences**
    
    - Print / Count all subsequences.
        
    - String subsequences.
        
2. **Sum-based**
    
    - Count subsequences with sum = K.
        
    - Print only one subsequence with sum = K.
        
    - Subset sum existence.
        
3. **Subset-related**
    
    - Generate power set.
        
    - Partition into equal sum subsets.
        
    - Unique subsets (handle duplicates with sorting + skip logic).
        
4. **String-based**
    
    - Subsequences forming palindrome.
        
    - Subsequences that match a given pattern.
        
    - Longest subsequence (turns into DP).
        
5. **Optimization / Early Exit**
    
    - Stop when condition satisfied (boolean return).
        

---

## 📌 Key Takeaways

- Pick/Not-Pick is **root pattern** for subsequence & subset questions.
    
- Every element → **2 choices**, giving 2n2^n2n results.
    
- **Always think Pick/Not-Pick** when:
    
    - Asked to generate all subsequences/subsets.
        
    - Problem says "choose or not choose each element".
        
    - Conditions involve sums, lengths, or matching subsequences.
# 📘 Notes: When Only **One Subsequence** is Needed (Pick / Non-Pick Recursion)

---

## 🔑 Key Idea

- Normally, Pick/Not-Pick explores **all paths** → generates **all subsequences**.
    
- But if you only need **one valid subsequence**, you can **stop recursion early**.
    
- Technique:
    
    - Use **boolean return value**.
        
    - When a valid subsequence is found, return `true` to stop further recursion.
        

---

## 🌳 Recursion Tree (Example: arr = [1, 2, 1], target = 2)

We want **any one subsequence** that sums to 2.
![[Pasted image 20250912215128.png]]

![[Pasted image 20250912215148.png]]
## 📝 Observations

1. **Why boolean return?**
    
    - To **propagate success upwards** in recursion and stop unnecessary exploration.
        
2. **Order of exploration matters**
    
    - If you `Pick` first, you may find `[1,1]` before `[2]`.
        
    - If you `Not Pick` first, you may find `[2]` before `[1,1]`.
        
3. **Time Complexity**
    
    - Worst case still O(2n)O(2^n)O(2n).
        
    - But early exit reduces practical runtime.
        

---

## 🎯 Variations in Interviews

1. **Find one subsequence with sum = K** ✅  
    (Most common variation).
    
2. **Find one subsequence with length = L**
    
    - Add `if (current.size() == L)` check.
        
3. **Find one subsequence that satisfies condition**
    
    - Example: palindrome subsequence, subsequence containing certain characters, etc.
        
4. **Decision problems**
    
    - Instead of printing, just return `true/false` → “Does such a subsequence exist?”
        
    - This is **Subset Sum Problem (recursive form).**
        

---

## 📌 Key Takeaways

- Use **boolean return type** to stop recursion when one valid subsequence is found.
    
- This is a **huge optimization** over printing all subsequences.
    
- Useful in:
    
    - Subset Sum (existence check).
        
    - Target subsequence search.
        
    - Early exit conditions.

# 📘 Notes: Returning Count of Subsequences

## 🔑 Key Concept

- For an array/string of size **n**, the **total number of subsequences = 2ⁿ**.  
    👉 Because for each element you have **2 choices**:
    
    1. **Pick** it
        
    2. **Not Pick** it
        
- If the problem asks for **all subsequences count**, direct formula `2ⁿ` is enough.
    
- If the problem has a **condition** (e.g., subsequences with sum = target, subsequences with product ≤ K, subsequences with only vowels, etc.), then recursion/DP is required.

![[Pasted image 20250913135119.png]]
## 📝 Interview Notes

1. **When to use `2ⁿ` formula**
    
    - When no condition is given, just total count.
        
2. **When to use recursion/DP**
    
    - When a constraint is given (sum, product, lexicographic order, etc.).
        
3. **Complexity**
    
    - Simple recursion = O(2ⁿ) (because exploring all subsequences).
        
    - DP optimization possible in problems like _subset sum, count subsets with given sum_ → reduces to O(n × target).
        
4. **Base Case Trick**
    
    - For pure counting: return 1 when index == n (empty subsequence counts).
        
    - For conditional counting: return 1 only if condition satisfied, else 0.
        

---

✅ In short:

- **Total count** = `2ⁿ`.
    
- **Conditional count** → recursion with **pick / not pick**.
    
- Convert to **DP** if constraints are large.
