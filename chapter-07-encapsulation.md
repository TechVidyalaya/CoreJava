# Chapter 07: Encapsulation

## 📖 Overview

**Encapsulation** is one of the four pillars of Object-Oriented Programming (OOP). It is the process of **wrapping data (variables) and methods together into a single unit (class)** while restricting direct access to the data.

In Java, encapsulation is achieved by making variables **private** and providing controlled access through **getter** and **setter** methods.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand encapsulation
- Protect object data using access modifiers
- Create getter and setter methods
- Understand the advantages of encapsulation
- Apply encapsulation in real-world applications

---

# What is Encapsulation?

Encapsulation means:

- Combining data and methods into one class.
- Hiding internal data from direct access.
- Allowing controlled access using methods.

Think of a **capsule** where everything is enclosed together.

---

# Why Do We Need Encapsulation?

Without encapsulation:

- Anyone can modify object data.
- Invalid values can be assigned.
- Data security is compromised.

Example:

```java
class Student {

    public int age;
}
```

```java
Student s = new Student();

s.age = -10;
```

Here, an invalid age is assigned.

---

# Using Encapsulation

```java
class Student {

    private int age;

    public void setAge(int age) {
        this.age = age;
    }

    public int getAge() {
        return age;
    }
}
```

Now the variable cannot be accessed directly.

---

# Getter and Setter Methods

### Setter

Used to assign a value.

```java
public void setAge(int age) {

    this.age = age;
}
```

---

### Getter

Used to retrieve a value.

```java
public int getAge() {

    return age;
}
```

---

# Complete Example

```java
class Student {

    private String name;
    private int age;

    public void setName(String name) {
        this.name = name;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }
}
```

```java
public class Main {

    public static void main(String[] args) {

        Student s = new Student();

        s.setName("Rahul");
        s.setAge(22);

        System.out.println(s.getName());
        System.out.println(s.getAge());
    }
}
```

### Output

```
Rahul
22
```

---

# Data Validation

One major advantage of encapsulation is validation.

```java
class Student {

    private int age;

    public void setAge(int age) {

        if (age > 0) {
            this.age = age;
        }
    }

    public int getAge() {

        return age;
    }
}
```

Now negative values are rejected.

---

# Real-World Example

### Bank Account

```java
class BankAccount {

    private double balance;

    public void deposit(double amount) {

        if (amount > 0) {
            balance += amount;
        }
    }

    public double getBalance() {

        return balance;
    }
}
```

Users cannot directly change the balance.

---

# Encapsulation Flow

```
        User

          │

          ▼

Getter / Setter Methods

          │

          ▼

Private Variables
```

The user interacts only through methods.

---

# Advantages of Encapsulation

- Data hiding
- Better security
- Easier maintenance
- Controlled data access
- Data validation
- Improved code flexibility

---

# Encapsulation vs Data Hiding

| Encapsulation | Data Hiding |
|---------------|-------------|
| Wraps data and methods together | Restricts direct access to data |
| Achieved using classes | Achieved using access modifiers |
| Improves design | Improves security |

---

# Common Mistakes

### Public Variables

```java
public String name;
```

Anyone can modify the value.

Prefer:

```java
private String name;
```

---

### Missing Validation

```java
public void setAge(int age) {

    this.age = age;
}
```

Better:

```java
public void setAge(int age) {

    if (age >= 0) {
        this.age = age;
    }
}
```

---

### Getter Without Need

Not every variable requires both getter and setter.

Example:

```java
private final String accountNumber;
```

Only a getter may be required.

---

# Best Practices

- Keep variables private.
- Validate data in setter methods.
- Expose only required methods.
- Avoid unnecessary setters for read-only fields.
- Keep business logic inside the class.

---

# Summary

In this chapter, you learned:

- What encapsulation is
- Why encapsulation is important
- Getter and setter methods
- Data validation
- Encapsulation vs data hiding
- Real-world implementation

---

# Quick Revision

- Encapsulation = Data + Methods together.
- Private variables cannot be accessed directly.
- Getters read data.
- Setters update data.
- Validation should be done inside setters.
- Encapsulation improves security and maintainability.

---

# Practice Questions

### Basic

1. What is encapsulation?
2. Why are variables kept private?
3. What is a getter?
4. What is a setter?
5. Why do we use getter and setter methods?

### Intermediate

6. Explain data hiding.
7. How does encapsulation improve security?
8. Why should validation be performed inside setters?

### Interview Questions

1. What is the difference between encapsulation and abstraction?
2. Can encapsulation exist without getters and setters?
3. Why shouldn't variables be public?
4. What are the benefits of encapsulation in enterprise applications?
5. How is encapsulation implemented in JavaBeans?

---

# Hands-on Exercise

Create a class named **Employee** with the following private variables:

- id
- name
- salary

Requirements:

1. Create getter and setter methods for each variable.
2. Validate that salary cannot be negative.
3. Create two Employee objects.
4. Set values using setters.
5. Display the values using getters.
