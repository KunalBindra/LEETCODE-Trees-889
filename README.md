# LEETCODE-Trees-889
---

### **Understanding the Algorithm**
- `preorder`: **Root → Left → Right**
- `postorder`: **Left → Right → Root**
- The idea is to recursively construct the tree by taking nodes from `preorder` and matching them with `postorder`.

### **Code Walkthrough**
#### **Initialization**
- `pri = 0`: Tracks the index in `preorder` (root is always the first element).
- `poi = 0`: Tracks the index in `postorder` (root is always the last element).

#### **Recursive Construction**
1. Create a node with `preorder[pri]`.
2. If the current node's value **does not** match `postorder[poi]`, recursively build the left subtree.
3. If the current node's value **still does not** match `postorder[poi]`, recursively build the right subtree.
4. Finally, increment `poi` because that node is processed.

---

### **Dry Run Example**
#### **Input**
```java
preorder  = [1, 2, 4, 5, 3, 6, 7]
postorder = [4, 5, 2, 6, 7, 3, 1]
```

#### **Step-by-Step Execution**
| Step | `pri` | `poi` | Action |
|------|------|------|--------|
| 1 | 0 → 1 | 0 | Create root: `1` |
| 2 | 1 → 2 | 0 | Create left child: `2` |
| 3 | 2 → 3 | 0 | Create left child: `4` |
| 4 | - | 0 → 1 | Base case: return `4` |
| 5 | 3 → 4 | 1 | Create right child: `5` |
| 6 | - | 1 → 2 | Base case: return `5` |
| 7 | - | 2 → 3 | Return `2` to parent (`1`) |
| 8 | 4 → 5 | 3 | Create right child: `3` |
| 9 | 5 → 6 | 3 | Create left child: `6` |
|10 | - | 3 → 4 | Base case: return `6` |
|11 | 6 → 7 | 4 | Create right child: `7` |
|12 | - | 4 → 5 | Base case: return `7` |
|13 | - | 5 → 6 | Return `3` to parent (`1`) |
|14 | - | 6 → 7 | Return `1` |

---

### **Constructed Tree**
```
        1
       / \
      2   3
     / \  / \
    4   5 6  7
```

---
### **Final Notes**
- This approach constructs the tree recursively using preorder for node selection and postorder for validation.
- The time complexity is **O(N)** since each node is processed once.
- The space complexity is **O(N)** for recursion stack in the worst case.
