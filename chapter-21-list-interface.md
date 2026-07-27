# Chapter 21: List Interface

## 📖 Overview

The **List** interface is part of the Java Collections Framework and represents an **ordered collection** of elements. It allows duplicate values, maintains insertion order, and provides index-based access to elements.

Common implementations of the `List` interface are **ArrayList**, **LinkedList**, and **Vector**.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the List interface
- Use common List implementations
- Perform CRUD operations on a List
- Iterate through a List
- Compare ArrayList, LinkedList, and Vector

---

# What is a List?

A `List` is an ordered collection that:

- Maintains insertion order
- Allows duplicate elements
- Supports index-based access
- Allows null values

Example:

```java
List<String> fruits = new ArrayList<>();

fruits.add("Apple");
fruits.add("Banana");
fruits.add("Apple");

System.out.println(fruits);
```

### Output

```
[Apple, Banana, Apple]
```

---

# List Hierarchy

```
Collection
     │
    List
 ┌────┼─────────┐
 │    │         │
ArrayList  LinkedList  Vector
```

---

# Creating a List

```java
import java.util.ArrayList;
import java.util.List;

List<String> courses = new ArrayList<>();
```

Programming to the `List` interface makes your code more flexible.

---

# Adding Elements

```java
courses.add("Java");
courses.add("Spring Boot");
courses.add("SQL");

System.out.println(courses);
```

### Output

```
[Java, Spring Boot, SQL]
```

---

# Adding at a Specific Index

```java
courses.add(1, "HTML");

System.out.println(courses);
```

### Output

```
[Java, HTML, Spring Boot, SQL]
```

---

# Accessing Elements

```java
System.out.println(courses.get(2));
```

### Output

```
Spring Boot
```

---

# Updating Elements

```java
courses.set(0, "Core Java");

System.out.println(courses);
```

### Output

```
[Core Java, HTML, Spring Boot, SQL]
```

---

# Removing Elements

### By Index

```java
courses.remove(1);
```

### By Value

```java
courses.remove("SQL");
```

---

# Searching Elements

### contains()

```java
System.out.println(courses.contains("Java"));
```

### Output

```
false
```

---

### indexOf()

```java
System.out.println(courses.indexOf("Spring Boot"));
```

### Output

```
1
```

---

# List Size

```java
System.out.println(courses.size());
```

### Output

```
2
```

---

# Checking Empty List

```java
System.out.println(courses.isEmpty());
```

### Output

```
false
```

---

# Clearing a List

```java
courses.clear();
```

After clearing:

```java
System.out.println(courses);
```

### Output

```
[]
```

---

# Iterating Using Enhanced For Loop

```java
List<String> languages = List.of("Java", "Python", "SQL");

for (String language : languages) {

    System.out.println(language);
}
```

### Output

```
Java
Python
SQL
```

---

# Iterating Using Iterator

```java
Iterator<String> iterator = languages.iterator();

while (iterator.hasNext()) {

    System.out.println(iterator.next());
}
```

---

# Iterating Using forEach()

```java
languages.forEach(System.out::println);
```

---

# ArrayList

Characteristics:

- Fast random access
- Dynamic array
- Best for read operations

Example:

```java
List<Integer> numbers = new ArrayList<>();

numbers.add(10);
numbers.add(20);
numbers.add(30);
```

---

# LinkedList

Characteristics:

- Doubly linked list
- Fast insertion and deletion
- Slower random access

Example:

```java
List<String> cities = new LinkedList<>();

cities.add("Delhi");
cities.add("Mumbai");
```

---

# Vector

Characteristics:

- Thread-safe
- Slower than ArrayList
- Legacy class

```java
Vector<String> names = new Vector<>();

names.add("Rahul");
names.add("Neha");
```

---

# ArrayList vs LinkedList vs Vector

| Feature | ArrayList | LinkedList | Vector |
|---------|-----------|------------|--------|
| Data Structure | Dynamic Array | Doubly Linked List | Dynamic Array |
| Random Access | Fast | Slow | Fast |
| Insert/Delete | Moderate | Fast | Moderate |
| Thread-safe | ❌ No | ❌ No | ✅ Yes |
| Performance | Fast | Good for updates | Slower |

---

# Real-World Examples

| Scenario | Recommended List |
|----------|------------------|
| Student List | ArrayList |
| Browser History | LinkedList |
| Legacy Thread-safe App | Vector |

---

# Common Mistakes

### Accessing Invalid Index

```java
courses.get(10);
```

❌ Throws:

```
IndexOutOfBoundsException
```

---

### Modifying While Iterating

Incorrect:

```java
for (String course : courses) {

    courses.remove(course);
}
```

May throw:

```
ConcurrentModificationException
```

Use an `Iterator` when removing elements during iteration.

---

### Forgetting Generics

Incorrect:

```java
ArrayList list = new ArrayList();
```

Correct:

```java
ArrayList<String> list = new ArrayList<>();
```

---

# Best Practices

- Program using the `List` interface.
- Use `ArrayList` for frequent reads.
- Use `LinkedList` for frequent insertions/deletions.
- Use generics for type safety.
- Prefer enhanced for loops or `forEach()` for iteration.

---

# Summary

In this chapter, you learned:

- List interface
- CRUD operations
- Iteration techniques
- ArrayList
- LinkedList
- Vector
- Best practices

---

# Quick Revision

- List maintains insertion order.
- Duplicates are allowed.
- Elements are accessed using indexes.
- `ArrayList` is best for reading.
- `LinkedList` is best for insert/delete operations.
- `Vector` is thread-safe.

---

# Practice Questions

### Basic

1. What is the List interface?
2. Does a List allow duplicate elements?
3. Which method retrieves an element by index?
4. What is the purpose of `set()`?
5. Which implementation is thread-safe?

### Intermediate

6. Compare ArrayList and LinkedList.
7. Explain different ways to iterate over a List.
8. Why should we program using the `List` interface?

### Interview Questions

1. What is the difference between ArrayList and LinkedList?
2. When would you choose Vector?
3. Why is ArrayList faster for random access?
4. What happens if an invalid index is accessed?
5. How can elements be safely removed while iterating?

---

# Hands-on Exercise

Create a **Course Management System** that:

1. Create a `List<String>` using `ArrayList`.
2. Add at least 5 course names.
3. Insert a course at a specific position.
4. Update one course name.
5. Remove a course by name.
6. Search for a course using `contains()`.
7. Display all courses using:
   - Enhanced for loop
   - Iterator
   - `forEach()`
8. Print the total number of courses.
