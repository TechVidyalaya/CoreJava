# Chapter 07: JVM Interview Questions

## 📖 Overview

This chapter contains frequently asked **JVM Interview Questions** covering JVM architecture, memory management, Garbage Collection, Class Loaders, Reflection, and performance tuning. These questions are commonly asked in Java Developer, Senior Java Developer, and Spring Boot interviews.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Answer common JVM interview questions
- Explain JVM internals confidently
- Understand real-world JVM concepts
- Prepare for technical interviews

---

# 1. What is JVM?

**Answer:**

The **Java Virtual Machine (JVM)** is a runtime environment that executes Java bytecode. It provides platform independence by allowing Java programs to run on any operating system with a compatible JVM.

---

# 2. What are the main components of the JVM?

**Answer:**

- Class Loader
- Runtime Data Areas
- Execution Engine
- Garbage Collector
- Native Interface (JNI)
- Native Libraries

---

# 3. Explain JVM Memory Structure.

**Answer:**

The JVM memory consists of:

- Heap
- Stack
- Method Area (Metaspace)
- Program Counter Register
- Native Method Stack

---

# 4. What is the difference between Heap and Stack?

| Heap | Stack |
|------|-------|
| Stores objects | Stores local variables |
| Shared among threads | One stack per thread |
| Managed by GC | Automatically released after method execution |
| Larger memory | Smaller memory |

---

# 5. What is Metaspace?

**Answer:**

Metaspace stores class metadata and replaced **PermGen** from Java 8 onwards. It uses native memory instead of a fixed JVM memory area.

---

# 6. What is Garbage Collection?

**Answer:**

Garbage Collection is the automatic process of identifying and removing objects that are no longer reachable, freeing Heap memory.

---

# 7. When does an object become eligible for Garbage Collection?

**Answer:**

An object becomes eligible when no live references point to it.

Example:

```java
Employee emp = new Employee();
emp = null;
```

---

# 8. What is the difference between Minor GC and Major GC?

| Minor GC | Major (Full) GC |
|----------|-----------------|
| Runs in Young Generation | Runs in Old Generation |
| Fast | Slower |
| Frequent | Less frequent |

---

# 9. What is a Memory Leak?

**Answer:**

A memory leak occurs when objects are no longer needed but are still referenced, preventing the Garbage Collector from reclaiming their memory.

---

# 10. What is Reflection?

**Answer:**

Reflection allows Java programs to inspect and manipulate classes, methods, fields, constructors, and annotations during runtime.

---

# 11. Where is Reflection used?

**Answer:**

Reflection is widely used in:

- Spring Framework
- Hibernate
- JUnit
- Jackson
- Dependency Injection
- Plugin systems

---

# 12. What are Annotations?

**Answer:**

Annotations are metadata that provide additional information to the compiler, JVM, or frameworks without changing program logic.

Example:

```java
@Override
```

---

# 13. What are Meta-Annotations?

**Answer:**

Meta-annotations define the behaviour of annotations.

Examples:

- `@Target`
- `@Retention`
- `@Inherited`
- `@Documented`
- `@Repeatable`

---

# 14. Explain the Class Loading Process.

**Answer:**

The JVM loads classes in three phases:

```text
Loading
    ↓
Linking
    ↓
Initialization
```

---

# 15. What are the built-in Class Loaders?

**Answer:**

- Bootstrap Class Loader
- Platform Class Loader
- Application Class Loader

---

# 16. What is the Parent Delegation Model?

**Answer:**

A Class Loader first delegates the class loading request to its parent. Only if the parent cannot load the class does the child attempt to load it.

This avoids duplicate class loading and improves security.

---

# 17. What is the difference between ClassNotFoundException and NoClassDefFoundError?

| ClassNotFoundException | NoClassDefFoundError |
|-------------------------|----------------------|
| Checked Exception | Error |
| Occurs during class loading | Occurs at runtime |
| Class not found | Class compiled but unavailable during execution |

---

# 18. What is JVM Performance Tuning?

**Answer:**

JVM Performance Tuning is the process of optimising memory, Garbage Collection, and JVM settings to improve application performance.

---

# 19. What do `-Xms` and `-Xmx` mean?

| Option | Description |
|--------|-------------|
| `-Xms` | Initial Heap size |
| `-Xmx` | Maximum Heap size |

Example:

```text
-Xms512m
-Xmx2g
```

---

# 20. Which tools are commonly used for JVM monitoring?

**Answer:**

- VisualVM
- JDK Mission Control
- JConsole
- Java Flight Recorder (JFR)
- Eclipse Memory Analyzer (MAT)

---

# 21. What is a Heap Dump?

**Answer:**

A Heap Dump is a snapshot of all objects stored in Heap memory. It is mainly used for analysing memory leaks and OutOfMemoryError issues.

---

# 22. What is a Thread Dump?

**Answer:**

A Thread Dump captures the state of all threads in a running JVM. It helps diagnose deadlocks, blocked threads, and high CPU usage.

---

# 23. Why is `finalize()` deprecated?

**Answer:**

`finalize()` has unpredictable execution and can negatively impact performance. Modern Java recommends using:

- Try-with-resources
- AutoCloseable
- Explicit resource cleanup

---

# 24. Which Garbage Collector is commonly used today?

**Answer:**

**G1 Garbage Collector (G1 GC)** is commonly used for enterprise applications because it provides predictable pause times and good overall performance.

---

# 25. Explain the Object Lifecycle.

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

# Top Interview Tips

- Understand **Heap vs Stack** clearly.
- Know the complete **JVM Memory Architecture**.
- Be able to explain the **Garbage Collection lifecycle**.
- Learn the **Class Loading process**.
- Understand when **Reflection** should be used.
- Practise explaining **Minor GC vs Major GC**.
- Know the purpose of JVM options like `-Xms` and `-Xmx`.
- Gain hands-on experience with JVM monitoring tools.

---

# Summary

In this chapter, you learned:

- Common JVM interview questions
- JVM architecture
- Memory management
- Garbage Collection
- Reflection
- Class Loaders
- Performance tuning
- Interview preparation tips

---

# Quick Revision

- JVM executes Java bytecode.
- Heap stores objects; Stack stores local variables.
- Metaspace replaced PermGen.
- Garbage Collection frees unused Heap memory.
- Reflection enables runtime inspection.
- Class Loaders load classes dynamically.
- G1 GC is commonly used for enterprise applications.
- VisualVM and JDK Mission Control are popular monitoring tools.

---

# Practice Questions

### Basic

1. What is JVM?
2. What is the purpose of Heap memory?
3. What is Garbage Collection?
4. Name the three built-in Class Loaders.
5. What is Reflection?

### Intermediate

6. Explain the JVM memory structure.
7. Differentiate Heap and Stack.
8. Explain the Parent Delegation Model.

### Interview Questions

1. How does the JVM execute a Java program?
2. Explain the JVM memory architecture with a diagram.
3. How does Garbage Collection work?
4. What are the advantages and disadvantages of Reflection?
5. How would you troubleshoot a Java application with high memory usage?

---

# Hands-on Exercise

Prepare for a mock JVM interview by:

1. Explaining the JVM architecture without notes.
2. Drawing the JVM memory structure.
3. Demonstrating Heap vs Stack with a Java program.
4. Showing object eligibility for Garbage Collection.
5. Displaying Class Loader information using Reflection.
6. Running an application with different Heap sizes (`-Xms` and `-Xmx`).
7. Monitoring the application using VisualVM or JDK Mission Control.
8. Answering all 25 interview questions aloud within 30 minutes.
