# Chapter 19: Exception Handling

## 📖 Overview

Exception Handling is a mechanism in Java used to handle runtime errors gracefully without terminating the program. It allows developers to identify, handle, and recover from unexpected situations such as invalid input, file errors, or division by zero.

Java provides a robust exception handling mechanism using **try**, **catch**, **finally**, **throw**, and **throws**.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand exceptions
- Differentiate errors and exceptions
- Use try-catch blocks
- Handle multiple exceptions
- Use finally block
- Create custom exceptions
- Understand throw and throws

---

# What is an Exception?

An **Exception** is an event that interrupts the normal flow of a program during execution.

Example:

```java
int result = 10 / 0;
```

### Output

```
Exception in thread "main"
java.lang.ArithmeticException: / by zero
```

---

# Exception Hierarchy

```
Throwable
│
├── Error
│   ├── OutOfMemoryError
│   └── StackOverflowError
│
└── Exception
    ├── IOException
    ├── SQLException
    ├── ClassNotFoundException
    ├── RuntimeException
        ├── ArithmeticException
        ├── NullPointerException
        ├── ArrayIndexOutOfBoundsException
        └── NumberFormatException
```

---

# Errors vs Exceptions

| Error | Exception |
|--------|-----------|
| Serious problem | Recoverable problem |
| Usually cannot be handled | Can be handled |
| Caused by JVM | Caused by program or environment |
| Example: `OutOfMemoryError` | Example: `IOException` |

---

# Types of Exceptions

## Checked Exceptions

Checked at compile time.

Examples:

- IOException
- SQLException
- FileNotFoundException

These must be handled or declared using `throws`.

---

## Unchecked Exceptions

Occur during runtime.

Examples:

- ArithmeticException
- NullPointerException
- ArrayIndexOutOfBoundsException
- NumberFormatException

---

# try-catch Block

```java
public class Main {

    public static void main(String[] args) {

        try {

            int result = 10 / 0;

        } catch (ArithmeticException e) {

            System.out.println("Cannot divide by zero.");
        }

        System.out.println("Program continues...");
    }
}
```

### Output

```
Cannot divide by zero.
Program continues...
```

---

# Multiple catch Blocks

```java
try {

    String s = null;

    System.out.println(s.length());

} catch (NullPointerException e) {

    System.out.println("Null value.");

} catch (Exception e) {

    System.out.println("General exception.");
}
```

---

# finally Block

The `finally` block always executes whether an exception occurs or not.

```java
try {

    System.out.println("Inside try");

} finally {

    System.out.println("Cleanup completed");
}
```

### Output

```
Inside try
Cleanup completed
```

Typical uses:

- Closing files
- Closing database connections
- Releasing resources

---

# try-catch-finally

```java
try {

    int result = 10 / 2;

} catch (Exception e) {

    System.out.println(e.getMessage());

} finally {

    System.out.println("Execution completed.");
}
```

---

# throw Keyword

Used to explicitly throw an exception.

```java
int age = 15;

if (age < 18) {

    throw new IllegalArgumentException("Age must be 18 or above.");
}
```

---

# throws Keyword

Used to declare that a method may throw an exception.

```java
import java.io.IOException;

public void readFile() throws IOException {

    // File reading logic
}
```

---

# throw vs throws

| throw | throws |
|--------|---------|
| Throws an exception | Declares possible exceptions |
| Used inside a method | Used in method declaration |
| Throws one exception at a time | Can declare multiple exceptions |

---

# Custom Exception

Create your own exception by extending `Exception`.

```java
class InvalidAgeException extends Exception {

    public InvalidAgeException(String message) {

        super(message);
    }
}
```

Usage:

```java
if (age < 18) {

    throw new InvalidAgeException("Invalid age");
}
```

---

# Common Runtime Exceptions

| Exception | Cause |
|-----------|-------|
| ArithmeticException | Division by zero |
| NullPointerException | Accessing null object |
| ArrayIndexOutOfBoundsException | Invalid array index |
| NumberFormatException | Invalid number conversion |
| ClassCastException | Invalid object casting |

---

# Exception Handling Flow

```
Start
   │
   ▼
try Block
   │
Exception?
 ┌─┴──────────┐
 │            │
No          Yes
 │            │
 ▼            ▼
Continue   catch Block
 │            │
 └──────┬─────┘
        ▼
   finally Block
        ▼
      End
```

---

# Best Practices

- Catch specific exceptions before generic ones.
- Avoid empty `catch` blocks.
- Use `finally` or try-with-resources to release resources.
- Create custom exceptions for business rules.
- Never use exceptions for normal program flow.

---

# Common Mistakes

### Catching Generic Exception First

Incorrect:

```java
catch (Exception e) {

}

catch (ArithmeticException e) {

}
```

Specific exceptions become unreachable.

---

### Empty Catch Block

```java
catch (Exception e) {

}
```

Always log or handle the exception appropriately.

---

### Ignoring Resource Cleanup

Always close files, streams, and database connections using `finally` or try-with-resources.

---

# Summary

In this chapter, you learned:

- Exception hierarchy
- Checked and unchecked exceptions
- try, catch, finally
- throw and throws
- Custom exceptions
- Exception handling best practices

---

# Quick Revision

- Exceptions interrupt normal program execution.
- Checked exceptions must be handled or declared.
- Unchecked exceptions occur at runtime.
- `try` contains risky code.
- `catch` handles exceptions.
- `finally` always executes.
- `throw` throws an exception.
- `throws` declares possible exceptions.

---

# Practice Questions

### Basic

1. What is an exception?
2. What is the difference between Error and Exception?
3. What is the purpose of the `try` block?
4. When does the `finally` block execute?
5. What is the difference between checked and unchecked exceptions?

### Intermediate

6. Explain `throw` and `throws` with examples.
7. Why should specific exceptions be caught before generic ones?
8. How do you create a custom exception?

### Interview Questions

1. What is the difference between checked and unchecked exceptions?
2. Explain the exception hierarchy in Java.
3. What is the purpose of the `finally` block?
4. What is the difference between `throw` and `throws`?
5. When should you create a custom exception?

---

# Hands-on Exercise

Create a **BankAccount** program that:

1. Accepts a withdrawal amount.
2. Throws a custom `InsufficientBalanceException` if the balance is insufficient.
3. Uses `try-catch-finally` to handle the exception.
4. Prints a success message for valid withdrawals.
5. Always displays `"Transaction Completed"` from the `finally` block.
