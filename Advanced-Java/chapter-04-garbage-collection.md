# Chapter 04: Garbage Collection

## 📖 Overview

**Garbage Collection (GC)** is the automatic memory management mechanism of the JVM. It identifies objects that are no longer in use and reclaims their memory, allowing developers to focus on application logic instead of manual memory management.

Understanding Garbage Collection is essential for building high-performance Java applications and is a common interview topic.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Garbage Collection
- Learn how objects become eligible for GC
- Understand the GC lifecycle
- Learn common Garbage Collectors
- Understand memory leaks
- Follow GC best practices

---

# What is Garbage Collection?

Garbage Collection is the process of automatically removing objects that are no longer reachable.

Example:

```java
Employee emp =
    new Employee();

emp = null;
```

The object becomes eligible for Garbage Collection.

---

# Why Garbage Collection?

Without Garbage Collection:

- Memory would keep increasing
- Applications could crash
- Developers would need manual memory management

With Garbage Collection:

- Automatic memory cleanup
- Better memory utilisation
- Reduced programming errors

---

# Object Lifecycle

```text
Object Created
       │
       ▼
Object Used
       │
       ▼
No References
       │
       ▼
Eligible for GC
       │
       ▼
Memory Reclaimed
```

---

# Eligible for Garbage Collection

An object becomes eligible for GC when no live references point to it.

Example:

```java
Employee emp =
    new Employee();

emp = null;
```

---

# Reassigning References

```java
Employee emp1 =
    new Employee();

Employee emp2 =
    new Employee();

emp1 = emp2;
```

The first object referenced by `emp1` becomes eligible for GC.

---

# Anonymous Objects

Objects without references are immediately eligible for GC.

```java
new Employee();
```

Since no reference is stored, the object can be collected.

---

# Island of Isolation

Objects referencing each other but not reachable from the application are eligible for GC.

```text
Object A ─────► Object B
     ▲             │
     └─────────────┘

No External References
```

Both objects can be garbage collected.

---

# Requesting Garbage Collection

You can request Garbage Collection using:

```java
System.gc();
```

or

```java
Runtime.getRuntime().gc();
```

> **Note:** These methods only request GC. The JVM decides whether and when to perform it.

---

# finalize() Method

Earlier versions of Java used:

```java
@Override
protected void finalize() {

    System.out.println("Cleaning...");
}
```

> **Note:** `finalize()` is **deprecated** and should not be used in modern Java.

Prefer:

- Try-with-resources
- AutoCloseable
- Proper resource management

---

# Garbage Collection Process

```text
Objects Created
       │
       ▼
Reachability Analysis
       │
       ▼
Unreachable Objects
       │
       ▼
Garbage Collector
       │
       ▼
Memory Reclaimed
```

---

# Types of Garbage Collectors

| Garbage Collector | Description |
|-------------------|-------------|
| Serial GC | Single-threaded collector |
| Parallel GC | Multiple threads for better throughput |
| G1 GC | Default collector in modern Java versions |
| ZGC | Low-latency collector for large heaps |
| Shenandoah GC | Low-pause-time collector |

> Java 8 commonly uses **Parallel GC** by default.

---

# Young and Old Generation

```text
Heap
│
├── Young Generation
│      │
│      ▼
│   Minor GC
│
└── Old Generation
       │
       ▼
    Major/Full GC
```

---

# Minor GC

Occurs in the **Young Generation**.

Characteristics:

- Fast
- Frequent
- Cleans short-lived objects

---

# Major (Full) GC

Occurs in the **Old Generation**.

Characteristics:

- Slower
- Less frequent
- Can temporarily pause the application

---

# Memory Leak

A memory leak occurs when objects are no longer needed but are still referenced.

Example:

```java
List<Employee> employees =
    new ArrayList<>();

while (true) {

    employees.add(
        new Employee()
    );
}
```

Objects remain referenced by the list and cannot be garbage collected.

---

# Common JVM GC Options

```text
-XX:+UseSerialGC

-XX:+UseParallelGC

-XX:+UseG1GC
```

These JVM options select the desired Garbage Collector.

---

# Real-World Applications

Garbage Collection plays an important role in:

- Spring Boot applications
- Enterprise servers
- Banking systems
- E-commerce platforms
- Big data processing
- Cloud-native applications

---

# Common Mistakes

### Assuming System.gc() Forces GC

```java
System.gc();
```

This only requests Garbage Collection.

---

### Holding Unnecessary References

Keeping unused objects in collections prevents Garbage Collection.

---

### Relying on finalize()

`finalize()` is deprecated and should not be used for resource cleanup.

---

# Best Practices

- Remove unnecessary object references.
- Close files, sockets, and database connections properly.
- Use try-with-resources for AutoCloseable objects.
- Avoid memory leaks caused by long-lived collections.
- Monitor GC behaviour using profiling tools.
- Choose an appropriate GC for your application's workload.

---

# Summary

In this chapter, you learned:

- Garbage Collection
- Object lifecycle
- GC eligibility
- Minor and Major GC
- Memory leaks
- Types of Garbage Collectors
- Best practices

---

# Quick Revision

- Garbage Collection automatically frees unused memory.
- Objects become eligible when no live references exist.
- `System.gc()` only requests Garbage Collection.
- Minor GC runs in the Young Generation.
- Major GC runs in the Old Generation.
- Avoid memory leaks by removing unnecessary references.
- Do not use the deprecated `finalize()` method.

---

# Practice Questions

### Basic

1. What is Garbage Collection?
2. When does an object become eligible for GC?
3. What does `System.gc()` do?
4. What is a memory leak?
5. What is Minor GC?

### Intermediate

6. Differentiate Minor GC and Major GC.
7. Explain the object lifecycle.
8. What is the Island of Isolation?

### Interview Questions

1. Explain Garbage Collection in Java.
2. How does the JVM identify garbage objects?
3. Why is `finalize()` deprecated?
4. Compare Serial GC, Parallel GC, and G1 GC.
5. How can memory leaks occur in Java despite automatic Garbage Collection?

---

# Hands-on Exercise

Create a **Garbage Collection Demo** application that:

1. Create multiple objects and make them eligible for GC.
2. Demonstrate object eligibility using:
   - Null references
   - Reassigned references
   - Anonymous objects
3. Invoke `System.gc()` and observe the behaviour.
4. Display JVM memory before and after object creation using:

```java
Runtime.getRuntime()
```

5. Create a simple memory leak using a collection.
6. Compare Minor GC and Major GC using JVM monitoring tools.
7. Run the application with different Garbage Collectors (Serial, Parallel, and G1).
8. Analyse GC activity using VisualVM or JDK Mission Control.
