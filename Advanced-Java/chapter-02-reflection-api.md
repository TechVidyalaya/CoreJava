# Chapter 02: Reflection API

## 📖 Overview

The **Reflection API** allows a Java program to inspect and manipulate classes, methods, fields, constructors, and objects at runtime. It is one of the most powerful features of Java and is widely used by frameworks such as **Spring**, **Hibernate**, **JUnit**, and **Jackson**.

Reflection enables applications to work dynamically without knowing class details during compilation.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Reflection API
- Inspect classes at runtime
- Access methods and fields dynamically
- Create objects using Reflection
- Invoke methods dynamically
- Learn Reflection best practices

---

# What is Reflection?

Reflection is the ability of a Java program to examine and modify its own structure during runtime.

Using Reflection, you can:

- Inspect classes
- Read class metadata
- Access private members
- Invoke methods
- Create objects dynamically

---

# Reflection Package

```java
import java.lang.reflect.*;
```

The Reflection API is mainly available in:

```text
java.lang.reflect
```

---

# Getting Class Information

There are three common ways to obtain a `Class` object.

Using `.class`

```java
Class<Employee> cls =
    Employee.class;
```

Using `getClass()`

```java
Employee emp = new Employee();

Class<?> cls =
    emp.getClass();
```

Using `Class.forName()`

```java
Class<?> cls =
    Class.forName("Employee");
```

---

# Reading Class Details

```java
Class<?> cls =
    Employee.class;

System.out.println(
    cls.getName()
);

System.out.println(
    cls.getSimpleName()
);
```

Example Output

```
com.demo.Employee

Employee
```

---

# Getting Constructors

```java
Constructor<?>[] constructors =
    cls.getConstructors();

for (Constructor<?> c : constructors) {

    System.out.println(c);
}
```

---

# Creating Objects Dynamically

```java
Constructor<Employee> constructor =
    Employee.class.getConstructor();

Employee employee =
    constructor.newInstance();
```

---

# Getting Methods

```java
Method[] methods =
    cls.getDeclaredMethods();

for (Method method : methods) {

    System.out.println(
        method.getName()
    );
}
```

---

# Invoking Methods

```java
Method method =
    cls.getMethod("display");

method.invoke(employee);
```

Output

```
Employee Details
```

---

# Getting Fields

```java
Field[] fields =
    cls.getDeclaredFields();

for (Field field : fields) {

    System.out.println(
        field.getName()
    );
}
```

---

# Accessing Private Fields

```java
Field field =
    cls.getDeclaredField("name");

field.setAccessible(true);

field.set(employee, "Rahul");

System.out.println(
    field.get(employee)
);
```

Output

```
Rahul
```

---

# Reading Annotations

Reflection is commonly used to process annotations.

```java
if (cls.isAnnotationPresent(Author.class)) {

    Author author =
        cls.getAnnotation(Author.class);

    System.out.println(
        author.name()
    );
}
```

---

# Common Reflection Classes

| Class | Purpose |
|--------|---------|
| `Class` | Represents a class |
| `Method` | Represents a method |
| `Field` | Represents a field |
| `Constructor` | Represents a constructor |
| `Modifier` | Reads access modifiers |

---

# Reflection Workflow

```
Class Object
      │
      ▼
Read Metadata
      │
      ▼
Fields
Methods
Constructors
Annotations
      │
      ▼
Create Object / Invoke Methods
```

---

# Real-World Applications

Reflection is widely used in:

- Spring Framework
- Hibernate ORM
- Dependency Injection
- JSON Serialization
- JUnit Testing
- Plugin Architectures

---

# Advantages

- Dynamic object creation
- Runtime inspection
- Flexible framework development
- Supports dependency injection
- Useful for testing and debugging

---

# Limitations

- Slower than direct method calls
- Breaks encapsulation when accessing private members
- Harder to understand and maintain
- Security restrictions may apply

---

# Common Mistakes

### Forgetting Exception Handling

Reflection methods may throw exceptions such as:

- `ClassNotFoundException`
- `NoSuchMethodException`
- `IllegalAccessException`
- `InvocationTargetException`

Always handle them appropriately.

---

### Accessing Private Members Without Permission

Incorrect:

```java
field.get(employee);
```

Correct:

```java
field.setAccessible(true);
```

---

### Overusing Reflection

Reflection should not replace normal object-oriented programming.

Use it only when runtime flexibility is required.

---

# Best Practices

- Prefer normal method calls whenever possible.
- Use Reflection only when dynamic behaviour is required.
- Cache Reflection metadata if accessed repeatedly.
- Handle Reflection exceptions properly.
- Avoid modifying private members unless necessary.

---

# Summary

In this chapter, you learned:

- Reflection API
- Class objects
- Constructors
- Methods
- Fields
- Dynamic object creation
- Annotation processing
- Best practices

---

# Quick Revision

- Reflection inspects classes at runtime.
- `Class` represents metadata about a class.
- `Method` invokes methods dynamically.
- `Field` accesses object fields.
- `Constructor` creates objects dynamically.
- Reflection is heavily used in Spring and Hibernate.

---

# Practice Questions

### Basic

1. What is Reflection?
2. Which package contains the Reflection API?
3. How do you obtain a `Class` object?
4. What is the purpose of the `Method` class?
5. How can Reflection create an object?

### Intermediate

6. Explain the difference between `getMethods()` and `getDeclaredMethods()`.
7. How can private fields be accessed using Reflection?
8. Why is Reflection slower than normal method calls?

### Interview Questions

1. What is the Reflection API in Java?
2. Where is Reflection used in enterprise applications?
3. Explain how Spring uses Reflection.
4. What are the advantages and disadvantages of Reflection?
5. Why should Reflection be used carefully?

---

# Hands-on Exercise

Create a **Reflection Inspector** application that:

1. Create an `Employee` class with private fields and public methods.
2. Obtain the `Class` object using all three approaches.
3. Display:
   - Class name
   - Constructors
   - Methods
   - Fields
4. Create an object dynamically using Reflection.
5. Invoke a method using `Method.invoke()`.
6. Read and modify a private field using `Field`.
7. Read a custom annotation applied to the class.
8. Print all discovered metadata in a structured format.
