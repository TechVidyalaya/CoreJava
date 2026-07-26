# Chapter 13: The Object Class

## 📖 Overview

Every class in Java directly or indirectly inherits from the **Object** class. It is the root of the Java class hierarchy and provides several useful methods that every Java object automatically inherits.

Understanding the `Object` class is important because many Java frameworks, collections, and APIs rely on these methods.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the Object class
- Use common Object class methods
- Override `toString()`
- Override `equals()`
- Understand `hashCode()`
- Know when to override Object methods

---

# What is the Object Class?

The `Object` class is the superclass of all Java classes.

Example:

```java
class Student {

}
```

Internally, Java treats it as:

```java
class Student extends Object {

}
```

Every class automatically inherits Object unless another class is extended.

---

# Why is Object Important?

The Object class provides common functionality for every object.

Examples include:

- Printing objects
- Comparing objects
- Generating hash codes
- Cloning objects
- Synchronisation support

---

# Common Methods of Object Class

| Method | Purpose |
|---------|---------|
| `toString()` | Returns string representation |
| `equals()` | Compares objects |
| `hashCode()` | Returns hash value |
| `getClass()` | Returns runtime class |
| `clone()` | Creates object copy |
| `wait()` | Waits for another thread |
| `notify()` | Wakes one waiting thread |
| `notifyAll()` | Wakes all waiting threads |

---

# The `toString()` Method

By default:

```java
class Student {

}
```

```java
Student s = new Student();

System.out.println(s);
```

### Output

```
Student@15db9742
```

This output is usually not useful.

---

# Overriding `toString()`

```java
class Student {

    String name;
    int age;

    Student(String name, int age) {

        this.name = name;
        this.age = age;
    }

    @Override
    public String toString() {

        return name + " - " + age;
    }
}
```

```java
Student s = new Student("Rahul", 22);

System.out.println(s);
```

### Output

```
Rahul - 22
```

---

# The `equals()` Method

Default behaviour compares object references.

```java
Student s1 = new Student("Rahul", 22);
Student s2 = new Student("Rahul", 22);

System.out.println(s1.equals(s2));
```

### Output

```
false
```

Both objects have different memory addresses.

---

# Overriding `equals()`

```java
class Student {

    String name;

    Student(String name) {
        this.name = name;
    }

    @Override
    public boolean equals(Object obj) {

        Student other = (Student) obj;

        return this.name.equals(other.name);
    }
}
```

Now:

```java
Student s1 = new Student("Rahul");
Student s2 = new Student("Rahul");

System.out.println(s1.equals(s2));
```

### Output

```
true
```

---

# The `hashCode()` Method

Every object has a hash code.

```java
Student s = new Student();

System.out.println(s.hashCode());
```

Example Output

```
356573597
```

Hash codes are mainly used by:

- HashMap
- HashSet
- Hashtable

---

# Relationship Between `equals()` and `hashCode()`

Rule:

If two objects are equal using `equals()`, they **must** return the same hash code.

Therefore, whenever you override `equals()`, you should also override `hashCode()`.

---

# Overriding `hashCode()`

```java
import java.util.Objects;

class Student {

    String name;

    Student(String name) {
        this.name = name;
    }

    @Override
    public int hashCode() {

        return Objects.hash(name);
    }
}
```

---

# The `getClass()` Method

Returns runtime class information.

```java
Student s = new Student();

System.out.println(s.getClass().getName());
```

### Output

```
Student
```

---

# The `clone()` Method

Used to create a copy of an object.

```java
class Student implements Cloneable {

}
```

The object must implement the `Cloneable` interface.

> In modern Java, copy constructors or factory methods are generally preferred over `clone()`.

---

# Real-World Example

Suppose two employees have the same employee ID.

```java
Employee e1 = new Employee(101);
Employee e2 = new Employee(101);
```

Overriding `equals()` allows comparing employee IDs instead of memory addresses.

---

# Common Mistakes

### Using `==` Instead of `equals()`

```java
String s1 = new String("Java");
String s2 = new String("Java");

System.out.println(s1 == s2);
```

Output

```
false
```

Correct:

```java
System.out.println(s1.equals(s2));
```

Output

```
true
```

---

### Overriding `equals()` Without `hashCode()`

This can cause incorrect behaviour in collections like `HashMap` and `HashSet`.

Always override both together.

---

### Not Checking Object Type

Incorrect:

```java
Student other = (Student) obj;
```

Better:

```java
if (!(obj instanceof Student)) {
    return false;
}
```

---

# Best Practices

- Override `toString()` for readable output.
- Override `equals()` for logical comparison.
- Always override `hashCode()` with `equals()`.
- Use `Objects.equals()` and `Objects.hash()` where appropriate.
- Avoid using `clone()` unless necessary.

---

# Summary

In this chapter, you learned:

- Object class hierarchy
- Common Object methods
- `toString()`
- `equals()`
- `hashCode()`
- `getClass()`
- `clone()`
- Best practices

---

# Quick Revision

- Every Java class extends `Object`.
- `toString()` returns a string representation.
- `equals()` compares object equality.
- `hashCode()` supports hash-based collections.
- Override `equals()` and `hashCode()` together.
- `getClass()` returns runtime type information.

---

# Practice Questions

### Basic

1. What is the Object class?
2. Which class is the parent of all Java classes?
3. What is the purpose of `toString()`?
4. What is the purpose of `equals()`?
5. What does `getClass()` return?

### Intermediate

6. Why should `equals()` and `hashCode()` be overridden together?
7. Explain the difference between `==` and `equals()`.
8. Why is `toString()` commonly overridden?

### Interview Questions

1. Is Object the superclass of every Java class?
2. What happens if `equals()` is overridden but `hashCode()` is not?
3. Why is `clone()` less preferred in modern Java?
4. What is the default implementation of `toString()`?
5. Which Java collections rely heavily on `hashCode()`?

---

# Hands-on Exercise

Create a class named **Employee** with:

Variables:

- id
- name

Requirements:

1. Override `toString()` to display employee details.
2. Override `equals()` to compare employees by `id`.
3. Override `hashCode()` accordingly.
4. Create two Employee objects with the same `id`.
5. Compare them using `equals()` and print their hash codes.
