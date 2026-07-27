# Chapter 23: Queue Interface

## 📖 Overview

The **Queue** interface is part of the Java Collections Framework (JCF) and is used to store elements that are processed in a specific order. A Queue generally follows the **FIFO (First In, First Out)** principle, where the first element added is the first one removed.

Queues are widely used in task scheduling, printing systems, message processing, and CPU scheduling.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the Queue interface
- Learn FIFO behavior
- Use Queue operations
- Understand PriorityQueue
- Differentiate Queue and Deque

---

# What is a Queue?

A Queue stores elements in the order they are inserted.

```
Front                          Rear

+-----+-----+-----+-----+
| 10  | 20  | 30  | 40  |
+-----+-----+-----+-----+

Remove → 10
Add → 50
```

FIFO = **First In, First Out**

---

# Queue Hierarchy

```
Collection
      │
     Queue
   ┌───┴───────────┐
   │               │
PriorityQueue   Deque
                    │
             ArrayDeque
             LinkedList
```

---

# Creating a Queue

```java
import java.util.LinkedList;
import java.util.Queue;

Queue<String> queue = new LinkedList<>();
```

---

# Adding Elements

### offer()

```java
queue.offer("Task1");
queue.offer("Task2");
queue.offer("Task3");

System.out.println(queue);
```

### Output

```
[Task1, Task2, Task3]
```

---

### add()

```java
queue.add("Task4");
```

Both `offer()` and `add()` insert elements.

> `offer()` returns `false` if insertion fails, while `add()` throws an exception.

---

# Viewing the Front Element

### peek()

```java
System.out.println(queue.peek());
```

### Output

```
Task1
```

Does **not** remove the element.

---

### element()

```java
System.out.println(queue.element());
```

Also returns the first element but throws an exception if the queue is empty.

---

# Removing Elements

### poll()

```java
System.out.println(queue.poll());
```

### Output

```
Task1
```

Queue becomes:

```
[Task2, Task3, Task4]
```

---

### remove()

```java
queue.remove();
```

Removes the first element.

If the queue is empty, it throws an exception.

---

# Common Queue Methods

| Method | Description |
|---------|-------------|
| `offer()` | Insert element |
| `add()` | Insert element |
| `peek()` | View first element |
| `element()` | View first element |
| `poll()` | Remove first element |
| `remove()` | Remove first element |
| `size()` | Number of elements |
| `isEmpty()` | Check if queue is empty |

---

# Iterating Through a Queue

```java
for (String task : queue) {

    System.out.println(task);
}
```

---

# PriorityQueue

A `PriorityQueue` orders elements based on their **natural ordering** or a custom comparator.

```java
Queue<Integer> numbers = new PriorityQueue<>();

numbers.offer(30);
numbers.offer(10);
numbers.offer(20);

System.out.println(numbers);
```

Possible Output

```
[10, 30, 20]
```

Removing elements:

```java
while (!numbers.isEmpty()) {

    System.out.println(numbers.poll());
}
```

### Output

```
10
20
30
```

---

# Queue vs PriorityQueue

| Queue (LinkedList) | PriorityQueue |
|--------------------|---------------|
| FIFO order | Priority order |
| Maintains insertion order | Maintains sorted priority |
| Used for scheduling | Used for priority processing |

---

# Deque (Double Ended Queue)

A `Deque` allows insertion and deletion from **both ends**.

Example:

```java
Deque<Integer> deque = new ArrayDeque<>();

deque.addFirst(10);
deque.addLast(20);

System.out.println(deque);
```

### Output

```
[10, 20]
```

---

# Queue Applications

Queues are commonly used in:

- Print Queue
- Task Scheduling
- CPU Scheduling
- BFS (Breadth-First Search)
- Message Queues
- Call Center Systems

---

# Real-World Example

Hospital token system:

```
Patient A
Patient B
Patient C

Treatment Order:

A
B
C
```

The first patient to register is treated first.

---

# Common Mistakes

### Using `remove()` on an Empty Queue

```java
queue.remove();
```

❌ Throws:

```
NoSuchElementException
```

Use:

```java
queue.poll();
```

---

### Using `element()` on an Empty Queue

```java
queue.element();
```

❌ Throws an exception.

Use:

```java
queue.peek();
```

---

### Expecting PriorityQueue to Preserve Insertion Order

```java
PriorityQueue<Integer> pq = new PriorityQueue<>();
```

Elements are arranged by **priority**, not insertion order.

---

# Best Practices

- Use `offer()` instead of `add()` when possible.
- Use `poll()` instead of `remove()` for safer removal.
- Use `peek()` instead of `element()` for safer access.
- Use `PriorityQueue` when sorted processing is required.
- Use `ArrayDeque` instead of `Stack` for stack-like operations.

---

# Summary

In this chapter, you learned:

- Queue interface
- FIFO principle
- Queue operations
- PriorityQueue
- Deque
- Queue applications
- Best practices

---

# Quick Revision

- Queue follows FIFO.
- `offer()` adds an element.
- `peek()` views the first element.
- `poll()` removes the first element.
- `PriorityQueue` processes elements by priority.
- `Deque` supports insertion/removal from both ends.

---

# Practice Questions

### Basic

1. What is a Queue?
2. What does FIFO mean?
3. What is the difference between `offer()` and `add()`?
4. What is the difference between `peek()` and `poll()`?
5. Which class implements the Queue interface?

### Intermediate

6. Compare `LinkedList` and `PriorityQueue`.
7. Explain the difference between `remove()` and `poll()`.
8. What is a Deque?

### Interview Questions

1. What is the difference between Queue and Deque?
2. Why is `PriorityQueue` not FIFO?
3. When should you use `PriorityQueue`?
4. Why are `offer()` and `poll()` preferred over `add()` and `remove()`?
5. Give real-world applications of the Queue interface.

---

# Hands-on Exercise

Create a **Ticket Booking System** that:

1. Create a `Queue<String>` using `LinkedList`.
2. Add five customer names.
3. Display the customer at the front using `peek()`.
4. Serve customers one by one using `poll()`.
5. Display the remaining queue after each removal.
6. Create a `PriorityQueue<Integer>` to manage ticket priorities.
7. Remove and display tickets in priority order.
