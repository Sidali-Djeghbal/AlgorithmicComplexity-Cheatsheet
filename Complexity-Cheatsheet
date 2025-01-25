# Algorithmic Complexity Cheatsheet

## 1. Introduction
- **Definition**: Algorithmic complexity measures the resources (time and space) required by an algorithm as a function of input size.
- **Importance**:
  - Evaluates algorithm performance.
  - Helps anticipate limitations and choose efficient solutions.
  - Facilitates comparison between algorithms solving the same problem.

---

## 2. Qualities of a Good Algorithm
1. **Precision**: Produces correct and expected results for all inputs.
2. **Simplicity**: Easy to understand and maintain.
3. **Robustness**: Handles edge cases and unexpected inputs gracefully.
4. **Modularity**: Composed of reusable, independent modules.
5. **Efficiency**: Optimized for time and memory usage (focus of this chapter).

---

## 3. Algorithmic Complexity
### Types of Complexity
1. **Temporal Complexity**: Time taken based on the number of basic operations (e.g., additions, multiplications).
2. **Spatial Complexity**: Memory required to process the input (e.g., array storage).

### Key Notations
- **Big-O (O)**: Upper bound (worst case).
- **Omega (Ω)**: Lower bound (best case).
- **Theta (Θ)**: Tight bound (average case).

---

## 4. Rules for Calculating Complexity
1. **Elementary Operations**: O(1) for each operation.
2. **Sequential Instructions**: Add complexities (e.g., O(f(n)) + O(g(n))).
3. **Conditional Statements**: Take the maximum complexity (e.g., max(O(f(n)), O(g(n)))).
4. **Loops**:
   - For loops: Multiply iterations by the body complexity (e.g., O(n) loop with O(1) body = O(n)).
   - Nested loops: Multiply complexities of each loop.
5. **Recursion**: Solve recurrence relations (e.g., divide-and-conquer methods).

---

## 5. Examples of Complexity Types
### 5.1 Linear Complexity (O(n))
- **Example**: Linear search in an array.
- **Code**:
```c
int linear_search(int *arr, int size, int value) {
    for (int i = 0; i < size; i++) {
        if (arr[i] == value) return i;
    }
    return -1;
}
```

### 5.2 Constant Complexity (O(1))
- **Example**: Accessing an array element by index.
- **Code**:
```c
int access_element(int *arr, int index) {
    return arr[index];
}
```

### 5.3 Logarithmic Complexity (O(log n))
- **Example**: Binary search in a sorted array.
- **Code**:
```c
int binary_search(int *arr, int size, int value) {
    int low = 0, high = size - 1;
    while (low <= high) {
        int mid = (low + high) / 2;
        if (arr[mid] == value) return mid;
        else if (arr[mid] < value) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}
```

### 5.4 Quadratic Complexity (O(n²))
- **Example**: Nested loops for pair comparisons.
- **Code**:
```c
void print_pairs(int *arr, int size) {
    for (int i = 0; i < size; i++) {
        for (int j = i + 1; j < size; j++) {
            printf("(%d, %d)\n", arr[i], arr[j]);
        }
    }
}
```

### 5.5 Exponential Complexity (O(2ⁿ))
- **Example**: Recursive subset generation.

---

## 6. Best, Worst, and Average Cases
- **Best Case** (Ω): Minimum resource usage (e.g., first element found).
- **Worst Case** (O): Maximum resource usage (e.g., last element found or not found).
- **Average Case** (Θ): Expected resource usage across typical inputs.

---

## 7. Key Takeaways
1. Focus on **temporal complexity** unless spatial constraints are critical.
2. Use **Big-O notation** for worst-case analysis.
3. Optimize **nested loops** and avoid **exponential algorithms** when possible.
4. Choose algorithms based on context (e.g., input size, hardware constraints).

---

## 8. Reference Examples Table
| Complexity      | Example                              | Big-O   |
|-----------------|--------------------------------------|---------|
| Constant (O(1)) | Access array element                | O(1)    |
| Linear (O(n))   | Linear search                       | O(n)    |
| Logarithmic     | Binary search                       | O(log n)|
| Quadratic (O(n²)) | Pair comparisons in nested loops  | O(n²)   |
| Exponential     | Recursive subset generation         | O(2ⁿ) |

