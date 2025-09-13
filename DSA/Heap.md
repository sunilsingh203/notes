# 📌 Heaps (Priority Queue) — Interview Notes

---

## 🔹 What is a Heap?

- A **complete binary tree** (all levels filled except possibly last, filled left → right).
    
- Heap property:
    
    - **Min Heap** → Parent ≤ Children (root = smallest element).
        
    - **Max Heap** → Parent ≥ Children (root = largest element).
        
- Implementation in Java:
    
    - Built-in: `PriorityQueue` (default = **Min Heap**).
        
    - For **Max Heap** → use comparator:
        
        `PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());`
        

---

## PriorityQueue (Java Heap) — Key Methods

The `PriorityQueue` class (java.util) is the standard heap implementation in Java (default = **Min Heap**).

### Construction

`PriorityQueue<Integer> minHeap = new PriorityQueue<>();  // Min Heap PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder()); // Max Heap`

### Methods

| Operation  | Method                | Description                                                  | Time Complexity                      |
| ---------- | --------------------- | ------------------------------------------------------------ | ------------------------------------ |
| Insert     | `add(e)` / `offer(e)` | Inserts element into heap.                                   | **O(log n)**                         |
| Get Top    | `peek()`              | Returns root without removing.                               | **O(1)**                             |
| Extract    | `poll()`              | Removes + returns root.                                      | **O(log n)**                         |
| Delete     | `remove(e)`           | Removes a specific element.                                  | **O(n)** (search + adjust)           |
| Search     | `contains(e)`         | Checks if element exists.                                    | **O(n)**                             |
| Size       | `size()`              | Returns number of elements.                                  | **O(1)**                             |
| Empty?     | `isEmpty()`           | Checks if heap is empty.                                     | **O(1)**                             |
| Clear      | `clear()`             | Removes all elements.                                        | **O(n)**                             |
| Iterator   | `iterator()`          | Iterates through heap (no order guarantee).                  | **O(n)**                             |
| Bulk Add   | `addAll(Collection)`  | Adds all elements from a collection.                         | **O(m log(n+m))** (m = new elements) |
| Comparator | `comparator()`        | Returns comparator used for ordering (null = natural order). | **O(1)**                             |

---

## 🔹 When to Use Which Heap?

1. **Find k-th smallest element** → **Max Heap** of size k  
    (keep k smallest elements, top = k-th smallest).
    
2. **Find k-th largest element** → **Min Heap** of size k  
    (keep k largest elements, top = k-th largest).
    
3. **Top k frequent elements** → Min Heap of size k (store by frequency).
    
4. **Median of a data stream** → Two Heaps (Max Heap for left half, Min Heap for right half).
    
5. **Merge k sorted lists/arrays** → Min Heap (store smallest among heads).
    
6. **Running maximum/minimum in sliding window** → Heap + Lazy deletion (but usually deque is better).
    

---

## 🔹 Java Implementation Examples

![[Pasted image 20250909125123.png]]
![[Pasted image 20250909125135.png]]
![[Pasted image 20250909125147.png]]

![[Pasted image 20250909125159.png]]


## 🔹 Heap vs PriorityQueue vs TreeMap

- **Heap** → abstract concept (tree).
    
- **PriorityQueue** → Java implementation (heap-based).
    
- **TreeMap** → BST (log n), also usable for priority problems but slower in some cases.
    

---

## 🔹 Key Interview Patterns

✅ **K-th element problems** → Heap of size k  
✅ **Running min/max / Median** → Two heaps  
✅ **Top K problems** → Min Heap (by frequency/value)  
✅ **Merge k sorted arrays** → Min Heap of size k  
✅ **Heap Sort** → Build Max Heap → Repeated extract

---

## 🔹 Quick Complexity Cheatsheet

- Insert → O(log n)
    
- Delete Top → O(log n)
    
- Build Heap (heapify all at once) → O(n)
    
- Heap Sort → O(n log n)
    

---

⚡Tip for Interviews:

- Always think: "Am I asked for **k smallest / largest / frequent**?" → Heap is the tool.
    
- **Identify**: if question says _smallest, largest, k-th_, or _streaming median_, **100% it’s Heap**.





