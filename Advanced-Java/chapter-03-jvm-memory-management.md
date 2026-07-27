# Chapter 03: JVM Memory Management

## 📖 Overview

The **Java Virtual Machine (JVM)** manages memory automatically. Every Java application runs inside the JVM, which allocates and deallocates memory for objects, methods, variables, and threads.

Understanding JVM memory is essential for writing efficient applications, debugging memory issues, and succeeding in Java interviews.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand JVM memory architecture
- Learn Heap and Stack memory
- Understand Method Area and Metaspace
- Learn Program Counter and Native Method Stack
- Identify memory-related errors
- Follow JVM memory best practices

---

# What is JVM Memory?

JVM memory is divided into different runtime areas, each serving a specific purpose.

These areas help the JVM execute Java programs efficiently.

---

# JVM Memory Architecture

```text
                JVM Memory
                     │
     ┌───────────────┼───────────────┐
     │               │               │
     ▼               ▼               ▼
  Heap          Method Area      Stack
     │                               │
     ▼                               ▼
 Object Storage              Method Calls
                     │
                     ▼
              Program Counter
                     │
                     ▼
            Native Method Stack
```

---

# Heap Memory

Heap memory stores:

- Objects
- Instance variables
- Arrays

Example:

```java
Employee emp =
    new Employee();
```

The object is created in the **Heap**.

Characteristics:

- Shared among threads
- Managed by Garbage Collector
- Largest memory area

---

# Heap Structure

The Heap is divided into generations.

```text
Heap
│
├── Young Generation
│     ├── Eden
│     ├── Survivor 0
│     └── Survivor 1
│
└── Old Generation
```

Objects usually move:

```
Eden

↓

Survivor

↓

Old Generation
```

---

# Stack Memory

Each thread has its own Stack.

The Stack stores:

- Local variables
- Method parameters
- Method calls

Example:

```java
public void display() {

    int age = 25;
}
```

The variable `age` is stored in the Stack.

---

# Stack Example

```java
public static void main(String[] args) {

    Employee emp =
        new Employee();

    emp.display();
}
```

Memory:

```text
Stack
│
├── main()
│      │
│      └── Reference → Employee
│
└── display()
       │
       └── Local Variables

Heap
│
└── Employee Object
```

---

# Method Area (Metaspace)

The Method Area stores:

- Class metadata
- Static variables
- Runtime constant pool
- Method bytecode

From **Java 8**, the Method Area is implemented as **Metaspace**.

---

# Metaspace

Before Java 8:

```
PermGen
```

After Java 8:

```
Metaspace
```

Benefits:

- Uses native memory
- Removes fixed-size PermGen limitations
- Better memory management

---

# Program Counter (PC Register)

Each thread has its own Program Counter.

It stores:

- Address of the current instruction
- Execution position

This helps the JVM resume execution after thread switching.

---

# Native Method Stack

Used for:

- Native methods
- JNI (Java Native Interface)
- Calling C/C++ libraries

Example:

```java
System.loadLibrary("nativeLib");
```

---

# Object Lifecycle

```
new Employee()

        │

        ▼

Heap Allocation

        │

        ▼

Object Used

        │

        ▼

No References

        │

        ▼

Garbage Collection
```

---

# Memory Errors

## StackOverflowError

Occurs due to excessive recursion.

```java
void test() {

    test();
}
```

Output

```
StackOverflowError
```

---

## OutOfMemoryError

Occurs when the JVM cannot allocate more memory.

```java
List<Object> list =
    new ArrayList<>();

while (true) {

    list.add(new Object());
}
```

Output

```
OutOfMemoryError
```

---

# Heap vs Stack

| Heap | Stack |
|------|-------|
| Stores objects | Stores local variables |
| Shared by threads | One stack per thread |
| Managed by GC | Automatically released after method completion |
| Larger memory | Smaller memory |

---

# JVM Memory Workflow

```text
Java Program
      │
      ▼
Class Loader
      │
      ▼
Method Area
      │
      ▼
Stack
      │
      ▼
Heap
      │
      ▼
Garbage Collector
```

---

# Real-World Applications

Understanding JVM memory helps in:

- Spring Boot applications
- High-performance systems
- Memory leak analysis
- Performance tuning
- Microservices
- Production troubleshooting

---

# Common Mistakes

### Confusing Heap and Stack

Objects are stored in the **Heap**, while local variables and method calls are stored in the **Stack**.

---

### Creating Too Many Objects

Repeated unnecessary object creation increases Garbage Collection activity.

---

### Infinite Recursion

Recursive methods without a termination condition cause:

```
StackOverflowError
```

---

# Best Practices

- Reuse objects where appropriate.
- Avoid unnecessary object creation.
- Release unused resources promptly.
- Monitor Heap usage in production.
- Understand Stack vs Heap before optimising performance.
- Use profiling tools such as VisualVM or JDK Mission Control.

---

# Summary

In this chapter, you learned:

- JVM memory architecture
- Heap Memory
- Stack Memory
- Method Area and Metaspace
- Program Counter
- Native Method Stack
- Common memory errors
- Best practices

---

# Quick Revision

- Heap stores objects.
- Stack stores local variables and method calls.
- Metaspace replaced PermGen in Java 8.
- Every thread has its own Stack and Program Counter.
- Garbage Collector manages Heap memory.
- Infinite recursion causes `StackOverflowError`.
- Excessive memory allocation can cause `OutOfMemoryError`.

---

# Practice Questions

### Basic

1. What is JVM memory?
2. What is stored in Heap memory?
3. What is stored in Stack memory?
4. What is Metaspace?
5. What is the Program Counter?

### Intermediate

6. Explain the JVM memory architecture.
7. Differentiate Heap and Stack memory.
8. What is the purpose of the Native Method Stack?

### Interview Questions

1. Explain JVM memory management.
2. What is the difference between Heap and Stack?
3. Why was PermGen replaced by Metaspace?
4. What causes `StackOverflowError` and `OutOfMemoryError`?
5. How does JVM memory management impact application performance?

---

# Hands-on Exercise

Create a **JVM Memory Demonstration** program that:

1. Create multiple objects and observe Heap usage.
2. Create methods with local variables to understand Stack memory.
3. Demonstrate a `StackOverflowError` using controlled recursion.
4. Demonstrate an `OutOfMemoryError` (in a safe test environment).
5. Display JVM memory statistics using:

```java
Runtime.getRuntime()
```

6. Compare used, free, total, and maximum memory.
7. Observe memory changes before and after object creation.
8. Explain how the Garbage Collector manages the created objects.
