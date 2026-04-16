
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

## 🧠 Quick Teaching Tip

Tell students:

* O(1) → “Instant”
* O(log n) → “Divide”
* O(n) → “Scan”
* O(n²) → “Compare all”
* O(2ⁿ), O(n!) → “Danger zone 🚨”

---

If you want, I can convert this into a **one-slide teaching chart** or **interview-ready cheatsheet**.
