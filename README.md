# 🔎 Binary Search in C

Binary Search is one of the most fundamental and powerful algorithms in computer science.  
It allows us to find an element in a **sorted array** in **O(log n)** time.  

---

## 📖 How It Works

1. Start with a **sorted array**.  
2. Find the **middle element**.  
3. If the middle element equals the target → 🎯 Success!  
4. If the target is smaller → search the **left half**.  
5. If the target is larger → search the **right half**.  
6. Repeat until the element is found or the interval becomes empty.  

---

## 🖼️ Example Walkthrough

Searching for `42` in:

[10, 15, 20, 25, 30, 35, 40, 42, 50]

pgsql
Копировать код

- Step 1 → middle = 25 → 42 > 25 → search right half  
- Step 2 → middle = 40 → 42 > 40 → search right half  
- Step 3 → middle = 42 → 🎯 FOUND  

---

## ⚡ Complexity

| Case          | Time Complexity |
|---------------|-----------------|
| Best Case     | O(1)            |
| Average Case  | O(log n)        |
| Worst Case    | O(log n)        |

- **Space Complexity**  
  - Iterative → O(1)  
  - Recursive → O(log n) (stack frames)  

---

## 📜 Iterative Implementation (C)

```c
#include <stdio.h>

int binarySearch(int arr[], int n, int target) {
    int left = 0, right = n - 1;

    while (left <= right) {
        int mid = left + (right - left) / 2; // avoid overflow
        if (arr[mid] == target) return mid;
        if (arr[mid] < target) left = mid + 1;
        else right = mid - 1;
    }
    return -1; // not found
}

int main() {
    int arr[] = {10, 15, 20, 25, 30, 35, 40, 42, 50};
    int n = sizeof(arr) / sizeof(arr[0]);
    int target = 42;

    int result = binarySearch(arr, n, target);

    if (result != -1)
        printf("Element found at index %d\n", result);
    else
        printf("Element not found\n");

    return 0;
}
📜 Recursive Implementation (C)
c
Копировать код
#include <stdio.h>

int binarySearchRecursive(int arr[], int left, int right, int target) {
    if (left <= right) {
        int mid = left + (right - left) / 2;

        if (arr[mid] == target) return mid;
        if (arr[mid] > target) return binarySearchRecursive(arr, left, mid - 1, target);

        return binarySearchRecursive(arr, mid + 1, right, target);
    }
    return -1;
}

int main() {
    int arr[] = {10, 15, 20, 25, 30, 35, 40, 42, 50};
    int n = sizeof(arr) / sizeof(arr[0]);
    int target = 42;

    int result = binarySearchRecursive(arr, 0, n - 1, target);

    if (result != -1)
        printf("Element found at index %d\n", result);
    else
        printf("Element not found\n");

    return 0;
}
✅ When to Use
Array must be sorted.

Efficient for large datasets.

Works for numbers, strings, and more.

❌ When Not to Use
On unsorted arrays (use linear search).

On linked lists (no random access).

🚀 Variations
First Occurrence Search → Find the first position of target.

Last Occurrence Search → Find the last position of target.

Lower Bound / Upper Bound → Find position where a number could be inserted.

Binary Search on Answers → Used in competitive programming (searching on ranges instead of arrays).

📚 Resources
GeeksforGeeks: Binary Search

Wikipedia

Visualgo Binary Search Visualizer

✨ Conclusion
Binary Search is a simple yet incredibly efficient algorithm.
It’s the foundation of many advanced algorithms and is essential for every programmer.
