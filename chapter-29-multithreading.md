# Chapter 29: Multithreading

## 📖 Overview

**Multithreading** allows a Java program to execute multiple threads simultaneously. It improves application performance by enabling tasks to run concurrently, making efficient use of CPU resources.

Multithreading is widely used in web servers, games, banking systems, chat applications, and background processing.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand threads and multithreading
- Create threads in Java
- Use the Thread lifecycle
- Synchronize shared resources
- Understand thread communication
- Learn best practices

---

# What is a Thread?

A **Thread** is the smallest unit of execution within a process.

Example:

- Browser → Multiple tabs
- Music Player → Play music while downloading songs
- IDE → Compile code while editing files

---

# Process vs Thread

| Process | Thread |
|---------|---------|
| Independent program | Small execution unit |
| Higher memory usage | Shares process memory |
| Slower creation | Faster creation |
| Can contain multiple threads | Belongs to a process |

---

# What is Multithreading?

Multithreading is the execution of multiple threads concurrently.

```
Application
     │
 ┌───┼───┐
 │   │   │
Thread1 Thread2 Thread3
```

---

# Creating a Thread (Extending Thread)

```java
class MyThread extends Thread {

    @Override
    public void run() {

        System.out.println("Thread is running.");
    }
}

public class Main {

    public static void main(String[] args) {

        MyThread thread = new MyThread();

        thread.start();
    }
}
```

Output

```
Thread is running.
```

---

# Creating a Thread (Implementing Runnable)

```java
class MyTask implements Runnable {

    @Override
    public void run() {

        System.out.println("Task executed.");
    }
}

public class Main {

    public static void main(String[] args) {

        Thread thread = new Thread(new MyTask());

        thread.start();
    }
}
```

---

# start() vs run()

```java
thread.start();
```

Creates a new thread.

```java
thread.run();
```

Executes like a normal method in the current thread.

Always use **start()** to create a new thread.

---

# Thread Lifecycle

```
New
 │
 ▼
Runnable
 │
 ▼
Running
 │
 ├────► Waiting / Blocked
 │
 ▼
Terminated
```

---

# Current Thread

```java
System.out.println(
    Thread.currentThread().getName()
);
```

Output

```
main
```

---

# Sleeping a Thread

```java
try {

    Thread.sleep(2000);

} catch (InterruptedException e) {

    e.printStackTrace();
}
```

Pauses the current thread for 2 seconds.

---

# Joining Threads

`join()` waits for another thread to finish.

```java
Thread t = new Thread(new MyTask());

t.start();

t.join();

System.out.println("Completed");
```

---

# Thread Priority

```java
thread.setPriority(Thread.MAX_PRIORITY);
```

Constants:

```java
Thread.MIN_PRIORITY
Thread.NORM_PRIORITY
Thread.MAX_PRIORITY
```

Priority is only a scheduling hint and is **not guaranteed**.

---

# Synchronization

When multiple threads access shared data, inconsistent results may occur.

```java
class Counter {

    private int count = 0;

    public synchronized void increment() {

        count++;
    }

    public int getCount() {

        return count;
    }
}
```

Only one thread can execute the synchronized method at a time.

---

# Synchronized Block

```java
synchronized (this) {

    count++;
}
```

Locks only the required block instead of the whole method.

---

# Thread Communication

Common methods:

```java
wait()

notify()

notifyAll()
```

These methods are used inside synchronized blocks for communication between threads.

---

# Lambda with Thread

```java
Thread thread = new Thread(() -> {

    System.out.println("Hello from Thread");
});

thread.start();
```

---

# Executor Framework (Recommended)

Instead of creating threads manually:

```java
ExecutorService executor =
    Executors.newFixedThreadPool(2);

executor.submit(() ->
    System.out.println("Task Running"));

executor.shutdown();
```

The Executor Framework manages thread creation efficiently.

---

# Common Thread Methods

| Method | Description |
|---------|-------------|
| `start()` | Starts a thread |
| `run()` | Thread task |
| `sleep()` | Pauses execution |
| `join()` | Waits for completion |
| `currentThread()` | Returns current thread |
| `setPriority()` | Sets priority |
| `isAlive()` | Checks if thread is running |

---

# Thread vs Runnable

| Thread | Runnable |
|---------|----------|
| Extends `Thread` | Implements `Runnable` |
| Cannot extend another class | Can extend another class |
| Less flexible | Preferred approach |
| Direct thread object | Separate task and thread |

---

# Real-World Applications

Multithreading is used in:

- Web servers
- Banking systems
- Video streaming
- Online games
- Background downloads
- Email applications
- Chat applications

---

# Common Mistakes

### Calling run() Instead of start()

Incorrect:

```java
thread.run();
```

Correct:

```java
thread.start();
```

---

### Ignoring Synchronization

```java
count++;
```

Multiple threads may update the same value simultaneously, causing race conditions.

---

### Forgetting shutdown()

```java
ExecutorService executor =
    Executors.newFixedThreadPool(2);
```

Always call:

```java
executor.shutdown();
```

---

# Best Practices

- Prefer implementing `Runnable` over extending `Thread`.
- Use the **Executor Framework** for thread management.
- Synchronize only shared resources.
- Avoid unnecessary synchronization.
- Handle `InterruptedException` properly.
- Keep thread tasks small and independent.

---

# Summary

In this chapter, you learned:

- Threads and multithreading
- Creating threads
- Thread lifecycle
- Synchronization
- Thread communication
- Executor Framework
- Best practices

---

# Quick Revision

- A thread is a lightweight unit of execution.
- Use `start()` to create a new thread.
- `Runnable` is preferred over extending `Thread`.
- `sleep()` pauses a thread.
- `join()` waits for another thread.
- `synchronized` prevents race conditions.
- Use `ExecutorService` for better thread management.

---

# Practice Questions

### Basic

1. What is a thread?
2. What is multithreading?
3. What is the difference between `start()` and `run()`?
4. What does `sleep()` do?
5. What is synchronization?

### Intermediate

6. Compare `Thread` and `Runnable`.
7. Explain the thread lifecycle.
8. What is the purpose of `join()`?

### Interview Questions

1. Why is `Runnable` preferred over extending `Thread`?
2. What is a race condition?
3. What is synchronization in Java?
4. What is the Executor Framework?
5. What are `wait()`, `notify()`, and `notifyAll()` used for?

---

# Hands-on Exercise

Create a **Bank Account Simulator** that:

1. Create a `BankAccount` class with a balance.
2. Create two threads:
   - Deposit money
   - Withdraw money
3. Use `synchronized` methods to ensure thread safety.
4. Print the balance after each transaction.
5. Repeat the same using an `ExecutorService`.
6. Observe the difference by running the program with and without synchronization.
