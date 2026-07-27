# Chapter 24: Map Interface

## 📖 Overview

The **Map** interface is part of the Java Collections Framework (JCF) and is used to store data as **key-value pairs**. Each key is unique and maps to exactly one value.

Unlike `List` and `Set`, the `Map` interface **does not extend the Collection interface**.

Common implementations include **HashMap**, **LinkedHashMap**, **TreeMap**, and **Hashtable**.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the Map interface
- Store and retrieve key-value pairs
- Perform CRUD operations on a Map
- Iterate through a Map
- Compare different Map implementations
- Choose the appropriate Map implementation

---

# What is a Map?

A Map stores data as **Key → Value** pairs.

Example:

```
101 → Rahul
102 → Neha
103 → Amit
```

- Keys must be unique.
- Values can be duplicated.
- Each key maps to only one value.

---

# Map Hierarchy

```
          Map
           │
 ┌─────────┼────────────┐
 │         │            │
HashMap LinkedHashMap TreeMap
           │
      Hashtable
```

> `Map` is **not** a subtype of `Collection`.

---

# Creating a Map

```java
import java.util.HashMap;
import java.util.Map;

Map<Integer, String> students = new HashMap<>();
```

---

# Adding Elements

Use `put()` to insert key-value pairs.

```java
students.put(101, "Rahul");
students.put(102, "Neha");
students.put(103, "Amit");

System.out.println(students);
```

### Output

```
{101=Rahul, 102=Neha, 103=Amit}
```

---

# Duplicate Keys

If the same key is inserted again, the old value is replaced.

```java
students.put(101, "Rohit");

System.out.println(students);
```

### Output

```
{101=Rohit, 102=Neha, 103=Amit}
```

---

# Retrieving Values

Use `get()`.

```java
System.out.println(students.get(102));
```

### Output

```
Neha
```

---

# Updating Values

Simply use `put()` with an existing key.

```java
students.put(103, "Ankit");
```

---

# Removing Elements

```java
students.remove(102);

System.out.println(students);
```

---

# Checking Keys and Values

### containsKey()

```java
System.out.println(students.containsKey(101));
```

Output

```
true
```

---

### containsValue()

```java
System.out.println(students.containsValue("Rahul"));
```

Output

```
true
```

---

# Size and Empty Check

```java
System.out.println(students.size());

System.out.println(students.isEmpty());
```

---

# Iterating Through a Map

## Using entrySet()

```java
for (Map.Entry<Integer, String> entry : students.entrySet()) {

    System.out.println(entry.getKey() + " : " + entry.getValue());
}
```

### Output

```
101 : Rahul
102 : Neha
103 : Amit
```

---

## Using keySet()

```java
for (Integer key : students.keySet()) {

    System.out.println(key);
}
```

---

## Using values()

```java
for (String value : students.values()) {

    System.out.println(value);
}
```

---

# HashMap

Characteristics:

- Fastest implementation
- No ordering
- One null key allowed
- Multiple null values allowed

Example:

```java
Map<Integer, String> map = new HashMap<>();
```

---

# LinkedHashMap

Characteristics:

- Maintains insertion order
- Slightly slower than HashMap

Example:

```java
Map<Integer, String> map = new LinkedHashMap<>();
```

Output order:

```
101
102
103
```

---

# TreeMap

Characteristics:

- Keys are automatically sorted
- Does not allow null keys
- Based on Red-Black Tree

Example:

```java
Map<Integer, String> map = new TreeMap<>();

map.put(103, "Amit");
map.put(101, "Rahul");
map.put(102, "Neha");

System.out.println(map);
```

### Output

```
{101=Rahul, 102=Neha, 103=Amit}
```

---

# Hashtable

Characteristics:

- Thread-safe
- Legacy class
- Does not allow null keys or values

```java
Map<Integer, String> map = new Hashtable<>();
```

---

# HashMap vs LinkedHashMap vs TreeMap vs Hashtable

| Feature | HashMap | LinkedHashMap | TreeMap | Hashtable |
|---------|---------|---------------|----------|-----------|
| Order | No | Insertion Order | Sorted by Key | No |
| Thread-safe | ❌ No | ❌ No | ❌ No | ✅ Yes |
| Null Key | ✅ One | ✅ One | ❌ No | ❌ No |
| Null Value | ✅ Yes | ✅ Yes | ✅ Yes | ❌ No |
| Performance | Fastest | Fast | Moderate | Slow |

---

# Useful Map Methods

| Method | Description |
|---------|-------------|
| `put()` | Add or update entry |
| `get()` | Retrieve value |
| `remove()` | Remove entry |
| `containsKey()` | Check key |
| `containsValue()` | Check value |
| `keySet()` | Get all keys |
| `values()` | Get all values |
| `entrySet()` | Get key-value pairs |
| `size()` | Number of entries |
| `clear()` | Remove all entries |

---

# Real-World Examples

| Scenario | Map Implementation |
|----------|--------------------|
| Student ID → Name | HashMap |
| Product Catalogue | LinkedHashMap |
| Leaderboard Rankings | TreeMap |
| Legacy Multi-threaded App | Hashtable |

---

# Common Mistakes

### Duplicate Keys

```java
map.put(1, "Java");
map.put(1, "Spring");
```

Only one value is stored.

---

### Assuming HashMap is Ordered

```java
HashMap<String, Integer> map = new HashMap<>();
```

Order is **not guaranteed**.

Use `LinkedHashMap` if insertion order matters.

---

### Accessing Missing Keys

```java
System.out.println(map.get(999));
```

Returns:

```
null
```

Always check for `null` when necessary.

---

# Best Practices

- Program using the `Map` interface.
- Use `HashMap` for fast lookups.
- Use `LinkedHashMap` when insertion order matters.
- Use `TreeMap` for sorted keys.
- Use `entrySet()` for efficient iteration.
- Use generics for type safety.

---

# Summary

In this chapter, you learned:

- Map interface
- Key-value pairs
- CRUD operations
- HashMap
- LinkedHashMap
- TreeMap
- Hashtable
- Best practices

---

# Quick Revision

- Map stores key-value pairs.
- Keys are unique.
- Values may be duplicated.
- HashMap is the fastest implementation.
- LinkedHashMap maintains insertion order.
- TreeMap sorts keys.
- Hashtable is thread-safe.

---

# Practice Questions

### Basic

1. What is the Map interface?
2. Can a Map contain duplicate keys?
3. Which method retrieves a value using a key?
4. Which implementation maintains insertion order?
5. Which implementation sorts keys automatically?

### Intermediate

6. Compare HashMap and TreeMap.
7. Explain the difference between `keySet()` and `entrySet()`.
8. Why doesn't Map extend the Collection interface?

### Interview Questions

1. What is the difference between HashMap and Hashtable?
2. When should you use LinkedHashMap?
3. Why are keys unique in a Map?
4. What happens if the same key is inserted twice?
5. Which Map implementation would you use for a leaderboard and why?

---

# Hands-on Exercise

Create an **Employee Directory** that:

1. Create a `HashMap<Integer, String>`.
2. Add five employee records.
3. Update one employee's name.
4. Search for an employee using their ID.
5. Remove an employee.
6. Display:
   - All keys
   - All values
   - All key-value pairs using `entrySet()`
7. Print the total number of employees.
