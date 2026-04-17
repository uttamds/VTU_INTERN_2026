
# Big O Notation
---

## 🔹 O(1) — Constant Time

Constant time means the operation takes the same amount of time regardless of the input size. Whether the data has 10 elements or 10 million elements, the time required does not change. A common example is accessing an element in an array using its index. This is considered the most efficient type of complexity because it does not grow with input size.

---

## 🔹 O(log n) — Logarithmic

Logarithmic time means the problem size is reduced at each step, usually by half. Instead of checking every element, we eliminate large portions of the data repeatedly. A classic example is binary search, where we divide the search space into two halves each time. This makes it very efficient for large datasets.

---

## 🔹 O(n) — Linear Time

Linear time means the running time grows directly with the size of the input. If the input size doubles, the time taken also doubles. This typically happens when we loop through all elements once, such as calculating the sum of an array or searching for an element in an unsorted list.

---

## 🔹 O(n log n) — Linearithmic

This complexity is a combination of linear and logarithmic behavior. We divide the problem into smaller parts and then process all elements. Algorithms like merge sort and quicksort (on average) follow this pattern. It is considered very efficient for sorting because it scales well even for large inputs.

---

## 🔹 O(n²) — Quadratic

Quadratic time occurs when we have nested loops, where each element is compared with every other element. As the input size increases, the time grows much faster. If the input doubles, the time becomes roughly four times. Examples include simple sorting algorithms like bubble sort or checking all pairs in a list.

---

## 🔹 O(2ⁿ) — Exponential

Exponential time means the number of operations doubles with each additional input element. This leads to extremely rapid growth and becomes impractical even for moderately large inputs. A classic example is the naive recursive Fibonacci solution, where the same calculations are repeated multiple times.

---

## 🔹 O(n!) — Factorial

Factorial time represents the highest growth among common complexities. It occurs when we generate all possible permutations of a set. Even a small increase in input size causes a massive increase in computation. For example, with just 5 elements, there are already 120 permutations. This type of complexity is usually avoided unless absolutely necessary.

---



=================
Here are **simple Java snippets** for each Big-O from your table.

---

## 🔹 O(1) — Constant Time

```java
int[] arr = {10, 20, 30, 40};

System.out.println(arr[2]); // Direct access
```

👉 No matter the array size, it takes the same time.

---

## 🔹 O(log n) — Logarithmic (Binary Search)

```java
int binarySearch(int[] arr, int target) {
    int left = 0, right = arr.length - 1;

    while (left <= right) {
        int mid = (left + right) / 2;

        if (arr[mid] == target)
            return mid;
        else if (arr[mid] < target)
            left = mid + 1;
        else
            right = mid - 1;
    }
    return -1;
}
```

👉 Cuts the problem in half each step.

---

## 🔹 O(n) — Linear Time

```java
int sum = 0;
int[] arr = {1, 2, 3, 4, 5};

for (int i = 0; i < arr.length; i++) {
    sum += arr[i];
}
System.out.println(sum);
```

👉 One full pass through the data.

---

## 🔹 O(n log n) — Linearithmic (Merge Sort)

```java
void mergeSort(int[] arr, int left, int right) {
    if (left >= right) return;

    int mid = (left + right) / 2;

    mergeSort(arr, left, mid);
    mergeSort(arr, mid + 1, right);
    merge(arr, left, mid, right);
}
```

👉 Divide (log n) + process all elements (n).

---


=============== Full code  =============================
import java.util.Arrays;

public class MergeSortExample {

    public static void mergeSort(int[] arr, int left, int right) {
        if (left < right) {
            int mid = (left + right) / 2;

            // Divide
            mergeSort(arr, left, mid);
            mergeSort(arr, mid + 1, right);

            // Conquer (Merge)
            merge(arr, left, mid, right);
        }
    }

    public static void merge(int[] arr, int left, int mid, int right) {

        int n1 = mid - left + 1;
        int n2 = right - mid;

        int[] leftArr = new int[n1];
        int[] rightArr = new int[n2];

        // Copy data
        for (int i = 0; i < n1; i++)
            leftArr[i] = arr[left + i];

        for (int j = 0; j < n2; j++)
            rightArr[j] = arr[mid + 1 + j];

        int i = 0, j = 0, k = left;

        // Merge two sorted arrays
        while (i < n1 && j < n2) {
            if (leftArr[i] <= rightArr[j]) {
                arr[k] = leftArr[i];
                i++;
            } else {
                arr[k] = rightArr[j];
                j++;
            }
            k++;
        }

        // Copy remaining elements
        while (i < n1) {
            arr[k] = leftArr[i];
            i++;
            k++;
        }

        while (j < n2) {
            arr[k] = rightArr[j];
            j++;
            k++;
        }
    }

    public static void main(String[] args) {

        int[] arr = {38, 27, 43, 3, 9, 82, 10};

        System.out.println("Before Sorting:");
        System.out.println(Arrays.toString(arr));

        mergeSort(arr, 0, arr.length - 1);

        System.out.println("After Sorting:");
        System.out.println(Arrays.toString(arr));
    }
}

==============

## 🔹 O(n²) — Quadratic (Nested Loops)

```java
int[] arr = {1, 2, 3, 4};

for (int i = 0; i < arr.length; i++) {
    for (int j = 0; j < arr.length; j++) {
        System.out.println(arr[i] + ", " + arr[j]);
    }
}
```

👉 Every element paired with every other.

---

## 🔹 O(2ⁿ) — Exponential (Recursive Fibonacci)

```java
int fib(int n) {
    if (n <= 1) return n;
    return fib(n - 1) + fib(n - 2);
}
```

👉 Explodes fast—recomputes same values again and again.

---

## 🔹 O(n!) — Factorial (Permutations)

```java
void permute(String str, String ans) {
    if (str.length() == 0) {
        System.out.println(ans);
        return;
    }

    for (int i = 0; i < str.length(); i++) {
        char ch = str.charAt(i);
        String rest = str.substring(0, i) + str.substring(i + 1);
        permute(rest, ans + ch);
    }
}
```

👉 Generates all possible arrangements.

---

## 🧠 Summary



* O(1) → “Instant”
* O(log n) → “Divide”
* O(n) → “Scan”
* O(n²) → “Compare all”
* O(2ⁿ), O(n!) → “Danger zone 🚨”

---

# Topics 



## 🔹 Array Traversal Patterns

Array traversal means visiting each element of an array in a specific order to solve a problem. The most basic pattern is a simple left-to-right loop, but there are many variations such as reverse traversal, skipping elements, or traversing with conditions. Understanding traversal patterns helps us structure logic clearly and efficiently, especially when working with searching, counting, or transforming data inside arrays.

---

## 🔹 Two Pointer Technique

The two pointer technique involves using two indices to traverse an array simultaneously, usually from different directions or at different speeds. This approach is especially useful when the array is sorted, as it helps reduce time complexity compared to nested loops. Instead of checking all possible pairs, we move the pointers based on conditions, making the solution more efficient and often reducing complexity from O(n²) to O(n).

---

## 🔹 Prefix Sum Concept

The prefix sum concept is used to efficiently calculate the sum of elements in a range. Instead of recomputing sums again and again, we store cumulative sums in a new array. Each position in the prefix sum array represents the sum of all elements up to that index. This allows us to answer range sum queries in constant time, making it very useful in problems involving multiple queries on the same data.

---

## 🔹 Kadane’s Algorithm

Kadane’s Algorithm is used to find the maximum sum of a contiguous subarray in an array. Instead of checking all possible subarrays, it works by maintaining a running sum and resetting it whenever it becomes negative. At each step, we keep track of the maximum sum found so far. This makes the algorithm very efficient, running in linear time, and it is widely used in optimization problems involving subarrays.


