# Chapter 05: JVM Performance Tuning

## 📖 Overview

**JVM Performance Tuning** is the process of configuring the Java Virtual Machine to improve application performance, reduce memory usage, and minimise Garbage Collection pauses.

Performance tuning is crucial for **enterprise applications**, **Spring Boot services**, **microservices**, and **high-traffic systems**.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand JVM performance tuning
- Configure Heap memory
- Tune Garbage Collection
- Monitor JVM performance
- Identify performance bottlenecks
- Follow JVM tuning best practices

---

# What is JVM Performance Tuning?

JVM Performance Tuning involves adjusting JVM settings to achieve:

- Faster application performance
- Lower memory consumption
- Reduced GC pauses
- Better CPU utilisation
- Improved application stability

---

# Performance Factors

The main factors affecting JVM performance are:

- Heap Size
- Garbage Collection
- CPU Usage
- Thread Count
- Memory Allocation
- Object Creation
- Class Loading

---

# JVM Memory Settings

The Heap size can be configured using JVM options.

Initial Heap Size

```text
-Xms512m
```

Maximum Heap Size

```text
-Xmx2g
```

Example:

```text
java -Xms512m -Xmx2g Main
```

---

# Choosing Heap Size

| Option | Purpose |
|---------|---------|
| `-Xms` | Initial Heap size |
| `-Xmx` | Maximum Heap size |

Example:

```text
-Xms1g

-Xmx4g
```

Keeping `-Xms` and `-Xmx` close to each other can reduce Heap resizing overhead.

---

# Selecting a Garbage Collector

Choose an appropriate GC depending on the application.

```text
-XX:+UseSerialGC
```

```text
-XX:+UseParallelGC
```

```text
-XX:+UseG1GC
```

---

# G1 Garbage Collector

G1 (Garbage First) is designed for:

- Large Heap sizes
- Predictable pause times
- High-performance applications

Example:

```text
-XX:+UseG1GC
```

---

# Monitoring Memory

The JVM provides memory statistics.

```java
Runtime runtime =
    Runtime.getRuntime();

System.out.println(
    runtime.totalMemory()
);

System.out.println(
    runtime.freeMemory()
);

System.out.println(
    runtime.maxMemory()
);
```

---

# JVM Monitoring Tools

Common tools include:

| Tool | Purpose |
|------|---------|
| VisualVM | Monitor memory and CPU |
| JDK Mission Control | Performance analysis |
| JConsole | JVM monitoring |
| Java Flight Recorder (JFR) | Runtime profiling |

---

# Thread Dumps

A thread dump shows the current state of all threads.

Generate using:

```text
jstack <PID>
```

Useful for analysing:

- Deadlocks
- Blocked threads
- High CPU usage

---

# Heap Dumps

A Heap dump captures objects stored in Heap memory.

Generate using:

```text
jmap -dump:file=heap.hprof <PID>
```

Analyse the dump using:

- VisualVM
- Eclipse Memory Analyzer (MAT)

---

# Garbage Collection Logs

Enable GC logging.

Java 8:

```text
-XX:+PrintGCDetails

-XX:+PrintGCDateStamps

-Xloggc:gc.log
```

GC logs help identify:

- Frequent collections
- Long pause times
- Memory pressure

---

# Reduce Object Creation

Avoid:

```java
for(int i = 0; i < 1000000; i++) {

    String s =
        new String("Java");
}
```

Better:

```java
String s = "Java";

for(int i = 0; i < 1000000; i++) {

    System.out.println(s);
}
```

Fewer objects reduce GC activity.

---

# Use Efficient Collections

Choose the appropriate collection.

| Requirement | Collection |
|-------------|------------|
| Fast lookup | HashMap |
| Ordered data | TreeMap |
| Dynamic list | ArrayList |
| Frequent insert/delete | LinkedList |

Selecting the right collection improves performance.

---

# Avoid Memory Leaks

Common causes:

- Static collections
- Unclosed resources
- Event listeners
- Cache growth
- Long-lived object references

Always remove unused references.

---

# Performance Workflow

```text
Slow Application
        │
        ▼
Collect Metrics
        │
        ▼
Identify Bottleneck
        │
        ▼
Tune JVM Settings
        │
        ▼
Test Again
        │
        ▼
Deploy
```

---

# Real-World Applications

JVM tuning is important in:

- Spring Boot services
- Banking systems
- E-commerce platforms
- Streaming applications
- Cloud deployments
- High-volume REST APIs

---

# Common Mistakes

### Increasing Heap Without Analysis

A larger Heap is not always better.

It can increase Full GC pause times.

---

### Ignoring GC Logs

GC logs provide valuable information about memory usage and should be analysed before changing JVM settings.

---

### Excessive Object Creation

Creating many temporary objects increases GC overhead and reduces performance.

---

# Best Practices

- Measure performance before tuning.
- Start with JVM defaults unless profiling indicates a problem.
- Use G1 GC for most enterprise workloads.
- Keep object creation under control.
- Monitor Heap and GC regularly.
- Use profiling tools instead of guessing performance issues.
- Test JVM changes in a staging environment before production.

---

# Summary

In this chapter, you learned:

- JVM Performance Tuning
- Heap configuration
- Garbage Collector selection
- Monitoring tools
- Heap dumps
- Thread dumps
- GC logging
- Performance best practices

---

# Quick Revision

- `-Xms` sets the initial Heap size.
- `-Xmx` sets the maximum Heap size.
- G1 GC is suitable for many enterprise applications.
- Use VisualVM and JDK Mission Control for monitoring.
- Heap dumps analyse memory usage.
- Thread dumps analyse thread issues.
- Always profile before tuning.

---

# Practice Questions

### Basic

1. What is JVM Performance Tuning?
2. What do `-Xms` and `-Xmx` represent?
3. Which tool is used to analyse Heap memory?
4. What is a Heap dump?
5. What is a Thread dump?

### Intermediate

6. Why are GC logs useful?
7. When should G1 GC be used?
8. How does reducing object creation improve performance?

### Interview Questions

1. Explain JVM Performance Tuning.
2. How do you investigate a Java application with high memory usage?
3. What is the difference between a Heap dump and a Thread dump?
4. Which JVM tools have you used for performance analysis?
5. What JVM tuning steps would you perform for a slow Spring Boot application?

---

# Hands-on Exercise

Create a **JVM Performance Analyzer** that:

1. Display JVM memory statistics using `Runtime`.
2. Run the application with different Heap sizes using `-Xms` and `-Xmx`.
3. Enable GC logging and analyse the output.
4. Generate a Heap dump using `jmap`.
5. Generate a Thread dump using `jstack`.
6. Monitor the application using VisualVM or JDK Mission Control.
7. Compare the performance using different Garbage Collectors.
8. Document your observations and recommend the best JVM configuration for the application.
