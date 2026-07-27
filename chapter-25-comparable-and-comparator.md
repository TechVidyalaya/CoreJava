# Chapter 25: Comparable and Comparator

## 📖 Overview

Sorting is a common operation in Java applications. While Java can automatically sort primitive data types and Strings, custom objects require additional logic.

Java provides two interfaces for custom sorting:

- **Comparable** – Defines the natural ordering of objects.
- **Comparator** – Defines custom sorting logic.

Both interfaces are widely used with collections like `ArrayList`, `TreeSet`, and `TreeMap`.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Comparable and Comparator
- Implement natural ordering
- Create custom sorting logic
- Sort collections of objects
- Differentiate Comparable and Comparator

---

# Why Do We Need Comparable?

Java can sort numbers easily.

```java
List<Integer> numbers = Arrays.asList(40, 10, 30, 20);

Collections.sort(numbers);

System.out.println(numbers);
```

### Output

```
[10, 20, 30, 40]
```

But for custom objects:

```java
class Student {

    int id;
    String name;
}
```

Java doesn't know how to compare two `Student` objects.

---

# Comparable Interface

The `Comparable` interface defines the **natural ordering** of objects.

Package:

```java
java.lang
```

Method:

```java
int compareTo(T obj)
```

---

# Implementing Comparable

```java
class Student implements Comparable<Student> {

    int id;
    String name;

    Student(int id, String name) {

        this.id = id;
        this.name = name;
    }

    @Override
    public int compareTo(Student other) {

        return this.id - other.id;
    }

    @Override
    public String toString() {

        return id + " - " + name;
    }
}
```

---

# Sorting Using Comparable

```java
List<Student> students = new ArrayList<>();

students.add(new Student(103, "Rahul"));
students.add(new Student(101, "Neha"));
students.add(new Student(102, "Amit"));

Collections.sort(students);

System.out.println(students);
```

### Output

```
[101 - Neha, 102 - Amit, 103 - Rahul]
```

---

# Understanding `compareTo()`

| Return Value | Meaning |
|-------------|---------|
| Negative | Current object comes first |
| Zero | Objects are equal |
| Positive | Current object comes after |

Example:

```java
10.compareTo(20); // Negative

20.compareTo(20); // Zero

30.compareTo(20); // Positive
```

---

# Comparator Interface

`Comparator` defines **custom sorting rules**.

Package:

```java
java.util
```

Method:

```java
int compare(T o1, T o2)
```

---

# Sorting by Name Using Comparator

```java
class NameComparator implements Comparator<Student> {

    @Override
    public int compare(Student s1, Student s2) {

        return s1.name.compareTo(s2.name);
    }
}
```

Usage:

```java
Collections.sort(students, new NameComparator());
```

### Output

```
[Amit, Neha, Rahul]
```

---

# Comparator Using Lambda (Java 8+)

```java
Collections.sort(students,
    (s1, s2) -> s1.name.compareTo(s2.name));
```

Or

```java
students.sort(
    Comparator.comparing(Student::getName)
);
```

---

# Reverse Order

```java
Collections.sort(
    students,
    Comparator.comparing(Student::getName).reversed()
);
```

---

# Sorting by Multiple Fields

First by age, then by name.

```java
students.sort(

    Comparator
        .comparing(Student::getAge)
        .thenComparing(Student::getName)
);
```

---

# Comparable vs Comparator

| Comparable | Comparator |
|------------|------------|
| `java.lang` | `java.util` |
| Natural ordering | Custom ordering |
| `compareTo()` | `compare()` |
| One sorting rule | Multiple sorting rules |
| Class must implement interface | Separate comparator class/object |

---

# Collections.sort() vs List.sort()

Using Collections:

```java
Collections.sort(students);
```

Using List:

```java
students.sort(Comparator.comparing(Student::getName));
```

Both perform sorting, but `List.sort()` is available from Java 8 onwards.

---

# Real-World Examples

| Scenario | Interface |
|----------|-----------|
| Employee ID | Comparable |
| Employee Name | Comparator |
| Product Price | Comparable |
| Product Rating | Comparator |
| Student Marks | Comparator |

---

# Common Mistakes

### Returning Only `1` or `-1`

Incorrect:

```java
return 1;
```

Correct:

```java
return Integer.compare(this.id, other.id);
```

---

### Using Subtraction for Large Numbers

Incorrect:

```java
return this.salary - other.salary;
```

Better:

```java
return Integer.compare(this.salary, other.salary);
```

This avoids integer overflow.

---

### Forgetting equals()

If `compareTo()` returns `0`, the objects are considered equal for sorting purposes. Ensure the comparison logic is consistent with `equals()` where appropriate.

---

# Best Practices

- Use `Comparable` for natural ordering.
- Use `Comparator` for multiple sorting criteria.
- Prefer `Comparator.comparing()` in Java 8+.
- Use `Integer.compare()` instead of subtraction.
- Keep comparison logic simple and consistent.

---

# Summary

In this chapter, you learned:

- Comparable interface
- Comparator interface
- Natural ordering
- Custom sorting
- Lambda-based sorting
- Multiple field sorting
- Best practices

---

# Quick Revision

- `Comparable` defines natural ordering.
- `Comparator` defines custom ordering.
- `compareTo()` belongs to Comparable.
- `compare()` belongs to Comparator.
- Use `Comparator.comparing()` for clean code.
- Multiple comparators can be chained using `thenComparing()`.

---

# Practice Questions

### Basic

1. What is the purpose of Comparable?
2. What is the purpose of Comparator?
3. Which package contains Comparable?
4. Which method is defined in Comparable?
5. Which interface allows multiple sorting strategies?

### Intermediate

6. Differentiate Comparable and Comparator.
7. Explain the return values of `compareTo()`.
8. How do you sort objects by multiple fields?

### Interview Questions

1. When should you use Comparable instead of Comparator?
2. Why is `Integer.compare()` preferred over subtraction?
3. What is natural ordering?
4. Explain `Comparator.comparing()` with an example.
5. Can a class have multiple Comparators? Why?

---

# Hands-on Exercise

Create a **Student** class with:

- id
- name
- marks

Requirements:

1. Implement `Comparable<Student>` to sort students by **ID**.
2. Create a `Comparator` to sort students by **Name**.
3. Create another `Comparator` to sort students by **Marks (descending)**.
4. Display the student list after each type of sorting.
5. Use both `Collections.sort()` and `List.sort()` in your program.
