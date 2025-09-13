# 📘 Greedy Algorithm Notes for DSA (LeetCode + Interviews)

---

## 🔹 1. What is a Greedy Algorithm?

- **Definition**: A greedy algorithm builds up a solution step by step, always choosing the option that offers the most immediate benefit (locally optimal choice), hoping it leads to the global optimum.
    
- **Key Idea**: "Take the best option available at the moment."
    
- **When It Works**: Only when the problem has:
    
    1. **Greedy-choice property** – a global solution can be reached by choosing local optimum.
        
    2. **Optimal substructure** – problem can be broken down into smaller subproblems.
        

---

## 🔹 2. Theory Summary

|Concept|Explanation|
|---|---|
|**Optimal Substructure**|The optimal solution to the problem can be formed using optimal solutions of its subproblems.|
|**Greedy Choice Property**|Making the locally optimal choice at each step leads to the globally optimal solution.|
|**Difference from DP**|DP explores all possible solutions with overlapping subproblems, Greedy just picks the best at each step.|
|**Pitfall**|Greedy doesn’t always work! Must prove correctness (usually via exchange argument).|

---

## 🔹 3. Common Problem Types (LeetCode + Interviews)

|Category|Example Problems|Greedy Strategy|
|---|---|---|
|**Interval Scheduling**|435. Non-overlapping Intervals, 452. Min Arrows to Burst Balloons|Sort intervals (by start or end) and pick greedily.|
|**Activity Selection**|Classic activity selection|Sort by finishing time, always pick earliest finishing job.|
|**Job Scheduling**|630. Course Schedule III|Sort by deadline, use heap to keep feasible jobs.|
|**Task Scheduling**|621. Task Scheduler|Count frequencies, use max-heap / greedy placement.|
|**Minimum/Maximum Sum**|455. Assign Cookies, 135. Candy|Sort + assign smallest valid resource.|
|**String Problems**|316. Remove Duplicate Letters|Stack + greedy lexicographic choice.|
|**Graph Problems**|Prim’s, Kruskal’s for MST|Pick minimum edge without cycle (Kruskal) / lowest weight expansion (Prim).|
|**Coin Change (Greedy)**|Works with canonical coins (1, 5, 10, 25), but fails for arbitrary denominations.|Always take largest coin first.|

---

## 🔹 4. Greedy Patterns & Java Templates

### ✅ Pattern 1: Sort + Choose
![[Pasted image 20250910230341.png]]

![[Pasted image 20250910230353.png]]
![[Pasted image 20250910230406.png]]

![[Pasted image 20250910230417.png]]


![[Pasted image 20250910230429.png]]


## 🔹 5. Steps to Solve Greedy Problems in Interviews

1. **Identify choice property** → Is local optimal leading to global optimal?
    
2. **Try sorting or heap** → Most greedy problems are sort + linear scan OR heap based.
    
3. **Check counterexample** → If greedy fails, may need DP.
    
4. **Use Exchange Argument Proof** → Justify correctness (replace a bad choice with greedy one).
    
5. **Implement cleanly in Java** → Use sorting, `PriorityQueue`, or two pointers.
    

---

## 🔹 6. Quick Greedy Cheat-Sheet

| Problem Type        | Template/Strategy                           |
| ------------------- | ------------------------------------------- |
| Interval / Activity | Sort by end, pick earliest finishing        |
| Task Scheduling     | Max heap / math formula                     |
| Course Schedule     | Sort by deadline + heap                     |
| Candy / Gas Station | Forward & backward pass / greedy accumulate |
| Assign Cookies      | Sort + two pointers                         |
| Remove Letters      | Stack + greedy lexicographic                |
| MST                 | Kruskal (sort edges) / Prim (PQ)            |
