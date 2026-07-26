# Chapter 05: The `static` Keyword

## 📖 Overview

The `static` keyword belongs to the **class** rather than an individual object. Static members are shared among all objects of the class.

The `static` keyword is widely used for utility methods, constants, counters, the `main()` method, and memory optimisation.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the `static` keyword
- Create static variables and methods
- Differentiate static and instance members
- Use static blocks
- Understand common use cases of `static`

---

# What is `static`?

A static member belongs to the **class**, not to any object.

There is only **one copy** of a static member, shared by all objects.

---

# Static Variable

A static variable is shared among all objects.

```java
class Student {

    static String college = "TechVidyalaya";

    String name;
}
```

Every Student object will have the same value for `college`.

---

# Example

```java
class Student {

    static String college = "TechVidyalaya";

    String name;

    Student(String name) {
        this.name = name;
    }

    void display() {
        System.out.println(name + " - " + college);
    }
}

public class Main {

    public static void main(String[] args) {

        Student s1 = new Student("Rahul");
        Student s2 = new Student("Amit");

        s1.display();
        s2.display();
    }
}
```

### Output

```
Rahul - TechVidyalaya
Amit - TechVidyalaya
```

---

# Changing Static Variables

Changing a static variable affects all objects.

```java
Student.college = "ABC College";
```

Now every Student object will use the updated value.

---

# Static Method

A static method belongs to the class.

It can be called without creating an object.

```java
class MathUtil {

    static void welcome() {

        System.out.println("Welcome");
    }
}
```

Calling it:

```java
MathUtil.welcome();
```

### Output

```
Welcome
```

---

# Static Method Rules

A static method can directly access:

- Static variables
- Other static methods

A static method **cannot directly access**:

- Instance variables
- Instance methods

Example:

```java
class Test {

    int x = 10;

    static void show() {

        // System.out.println(x); ❌
    }
}
```

---

# Accessing Instance Members

Use an object inside a static method.

```java
class Student {

    String name = "Rahul";

    static void display() {

        Student s = new Student();

        System.out.println(s.name);
    }
}
```

---

# Static Block

A static block executes **once** when the class is loaded.

```java
class Student {

    static {

        System.out.println("Static Block Executed");
    }
}
```

---

# Static Block Execution

```java
class Student {

    static {

        System.out.println("Loading Class");
    }

    Student() {

        System.out.println("Constructor");
    }
}

public class Main {

    public static void main(String[] args) {

        new Student();
        new Student();
    }
}
```

### Output

```
Loading Class
Constructor
Constructor
```

The static block runs only once.

---

# Static Import

Java allows importing static members.

Without static import:

```java
Math.sqrt(25);
```

With static import:

```java
import static java.lang.Math.*;

sqrt(25);
```

---

# Static vs Instance Members

| Static | Instance |
|---------|----------|
| Belongs to class | Belongs to object |
| Single copy | Separate copy per object |
| Loaded once | Created with each object |
| Accessed using class name | Accessed using object |
| Memory efficient | Uses more memory |

---

# Real-World Example

Employee ID generator.

```java
class Employee {

    static int counter = 1001;

    int id;

    Employee() {

        id = counter++;

    }

    void display() {

        System.out.println(id);
    }
}
```

```java
Employee e1 = new Employee();
Employee e2 = new Employee();

e1.display();
e2.display();
```

### Output

```
1001
1002
```

---

# Common Uses of `static`

- `main()` method
- Utility classes
- Constants
- Database configuration
- Counters
- Singleton design pattern

---

# Common Mistakes

### Accessing Instance Variable

```java
static void show() {

    System.out.println(name);
}
```

❌ Compilation Error

---

### Calling Static Method Using Object

```java
Student s = new Student();

s.show();
```

Although valid, prefer:

```java
Student.show();
```

---

### Modifying Constants

```java
static final double PI = 3.14;
```

A `static final` variable cannot be modified.

---

# Best Practices

- Access static members using the class name.
- Use static variables only when data is shared.
- Keep utility methods static.
- Avoid excessive use of static variables as they create global state.
- Use `static final` for constants.

---

# Summary

In this chapter, you learned:

- Static variables
- Static methods
- Static blocks
- Static imports
- Static vs instance members
- Common use cases

---

# Quick Revision

- Static belongs to the class.
- One copy is shared by all objects.
- Static methods can be called without objects.
- Static methods cannot directly access instance members.
- Static blocks execute only once.
- Use the class name to access static members.

---

# Practice Questions

### Basic

1. What is the `static` keyword?
2. What is a static variable?
3. What is a static method?
4. Can a static method access instance variables directly?
5. When does a static block execute?

### Intermediate

6. Differentiate static and instance variables.
7. Why is the `main()` method static?
8. Explain the purpose of a static block.

### Interview Questions

1. Why are static variables memory efficient?
2. Can constructors be static? Why?
3. Can we override static methods?
4. What is static import?
5. When should static variables be avoided?

---

# Hands-on Exercise

Create a class named **Employee** with:

**Variables**

- id
- name
- `static int employeeCount`

Requirements:

1. Increment `employeeCount` whenever an object is created.
2. Create a `display()` method to print employee details.
3. Create three Employee objects.
4. Print the total number of employees using the static variable.
