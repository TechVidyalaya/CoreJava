# Chapter 22: Set Interface

## 📖 Overview

The **Set** interface is part of the Java Collections Framework (JCF) and represents a collection of **unique elements**. Unlike a `List`, a `Set` does **not allow duplicate values**.

Common implementations are **HashSet**, **LinkedHashSet**, and **TreeSet**, each providing different ordering and performance characteristics.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the Set interface
- Store unique elements
- Use HashSet, LinkedHashSet, and TreeSet
- Perform common Set operations
- Choose the right Set implementation

---

# What is a Set?

A `Set` is a collection that:

- Stores unique elements
- Does not allow duplicates
- Does not support index-based access
- Can store one `null` value (except `TreeSet`)

Example:

```java
Set<String> technologies = new HashSet<>();

technologies.add("Java");
technologies.add("Spring");
technologies.add("Java");

System.out.println(technologies);
```

### Output

```
[Java, Spring]
```

---

# Set Hierarchy

```
Collection
     │
    Set
 ┌────┼─────────────┐
 │    │             │
HashSet LinkedHashSet TreeSet
```

---

# Creating a Set

```java
import java.util.HashSet;
import java.util.Set;

Set<String> skills = new HashSet<>();
```

---

# Adding Elements

```java
skills.add("Java");
skills.add("Spring Boot");
skills.add("SQL");

System.out.println(skills);
```

### Output

```
[Java, Spring Boot, SQL]
```

> The order may vary because `HashSet` does not maintain insertion order.

---

# Duplicate Elements

```java
skills.add("Java");
skills.add("Java");

System.out.println(skills);
```

### Output

```
[Java, Spring Boot, SQL]
```

Duplicate values are ignored.

---

# Checking an Element

```java
System.out.println(skills.contains("Java"));
```

### Output

```
true
```

---

# Removing an Element

```java
skills.remove("SQL");

System.out.println(skills);
```

---

# Set Size

```java
System.out.println(skills.size());
```

### Output

```
2
```

---

# Checking Empty Set

```java
System.out.println(skills.isEmpty());
```

### Output

```
false
```

---

# Clearing a Set

```java
skills.clear();

System.out.println(skills);
```

### Output

```
[]
```

---

# Iterating Through a Set

Using enhanced for loop:

```java
Set<String> languages = new HashSet<>();

languages.add("Java");
languages.add("Python");
languages.add("SQL");

for (String language : languages) {

    System.out.println(language);
}
```

---

Using `Iterator`:

```java
Iterator<String> iterator = languages.iterator();

while (iterator.hasNext()) {

    System.out.println(iterator.next());
}
```

---

Using `forEach()`:

```java
languages.forEach(System.out::println);
```

---

# HashSet

Characteristics:

- No duplicates
- No insertion order
- Fastest performance
- Backed by `HashMap`

Example:

```java
Set<Integer> numbers = new HashSet<>();

numbers.add(20);
numbers.add(10);
numbers.add(30);

System.out.println(numbers);
```

Possible Output

```
[20, 10, 30]
```

---

# LinkedHashSet

Characteristics:

- No duplicates
- Maintains insertion order
- Slightly slower than `HashSet`

Example:

```java
Set<String> cities = new LinkedHashSet<>();

cities.add("Delhi");
cities.add("Mumbai");
cities.add("Chennai");

System.out.println(cities);
```

### Output

```
[Delhi, Mumbai, Chennai]
```

---

# TreeSet

Characteristics:

- No duplicates
- Automatically sorts elements
- Slower than `HashSet`
- Does not allow `null`

Example:

```java
Set<Integer> marks = new TreeSet<>();

marks.add(80);
marks.add(60);
marks.add(90);

System.out.println(marks);
```

### Output

```
[60, 80, 90]
```

---

# HashSet vs LinkedHashSet vs TreeSet

| Feature | HashSet | LinkedHashSet | TreeSet |
|---------|---------|---------------|----------|
| Duplicates | ❌ No | ❌ No | ❌ No |
| Order | Unordered | Insertion Order | Sorted |
| Performance | Fastest | Fast | Moderate |
| Null Allowed | ✅ Yes | ✅ Yes | ❌ No |
| Backed By | HashMap | HashMap + Linked List | TreeMap |

---

# Set Operations

### Union

```java
Set<Integer> set1 = new HashSet<>(Set.of(1, 2, 3));
Set<Integer> set2 = new HashSet<>(Set.of(3, 4, 5));

set1.addAll(set2);

System.out.println(set1);
```

### Output

```
[1, 2, 3, 4, 5]
```

---

### Intersection

```java
set1.retainAll(set2);

System.out.println(set1);
```

### Output

```
[3, 4, 5]
```

---

### Difference

```java
set1.removeAll(set2);

System.out.println(set1);
```

---

# Real-World Examples

| Scenario | Recommended Set |
|----------|-----------------|
| Unique Email IDs | HashSet |
| Browser Bookmarks | LinkedHashSet |
| Leaderboard Scores | TreeSet |
| Unique Usernames | HashSet |

---

# Common Mistakes

### Expecting Ordered Output from HashSet

```java
HashSet<String> set = new HashSet<>();
```

❌ Order is not guaranteed.

Use `LinkedHashSet` if insertion order matters.

---

### Accessing by Index

Incorrect:

```java
set.get(0);
```

`Set` does not support indexing.

---

### Adding Null to TreeSet

```java
TreeSet<String> set = new TreeSet<>();

set.add(null);
```

❌ Throws:

```
NullPointerException
```

---

# Best Practices

- Use `HashSet` for maximum performance.
- Use `LinkedHashSet` when insertion order is important.
- Use `TreeSet` when sorted data is required.
- Program using the `Set` interface.
- Use generics for type safety.

---

# Summary

In this chapter, you learned:

- Set interface
- HashSet
- LinkedHashSet
- TreeSet
- Set operations
- Common methods
- Best practices

---

# Quick Revision

- Set stores unique elements.
- Duplicate values are ignored.
- HashSet is unordered and fastest.
- LinkedHashSet maintains insertion order.
- TreeSet keeps elements sorted.
- Set does not support index-based access.

---

# Practice Questions

### Basic

1. What is the Set interface?
2. Does Set allow duplicate elements?
3. Which Set implementation maintains insertion order?
4. Which Set implementation stores sorted data?
5. Can TreeSet store `null`?

### Intermediate

6. Compare HashSet, LinkedHashSet, and TreeSet.
7. Explain how duplicate elements are handled in a Set.
8. Describe the union and intersection operations.

### Interview Questions

1. What is the difference between List and Set?
2. Why is HashSet generally faster than TreeSet?
3. Why doesn't Set support index-based access?
4. When would you choose LinkedHashSet over HashSet?
5. What data structure is used internally by HashSet?

---

# Hands-on Exercise

Create a **Student Registration System** that:

1. Store student IDs using a `HashSet`.
2. Add duplicate IDs and verify they are ignored.
3. Display all registered IDs.
4. Search for a specific student ID.
5. Remove a student ID.
6. Create another Set and perform:
   - Union
   - Intersection
   - Difference
7. Display the results of each operation.
