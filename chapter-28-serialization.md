# Chapter 28: Serialization

## 📖 Overview

**Serialization** is the process of converting a Java object into a sequence of bytes so that it can be stored in a file, sent over a network, or saved in a database. **Deserialization** is the reverse process of converting the byte stream back into a Java object.

Serialization is commonly used in distributed systems, caching, session management, and object persistence.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Serialization and Deserialization
- Implement the `Serializable` interface
- Serialize and deserialize objects
- Use `transient` fields
- Understand `serialVersionUID`
- Follow serialization best practices

---

# What is Serialization?

Serialization converts an object into a byte stream.

```
Java Object
      │
      ▼
Serialization
      │
      ▼
Byte Stream
      │
      ▼
File / Network / Database
```

---

# What is Deserialization?

Deserialization converts a byte stream back into a Java object.

```
File / Network
      │
      ▼
Byte Stream
      │
      ▼
Deserialization
      │
      ▼
Java Object
```

---

# Serializable Interface

To serialize an object, the class must implement the `Serializable` interface.

```java
import java.io.Serializable;

class Student implements Serializable {

    private int id;
    private String name;

    public Student(int id, String name) {

        this.id = id;
        this.name = name;
    }
}
```

`Serializable` is a **marker interface**, meaning it contains no methods.

---

# Serializing an Object

```java
import java.io.FileOutputStream;
import java.io.ObjectOutputStream;

Student student = new Student(101, "Rahul");

ObjectOutputStream out =
    new ObjectOutputStream(
        new FileOutputStream("student.ser"));

out.writeObject(student);

out.close();
```

The object is stored in `student.ser`.

---

# Deserializing an Object

```java
import java.io.FileInputStream;
import java.io.ObjectInputStream;

ObjectInputStream in =
    new ObjectInputStream(
        new FileInputStream("student.ser"));

Student student = (Student) in.readObject();

System.out.println(student);

in.close();
```

---

# Making Output Readable

Override `toString()`.

```java
@Override
public String toString() {

    return id + " - " + name;
}
```

Output

```
101 - Rahul
```

---

# transient Keyword

The `transient` keyword prevents a field from being serialized.

```java
class Student implements Serializable {

    private String name;

    private transient String password;
}
```

During deserialization:

```java
System.out.println(student.getPassword());
```

Output

```
null
```

---

# serialVersionUID

`serialVersionUID` uniquely identifies the version of a serialized class.

```java
private static final long serialVersionUID = 1L;
```

If the class structure changes without updating the version, deserialization may fail.

---

# Object Streams

| Class | Purpose |
|--------|---------|
| `ObjectOutputStream` | Writes objects |
| `ObjectInputStream` | Reads objects |

---

# Serialization Process

```
Student Object
      │
      ▼
ObjectOutputStream
      │
      ▼
student.ser
```

---

# Deserialization Process

```
student.ser
      │
      ▼
ObjectInputStream
      │
      ▼
Student Object
```

---

# Common Exceptions

| Exception | Cause |
|-----------|-------|
| `NotSerializableException` | Class doesn't implement `Serializable` |
| `InvalidClassException` | Version mismatch |
| `IOException` | File operation failed |
| `ClassNotFoundException` | Class unavailable during deserialization |

---

# Real-World Applications

Serialization is used in:

- Session management
- Object caching
- Network communication
- Distributed systems
- Saving application state
- RMI (Remote Method Invocation)

---

# Common Mistakes

### Forgetting to Implement Serializable

```java
class Student {

}
```

Attempting serialization results in:

```
NotSerializableException
```

---

### Serializing Sensitive Data

```java
private String password;
```

Use:

```java
private transient String password;
```

---

### Missing serialVersionUID

Without explicitly defining it, Java generates one automatically, which may cause compatibility issues after class modifications.

---

# Best Practices

- Always implement `Serializable` when object serialization is required.
- Declare `serialVersionUID`.
- Mark confidential fields as `transient`.
- Close streams or use try-with-resources.
- Avoid serializing unnecessary data.

---

# Summary

In this chapter, you learned:

- Serialization
- Deserialization
- Serializable interface
- Object streams
- transient keyword
- serialVersionUID
- Best practices

---

# Quick Revision

- Serialization converts an object into bytes.
- Deserialization recreates the object.
- `Serializable` is a marker interface.
- `ObjectOutputStream` writes objects.
- `ObjectInputStream` reads objects.
- `transient` excludes fields from serialization.
- `serialVersionUID` manages class version compatibility.

---

# Practice Questions

### Basic

1. What is serialization?
2. What is deserialization?
3. Which interface enables serialization?
4. What is a marker interface?
5. Which class writes objects to a file?

### Intermediate

6. What is the purpose of `transient`?
7. Why is `serialVersionUID` important?
8. Explain the serialization process.

### Interview Questions

1. What is the difference between serialization and deserialization?
2. Why is `Serializable` called a marker interface?
3. What happens if a class doesn't implement `Serializable`?
4. What is `serialVersionUID`?
5. When should the `transient` keyword be used?

---

# Hands-on Exercise

Create a **Student Management** program that:

1. Create a `Student` class implementing `Serializable`.
2. Add fields:
   - id
   - name
   - email
   - password (`transient`)
3. Serialize the object into `student.ser`.
4. Deserialize the object.
5. Display all fields.
6. Verify that the password is **not** restored after deserialization.
