# Chapter 18: Enum

## 📖 Overview

An **Enum (Enumeration)** is a special Java data type used to define a fixed set of constants. Enums improve code readability, type safety, and reduce errors caused by invalid values.

For example, days of the week, months, order status, and payment status are ideal candidates for enums.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand enums
- Create and use enums
- Access enum values
- Use enum methods
- Add fields and methods to enums
- Use enums in switch statements

---

# What is an Enum?

An enum is a collection of predefined constant values.

Example:

```java
enum Day {
    MONDAY,
    TUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY,
    SATURDAY,
    SUNDAY
}
```

---

# Why Use Enums?

Instead of using Strings:

```java
String status = "COMPLETED";
```

Someone could accidentally write:

```java
status = "Complete";
```

Using an enum:

```java
Status status = Status.COMPLETED;
```

Only valid values are allowed.

---

# Creating an Enum

```java
enum Status {

    PENDING,
    PROCESSING,
    COMPLETED,
    CANCELLED

}
```

---

# Using an Enum

```java
public class Main {

    public static void main(String[] args) {

        Status orderStatus = Status.COMPLETED;

        System.out.println(orderStatus);
    }
}
```

### Output

```
COMPLETED
```

---

# Enum in a Switch Statement

```java
Status status = Status.PROCESSING;

switch (status) {

    case PENDING:
        System.out.println("Order Pending");
        break;

    case PROCESSING:
        System.out.println("Order Processing");
        break;

    case COMPLETED:
        System.out.println("Order Completed");
        break;

    default:
        System.out.println("Cancelled");
}
```

### Output

```
Order Processing
```

---

# values()

Returns all enum constants.

```java
for (Status status : Status.values()) {

    System.out.println(status);
}
```

### Output

```
PENDING
PROCESSING
COMPLETED
CANCELLED
```

---

# valueOf()

Returns the enum constant for a given name.

```java
Status status = Status.valueOf("PENDING");

System.out.println(status);
```

### Output

```
PENDING
```

---

# ordinal()

Returns the position of the constant.

```java
System.out.println(Status.COMPLETED.ordinal());
```

### Output

```
2
```

> Avoid using `ordinal()` for business logic, as positions may change.

---

# name()

Returns the constant name.

```java
System.out.println(Status.CANCELLED.name());
```

### Output

```
CANCELLED
```

---

# Enum with Fields

Enums can have variables.

```java
enum Status {

    PENDING("Pending"),
    COMPLETED("Completed");

    private String message;

    Status(String message) {
        this.message = message;
    }

    public String getMessage() {
        return message;
    }
}
```

Usage:

```java
System.out.println(Status.COMPLETED.getMessage());
```

### Output

```
Completed
```

---

# Enum with Methods

```java
enum PaymentStatus {

    SUCCESS,
    FAILED;

    public boolean isSuccessful() {
        return this == SUCCESS;
    }
}
```

Usage:

```java
System.out.println(PaymentStatus.SUCCESS.isSuccessful());
```

### Output

```
true
```

---

# Enum with Constructor

Constructors in enums are always **private**.

```java
enum Size {

    SMALL(30),
    MEDIUM(40),
    LARGE(50);

    private int value;

    Size(int value) {
        this.value = value;
    }

    public int getValue() {
        return value;
    }
}
```

---

# Enum in Real-World Applications

Enums are commonly used for:

- Order Status
- Payment Status
- User Roles
- Days of Week
- Months
- Traffic Signals
- HTTP Methods
- Log Levels

Example:

```java
enum UserRole {

    ADMIN,
    TRAINER,
    STUDENT
}
```

---

# Enum vs Constants

Instead of:

```java
public static final String ADMIN = "ADMIN";
```

Use:

```java
enum Role {

    ADMIN,
    USER,
    GUEST

}
```

Enums are more readable and type-safe.

---

# Common Mistakes

### Comparing Enum with Strings

Incorrect:

```java
if (status.equals("PENDING")) {

}
```

Correct:

```java
if (status == Status.PENDING) {

}
```

---

### Using `ordinal()` as Database Value

```java
status.ordinal();
```

If enum order changes, stored values become incorrect.

Prefer storing the enum name or a custom code.

---

### Creating Enum Objects

Incorrect:

```java
new Status();
```

Enums cannot be instantiated using `new`.

---

# Best Practices

- Use enums for fixed sets of constants.
- Compare enums using `==`.
- Avoid using `ordinal()` for business logic.
- Add fields and methods when additional information is required.
- Use meaningful enum names in uppercase.

---

# Summary

In this chapter, you learned:

- Enum basics
- Creating enums
- Enum methods
- Enum constructors
- Enum fields
- Enum methods
- Enum in switch statements
- Best practices

---

# Quick Revision

- Enum represents a fixed set of constants.
- Enums improve type safety.
- Use `values()` to get all constants.
- Use `valueOf()` to convert String to enum.
- Compare enums using `==`.
- Enums can have constructors, fields, and methods.

---

# Practice Questions

### Basic

1. What is an enum?
2. Why are enums used?
3. How do you create an enum?
4. What does `values()` return?
5. What is the purpose of `valueOf()`?

### Intermediate

6. Explain the difference between enums and constants.
7. Can enums have constructors and methods?
8. Why should enums be compared using `==`?

### Interview Questions

1. Can an enum extend another class?
2. Why are enum constructors private?
3. What is the difference between `name()` and `ordinal()`?
4. Why should `ordinal()` not be used in database storage?
5. Give real-world examples where enums are useful.

---

# Hands-on Exercise

Create an enum named `OrderStatus` with the following constants:

- NEW
- CONFIRMED
- SHIPPED
- DELIVERED
- CANCELLED

Requirements:

1. Add a display message for each status.
2. Create a method `getMessage()`.
3. Print all enum values using `values()`.
4. Use a `switch` statement to display different messages for each status.
5. Display the name and message of every status.
