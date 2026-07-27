# Chapter 15: Mini Project – Employee Management System (Java 8)

## 📖 Overview

In this chapter, you'll build a **console-based Employee Management System** using the major features introduced in **Java 8**. This project reinforces concepts learned throughout the module and demonstrates how Java 8 features work together in a real-world application.

---

# 🎯 Learning Objectives

After completing this project, you will be able to:

- Apply Lambda Expressions
- Use Functional Interfaces
- Process data using Stream API
- Use Collectors for grouping and summarising
- Handle null values with Optional
- Format dates using the Date & Time API
- Perform asynchronous operations with CompletableFuture

---

# Project Requirements

The application should manage employees with the following details:

- Employee ID
- Name
- Department
- Salary
- Joining Date

Example:

| ID | Name | Department | Salary | Joining Date |
|----|------|------------|--------|--------------|
| 101 | Rahul | IT | 65000 | 2022-01-15 |
| 102 | Neha | HR | 52000 | 2021-09-20 |
| 103 | Amit | IT | 78000 | 2020-03-10 |
| 104 | Priya | Finance | 60000 | 2023-06-01 |

---

# Features to Implement

## 1. Display All Employees

Print all employee details.

---

## 2. Search Employee

Search by Employee ID.

Use:

```java
Optional<Employee>
```

Return:

- Employee details if found
- "Employee Not Found" otherwise

---

## 3. Filter Employees

Display employees whose salary is greater than:

```text
50000
```

Use:

```java
filter()
```

---

## 4. Sort Employees

Sort employees by:

- Name
- Salary
- Joining Date

Use:

```java
sorted()
```

---

## 5. Convert Names to Uppercase

Use:

```java
map()
```

Example:

```
Rahul

↓

RAHUL
```

---

## 6. Department-wise Grouping

Group employees by department.

Use:

```java
Collectors.groupingBy()
```

Example:

```
IT
 Rahul
 Amit

HR
 Neha

Finance
 Priya
```

---

## 7. Salary Statistics

Calculate:

- Total Salary
- Average Salary
- Highest Salary
- Lowest Salary

Use:

```java
Collectors.summarizingInt()
```

---

## 8. Recent Employees

Display employees who joined after a specific date.

Example:

```java
joiningDate.isAfter(
    LocalDate.of(2022, 1, 1)
);
```

---

## 9. Asynchronous Report Generation

Generate an employee report in the background.

Use:

```java
CompletableFuture
```

Example:

```
Generating Report...

Report Generated Successfully
```

---

## 10. Display Current Date

Print the current date.

Use:

```java
LocalDate.now()
```

---

# Java 8 Features Used

| Feature | Usage |
|---------|-------|
| Lambda Expressions | Filtering and sorting |
| Functional Interfaces | Predicates and Functions |
| Method References | Printing data |
| Stream API | Collection processing |
| Collectors | Grouping and statistics |
| Optional | Employee search |
| Date & Time API | Joining dates |
| CompletableFuture | Background processing |

---

# Suggested Project Structure

```text
EmployeeManagementSystem/

│── Employee.java
│── EmployeeService.java
│── Main.java
│── Utils.java
```

---

# Expected Output

```text
========== Employee Management ==========
1. Display Employees
2. Search Employee
3. Filter Salary > 50000
4. Sort by Salary
5. Group by Department
6. Salary Statistics
7. Generate Report
8. Exit
=========================================
```

Example:

```text
Employee Found

ID : 101
Name : Rahul
Department : IT
Salary : 65000
Joining Date : 2022-01-15
```

Statistics:

```text
Total Employees : 4

Total Salary : 255000

Average Salary : 63750

Highest Salary : 78000

Lowest Salary : 52000
```

---

# Possible Enhancements

- Add new employee
- Update employee details
- Delete employee
- Save data to a file
- Read data from CSV
- Export reports
- Add logging
- Build REST APIs using Spring Boot

---

# Best Practices

- Use Streams instead of loops where appropriate.
- Use Method References for cleaner code.
- Avoid `Optional.get()` without checking.
- Keep stream pipelines simple.
- Handle asynchronous exceptions properly.
- Separate business logic from the main class.

---

# Summary

In this project, you applied:

- Lambda Expressions
- Functional Interfaces
- Stream API
- Collectors
- Optional
- Date & Time API
- CompletableFuture

You now have a practical understanding of how Java 8 features work together to build clean, modern Java applications.

---

# Quick Revision

- Use Streams to process collections.
- Use Collectors for grouping and summarising.
- Use Optional for safe null handling.
- Use LocalDate for date operations.
- Use CompletableFuture for asynchronous tasks.
- Keep Java 8 code readable and maintainable.

---

# Practice Challenges

### Basic

1. Display employees sorted by name.
2. Find employees from the IT department.
3. Print employee names in uppercase.

### Intermediate

4. Find employees who joined after a given date.
5. Calculate department-wise average salary.
6. Display the top 3 highest-paid employees.

### Advanced

7. Generate reports asynchronously using `CompletableFuture`.
8. Export employee data to a CSV file using Java I/O.
9. Extend the application to support CRUD operations.
10. Convert this console application into a Spring Boot REST API.

---

# Congratulations 🎉

You have successfully completed the **Java 8 Features** module.

You now understand:

- Functional Programming in Java
- Lambda Expressions
- Functional Interfaces
- Method References
- Stream API
- Collectors
- Optional
- Date & Time API
- Default & Static Methods
- Base64 API
- CompletableFuture
- Java 8 Best Practices

These concepts form the foundation for modern Java development and are heavily used in **Spring Boot**, **Microservices**, and enterprise applications.
