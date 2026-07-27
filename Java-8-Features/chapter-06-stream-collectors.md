# Chapter 06: Stream Collectors

## 📖 Overview

The **Collectors** utility class provides a set of methods to collect the results of a Stream into collections, maps, strings, or summary statistics.

It is part of the **Stream API** and is commonly used with the `collect()` terminal operation.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the Collectors class
- Use common collector methods
- Convert Streams into collections
- Group and partition data
- Perform summarization operations
- Apply Collectors in real-world scenarios

---

# What is Collectors?

`Collectors` is a utility class in the `java.util.stream` package.

It provides predefined collectors that are used with the `collect()` method.

```java
import java.util.stream.Collectors;
```

General syntax:

```java
stream.collect(Collectors.method());
```

---

# Collecting to a List

```java
List<String> names =
    Arrays.asList("Rahul", "Neha", "Amit");

List<String> result =
    names.stream()
         .filter(name -> name.length() > 4)
         .collect(Collectors.toList());

System.out.println(result);
```

Output

```
[Rahul]
```

---

# Collecting to a Set

```java
Set<String> result =
    names.stream()
         .collect(Collectors.toSet());
```

Duplicates are automatically removed.

---

# Collecting to a Map

```java
List<Student> students = Arrays.asList(
    new Student(101, "Rahul"),
    new Student(102, "Neha")
);

Map<Integer, String> map =
    students.stream()
            .collect(Collectors.toMap(
                Student::getId,
                Student::getName
            ));

System.out.println(map);
```

Output

```
{101=Rahul, 102=Neha}
```

---

# Joining Strings

Combine multiple strings into one.

```java
String result =
    names.stream()
         .collect(Collectors.joining(", "));

System.out.println(result);
```

Output

```
Rahul, Neha, Amit
```

---

# Counting Elements

```java
long count =
    names.stream()
         .collect(Collectors.counting());

System.out.println(count);
```

Output

```
3
```

---

# Summing Values

```java
int totalSalary =
    employees.stream()
             .collect(Collectors.summingInt(
                 Employee::getSalary
             ));

System.out.println(totalSalary);
```

---

# Averaging Values

```java
double averageSalary =
    employees.stream()
             .collect(Collectors.averagingInt(
                 Employee::getSalary
             ));
```

---

# Finding Maximum

```java
Optional<Employee> highestPaid =
    employees.stream()
             .collect(Collectors.maxBy(
                 Comparator.comparing(
                     Employee::getSalary
                 )));
```

---

# Finding Minimum

```java
Optional<Employee> lowestPaid =
    employees.stream()
             .collect(Collectors.minBy(
                 Comparator.comparing(
                     Employee::getSalary
                 )));
```

---

# Grouping Elements

Group employees by department.

```java
Map<String, List<Employee>> grouped =
    employees.stream()
             .collect(Collectors.groupingBy(
                 Employee::getDepartment
             ));
```

Example Output

```
IT
  Rahul
  Amit

HR
  Neha
```

---

# Partitioning Data

Split data into two groups based on a condition.

```java
Map<Boolean, List<Employee>> result =
    employees.stream()
             .collect(Collectors.partitioningBy(
                 e -> e.getSalary() > 50000
             ));
```

Output

```
true  -> Employees with salary > 50000

false -> Remaining employees
```

---

# Mapping Collector

Transform values before collecting.

```java
List<String> names =
    employees.stream()
             .collect(Collectors.mapping(
                 Employee::getName,
                 Collectors.toList()
             ));
```

---

# Summary Statistics

```java
IntSummaryStatistics stats =
    employees.stream()
             .collect(Collectors.summarizingInt(
                 Employee::getSalary
             ));

System.out.println(stats);
```

Example Output

```
count=5
sum=250000
min=30000
average=50000.0
max=70000
```

---

# Common Collectors

| Collector | Purpose |
|-----------|---------|
| `toList()` | Collect into List |
| `toSet()` | Collect into Set |
| `toMap()` | Collect into Map |
| `joining()` | Join strings |
| `counting()` | Count elements |
| `groupingBy()` | Group elements |
| `partitioningBy()` | Divide into two groups |
| `mapping()` | Transform while collecting |
| `summingInt()` | Sum integers |
| `averagingInt()` | Calculate average |
| `summarizingInt()` | Summary statistics |

---

# Real-World Applications

Collectors are widely used in:

- Employee management systems
- Sales reports
- Dashboard analytics
- Student result processing
- E-commerce applications
- Spring Boot REST APIs

---

# Common Mistakes

### Duplicate Keys in toMap()

```java
Collectors.toMap(
    Student::getId,
    Student::getName
);
```

If duplicate keys exist, an exception is thrown.

Use a merge function if duplicates are possible.

---

### Forgetting collect()

Incorrect:

```java
stream.filter(...)
      .map(...);
```

Without `collect()` or another terminal operation, the stream is not executed.

---

### Using groupingBy() Unnecessarily

If only two groups are needed, prefer:

```java
Collectors.partitioningBy(...)
```

---

# Best Practices

- Use `toList()` for ordered collections.
- Use `toSet()` to remove duplicates.
- Use `groupingBy()` for categorisation.
- Use `partitioningBy()` for true/false conditions.
- Prefer `summarizingInt()` when multiple statistics are required.

---

# Summary

In this chapter, you learned:

- Collectors class
- `collect()` method
- List, Set, and Map collectors
- Grouping and partitioning
- Joining strings
- Summary statistics
- Best practices

---

# Quick Revision

- `Collectors` works with the `collect()` terminal operation.
- `toList()` creates a List.
- `toSet()` removes duplicates.
- `toMap()` converts a Stream into a Map.
- `groupingBy()` groups similar elements.
- `partitioningBy()` divides data into two groups.
- `summarizingInt()` calculates count, sum, min, max, and average.

---

# Practice Questions

### Basic

1. What is the purpose of the `Collectors` class?
2. Which method collects data into a List?
3. What does `joining()` do?
4. What is `groupingBy()` used for?
5. What is the difference between `toList()` and `toSet()`?

### Intermediate

6. Explain `partitioningBy()` with an example.
7. What happens if duplicate keys are used with `toMap()`?
8. When should `summarizingInt()` be preferred?

### Interview Questions

1. What is the role of Collectors in the Stream API?
2. Differentiate `groupingBy()` and `partitioningBy()`.
3. Explain `toMap()` with duplicate key handling.
4. What are summary statistics in Streams?
5. Which Collectors are most commonly used in enterprise applications?

---

# Hands-on Exercise

Create an **Employee Management** program that:

1. Create a list of employees with:
   - ID
   - Name
   - Department
   - Salary
2. Collect employee names into a `List`.
3. Collect departments into a `Set`.
4. Create a `Map` of Employee ID to Employee Name.
5. Group employees by department.
6. Partition employees based on salary greater than ₹50,000.
7. Calculate:
   - Total salary
   - Average salary
   - Highest salary
   - Summary statistics
8. Print all collected results.
