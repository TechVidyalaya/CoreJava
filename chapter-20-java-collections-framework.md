# Chapter 20: Java Collections Framework (JCF)

## 📖 Overview

The **Java Collections Framework (JCF)** is a unified architecture for storing and manipulating groups of objects. It provides ready-made data structures such as **List**, **Set**, **Queue**, and **Map**, along with algorithms for searching, sorting, and traversing data.

Using collections makes Java applications more efficient, flexible, and easier to maintain.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the Java Collections Framework
- Differentiate Collection and Collections
- Identify major collection interfaces
- Choose the appropriate collection
- Understand the Collection hierarchy

---

# What is the Java Collections Framework?

The Java Collections Framework (JCF) is a set of interfaces and classes used to store and manipulate groups of objects.

Examples:

- Student records
- Employee list
- Shopping cart
- Product catalogue
- Customer orders

---

# Why Use Collections?

Without collections:

```java
String student1 = "Rahul";
String student2 = "Amit";
String student3 = "Neha";
```

With collections:

```java
import java.util.ArrayList;

ArrayList<String> students = new ArrayList<>();

students.add("Rahul");
students.add("Amit");
students.add("Neha");
```

Collections are dynamic and easy to manage.

---

# Collection Hierarchy

```
                 Iterable
                     │
               Collection
          ┌──────────┼──────────┐
          │          │          │
        List        Set       Queue
          │          │          │
  ArrayList     HashSet     PriorityQueue
  LinkedList    LinkedHashSet
  Vector        TreeSet
```

`Map` is part of the Collections Framework but **does not extend the Collection interface**.

```
Map
│
├── HashMap
├── LinkedHashMap
├── TreeMap
└── Hashtable
```

---

# Collection vs Collections

| Collection | Collections |
|------------|-------------|
| Interface | Utility class |
| Stores objects | Provides static utility methods |
| Part of JCF hierarchy | Contains methods like `sort()`, `reverse()` |

Example:

```java
Collections.sort(list);
```

---

# Major Collection Interfaces

| Interface | Description |
|-----------|-------------|
| List | Ordered collection with duplicates |
| Set | Unique elements only |
| Queue | FIFO data structure |
| Map | Key-value pairs |

---

# List

Characteristics:

- Ordered
- Allows duplicates
- Index-based access

Implementations:

- ArrayList
- LinkedList
- Vector

Example:

```java
List<String> names = new ArrayList<>();

names.add("Java");
names.add("Spring");
names.add("Java");

System.out.println(names);
```

### Output

```
[Java, Spring, Java]
```

---

# Set

Characteristics:

- No duplicate elements
- No index
- Fast searching

Implementations:

- HashSet
- LinkedHashSet
- TreeSet

Example:

```java
Set<String> courses = new HashSet<>();

courses.add("Java");
courses.add("Spring");
courses.add("Java");

System.out.println(courses);
```

### Output

```
[Java, Spring]
```

---

# Queue

Characteristics:

- FIFO (First In, First Out)
- Used for scheduling and processing tasks

Implementation:

- PriorityQueue
- LinkedList

Example:

```java
Queue<String> queue = new LinkedList<>();

queue.offer("Task1");
queue.offer("Task2");

System.out.println(queue.poll());
```

### Output

```
Task1
```

---

# Map

Stores data as **key-value pairs**.

Example:

```java
Map<Integer, String> employees = new HashMap<>();

employees.put(101, "Rahul");
employees.put(102, "Neha");

System.out.println(employees);
```

### Output

```
{101=Rahul, 102=Neha}
```

---

# Common Collection Methods

| Method | Description |
|---------|-------------|
| `add()` | Add element |
| `remove()` | Remove element |
| `contains()` | Check existence |
| `size()` | Number of elements |
| `isEmpty()` | Check if empty |
| `clear()` | Remove all elements |

Example:

```java
List<Integer> numbers = new ArrayList<>();

numbers.add(10);
numbers.add(20);

System.out.println(numbers.size());
```

### Output

```
2
```

---

# Iterating Through Collections

Using enhanced for loop:

```java
List<String> names = List.of("Java", "Spring", "SQL");

for (String name : names) {

    System.out.println(name);
}
```

### Output

```
Java
Spring
SQL
```

---

# Iterator

An `Iterator` is used to traverse collections safely.

```java
Iterator<String> iterator = names.iterator();

while (iterator.hasNext()) {

    System.out.println(iterator.next());
}
```

---

# Choosing the Right Collection

| Requirement | Recommended Collection |
|-------------|------------------------|
| Ordered with duplicates | ArrayList |
| Frequent insert/delete | LinkedList |
| Unique values | HashSet |
| Sorted values | TreeSet |
| FIFO processing | Queue |
| Key-value mapping | HashMap |

---

# Real-World Examples

| Scenario | Collection |
|----------|------------|
| Shopping Cart | ArrayList |
| Student Roll Numbers | HashSet |
| Print Queue | Queue |
| Employee Database | HashMap |
| Leaderboard | TreeSet |

---

# Common Mistakes

### Using Array Instead of Collection

```java
String[] names = new String[5];
```

Arrays have fixed size.

Prefer:

```java
ArrayList<String> names = new ArrayList<>();
```

---

### Choosing the Wrong Collection

Need duplicates?

❌ `HashSet`

✅ `ArrayList`

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

- Program to interfaces (`List`, `Set`, `Map`) rather than implementation classes.
- Use generics for type safety.
- Choose collections based on your use case.
- Prefer `ArrayList` for frequent reads.
- Use `HashSet` when uniqueness is required.
- Use `HashMap` for key-value storage.

---

# Summary

In this chapter, you learned:

- Java Collections Framework
- Collection hierarchy
- List, Set, Queue, and Map
- Collection vs Collections
- Common collection methods
- Choosing the right collection

---

# Quick Revision

- JCF stores groups of objects.
- `Collection` is an interface.
- `Collections` is a utility class.
- `List` allows duplicates.
- `Set` stores unique elements.
- `Queue` follows FIFO.
- `Map` stores key-value pairs.

---

# Practice Questions

### Basic

1. What is the Java Collections Framework?
2. What is the difference between `Collection` and `Collections`?
3. Which interface allows duplicate elements?
4. Which interface stores unique values?
5. Is `Map` a subtype of `Collection`?

### Intermediate

6. Differentiate `List`, `Set`, `Queue`, and `Map`.
7. When would you use an `Iterator`?
8. How do you choose the right collection?

### Interview Questions

1. Explain the Collection hierarchy.
2. Why should we program to interfaces instead of implementation classes?
3. What is the difference between `ArrayList` and `HashSet`?
4. Why does `Map` not extend the `Collection` interface?
5. What are the advantages of the Java Collections Framework?

---

# Hands-on Exercise

Create a **Student Management System** that:

1. Store student names in an `ArrayList`.
2. Store unique course names in a `HashSet`.
3. Store registration numbers and student names in a `HashMap`.
4. Display all data using loops.
5. Print the total number of students and courses.
6. Search for a student by registration number.
