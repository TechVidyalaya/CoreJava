# Chapter 16: Arrays Utility Class

## 📖 Overview

The **Arrays** class is a utility class provided by Java in the `java.util` package. It contains static methods for performing common operations on arrays such as sorting, searching, comparing, filling, copying, and converting arrays to strings.

Using the `Arrays` class simplifies array manipulation and reduces the amount of code you need to write.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the Arrays utility class
- Sort arrays
- Search elements using binary search
- Compare arrays
- Fill array elements
- Copy arrays
- Convert arrays into strings

---

# What is the Arrays Class?

The `Arrays` class is part of the `java.util` package.

Import it using:

```java
import java.util.Arrays;
```

Since all methods are static, you don't need to create an object.

Example:

```java
Arrays.sort(numbers);
```

---

# Sorting an Array

The `sort()` method sorts an array in ascending order.

```java
import java.util.Arrays;

public class Main {

    public static void main(String[] args) {

        int[] numbers = {50, 20, 40, 10, 30};

        Arrays.sort(numbers);

        System.out.println(Arrays.toString(numbers));
    }
}
```

### Output

```
[10, 20, 30, 40, 50]
```

---

# Binary Search

The `binarySearch()` method searches for an element in a **sorted array**.

```java
import java.util.Arrays;

public class Main {

    public static void main(String[] args) {

        int[] numbers = {10, 20, 30, 40, 50};

        int index = Arrays.binarySearch(numbers, 30);

        System.out.println(index);
    }
}
```

### Output

```
2
```

> Always sort the array before using `binarySearch()`.

---

# Comparing Arrays

The `equals()` method checks whether two arrays have the same elements in the same order.

```java
import java.util.Arrays;

public class Main {

    public static void main(String[] args) {

        int[] a = {1, 2, 3};
        int[] b = {1, 2, 3};

        System.out.println(Arrays.equals(a, b));
    }
}
```

### Output

```
true
```

---

# Filling an Array

The `fill()` method assigns the same value to every element.

```java
import java.util.Arrays;

public class Main {

    public static void main(String[] args) {

        int[] numbers = new int[5];

        Arrays.fill(numbers, 100);

        System.out.println(Arrays.toString(numbers));
    }
}
```

### Output

```
[100, 100, 100, 100, 100]
```

---

# Copying an Array

The `copyOf()` method creates a new array.

```java
import java.util.Arrays;

public class Main {

    public static void main(String[] args) {

        int[] original = {10, 20, 30};

        int[] copy = Arrays.copyOf(original, original.length);

        System.out.println(Arrays.toString(copy));
    }
}
```

### Output

```
[10, 20, 30]
```

---

# Copying a Range

Use `copyOfRange()` to copy a portion of an array.

```java
import java.util.Arrays;

public class Main {

    public static void main(String[] args) {

        int[] numbers = {10, 20, 30, 40, 50};

        int[] result = Arrays.copyOfRange(numbers, 1, 4);

        System.out.println(Arrays.toString(result));
    }
}
```

### Output

```
[20, 30, 40]
```

---

# Converting Array to String

The `toString()` method converts an array into a readable string.

```java
int[] numbers = {10, 20, 30};

System.out.println(Arrays.toString(numbers));
```

### Output

```
[10, 20, 30]
```

Without `toString()`:

```java
System.out.println(numbers);
```

Output:

```
[I@6d06d69c
```

---

# Sorting Strings

```java
import java.util.Arrays;

public class Main {

    public static void main(String[] args) {

        String[] languages = {
            "Python",
            "Java",
            "C++"
        };

        Arrays.sort(languages);

        System.out.println(Arrays.toString(languages));
    }
}
```

### Output

```
[C++, Java, Python]
```

---

# Parallel Sorting

For large arrays, Java provides `parallelSort()`.

```java
int[] numbers = {9, 3, 7, 1, 5};

Arrays.parallelSort(numbers);

System.out.println(Arrays.toString(numbers));
```

### Output

```
[1, 3, 5, 7, 9]
```

---

# Deep Comparison

For multidimensional arrays, use `deepEquals()`.

```java
int[][] a = {
    {1, 2},
    {3, 4}
};

int[][] b = {
    {1, 2},
    {3, 4}
};

System.out.println(Arrays.deepEquals(a, b));
```

### Output

```
true
```

---

# Deep String Representation

Use `deepToString()` for multidimensional arrays.

```java
int[][] matrix = {
    {1, 2},
    {3, 4}
};

System.out.println(Arrays.deepToString(matrix));
```

### Output

```
[[1, 2], [3, 4]]
```

---

# Common Arrays Methods

| Method | Purpose |
|---------|---------|
| `sort()` | Sort array |
| `parallelSort()` | Parallel sorting |
| `binarySearch()` | Search element |
| `equals()` | Compare arrays |
| `deepEquals()` | Compare multidimensional arrays |
| `fill()` | Fill array |
| `copyOf()` | Copy array |
| `copyOfRange()` | Copy part of array |
| `toString()` | Convert array to string |
| `deepToString()` | Convert multidimensional array |

---

# Real-World Example

Sorting employee IDs.

```java
int[] employeeIds = {
    105,
    102,
    101,
    104,
    103
};

Arrays.sort(employeeIds);

System.out.println(Arrays.toString(employeeIds));
```

### Output

```
[101, 102, 103, 104, 105]
```

---

# Common Mistakes

### Using Binary Search on an Unsorted Array

```java
int[] numbers = {30, 10, 20};

Arrays.binarySearch(numbers, 20);
```

❌ Result is unpredictable.

Always sort first.

---

### Printing Arrays Directly

```java
System.out.println(numbers);
```

❌ Prints the object's memory representation.

Use:

```java
System.out.println(Arrays.toString(numbers));
```

---

### Comparing Arrays Using `==`

```java
int[] a = {1, 2};
int[] b = {1, 2};

System.out.println(a == b);
```

Output

```
false
```

Correct:

```java
System.out.println(Arrays.equals(a, b));
```

---

# Best Practices

- Always import `java.util.Arrays`.
- Use `Arrays.sort()` instead of writing custom sorting algorithms unless required.
- Sort arrays before using `binarySearch()`.
- Use `Arrays.equals()` for comparison.
- Use `Arrays.toString()` for debugging and printing arrays.

---

# Summary

In this chapter, you learned:

- Arrays utility class
- Sorting arrays
- Searching arrays
- Comparing arrays
- Filling arrays
- Copying arrays
- Converting arrays to strings
- Working with multidimensional arrays

---

# Quick Revision

- `Arrays` belongs to `java.util`.
- All methods are static.
- Use `sort()` for sorting.
- Use `binarySearch()` on sorted arrays.
- Use `equals()` for comparison.
- Use `toString()` for printing arrays.
- Use `deepToString()` for multidimensional arrays.

---

# Practice Questions

### Basic

1. What is the Arrays utility class?
2. Which package contains the Arrays class?
3. What does `Arrays.sort()` do?
4. What is the purpose of `Arrays.fill()`?
5. Why is `Arrays.toString()` used?

### Intermediate

6. Explain `binarySearch()` with an example.
7. Differentiate `copyOf()` and `copyOfRange()`.
8. Explain `deepEquals()` and `deepToString()`.

### Interview Questions

1. Why should an array be sorted before using `binarySearch()`?
2. What is the difference between `Arrays.equals()` and `==`?
3. When should you use `parallelSort()`?
4. What happens if `binarySearch()` is used on an unsorted array?
5. Why is the Arrays class considered a utility class?

---

# Hands-on Exercise

Create a program that:

1. Creates an integer array with 10 random numbers.
2. Display the original array.
3. Sort the array.
4. Search for a number using `binarySearch()`.
5. Create a copy of the array.
6. Compare the original and copied arrays.
7. Fill another array with the value `999`.
8. Display all arrays using `Arrays.toString()`.
