# Chapter 10: Nashorn JavaScript Engine

## 📖 Overview

The **Nashorn JavaScript Engine** was introduced in **Java 8** to allow Java applications to execute JavaScript code. It replaced the older Rhino engine and enabled seamless integration between Java and JavaScript.

> **Note:** Nashorn was **deprecated in Java 11** and **removed in Java 15**. It is included here because it is a Java 8 feature and may still appear in legacy applications and interviews.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the Nashorn JavaScript Engine
- Execute JavaScript from Java
- Pass data between Java and JavaScript
- Call Java methods from JavaScript
- Understand Nashorn limitations

---

# What is Nashorn?

Nashorn is a **JavaScript engine** built into Java 8.

It allows Java programs to:

- Execute JavaScript code
- Evaluate scripts at runtime
- Exchange data between Java and JavaScript
- Extend applications with scripting support

---

# Required Classes

```java
import javax.script.ScriptEngine;
import javax.script.ScriptEngineManager;
```

---

# Creating a Script Engine

```java
ScriptEngineManager manager =
    new ScriptEngineManager();

ScriptEngine engine =
    manager.getEngineByName("nashorn");
```

---

# Executing JavaScript Code

```java
engine.eval(
    "print('Hello from JavaScript');"
);
```

Output

```
Hello from JavaScript
```

---

# Evaluating Expressions

```java
Object result =
    engine.eval("10 + 20");

System.out.println(result);
```

Output

```
30
```

---

# Storing Variables

```java
engine.eval(
    "var name = 'Java';"
);

Object value =
    engine.eval("name");

System.out.println(value);
```

Output

```
Java
```

---

# Passing Data from Java to JavaScript

```java
engine.put("number", 100);

Object result =
    engine.eval("number + 50");

System.out.println(result);
```

Output

```
150
```

---

# Reading Data from JavaScript

```java
engine.eval(
    "var language = 'Java 8';"
);

String value =
    (String) engine.get("language");

System.out.println(value);
```

Output

```
Java 8
```

---

# Calling Java Classes

JavaScript can access Java classes.

```java
engine.eval(
    "var date = Java.type('java.time.LocalDate');" +
    "print(date.now());"
);
```

Example Output

```
2026-07-27
```

---

# Executing Functions

```java
engine.eval(
    "function square(x) { return x * x; }"
);

Object result =
    engine.eval("square(6)");

System.out.println(result);
```

Output

```
36
```

---

# Running a Script File

```java
FileReader reader =
    new FileReader("script.js");

engine.eval(reader);
```

Example `script.js`

```javascript
print("Welcome to Nashorn");
```

---

# Common ScriptEngine Methods

| Method | Purpose |
|---------|---------|
| `getEngineByName()` | Get scripting engine |
| `eval()` | Execute script |
| `put()` | Pass Java variable |
| `get()` | Retrieve variable |
| `getBindings()` | Access script variables |

---

# Nashorn Workflow

```
Java Program
      │
      ▼
ScriptEngine
      │
      ▼
JavaScript Code
      │
      ▼
Result Returned
```

---

# Real-World Applications

Nashorn was used for:

- Rule engines
- Dynamic configuration
- Script-based automation
- Template processing
- Lightweight plugins
- Legacy enterprise applications

---

# Limitations

- Deprecated in Java 11
- Removed in Java 15
- No longer actively maintained
- Modern projects prefer:
  - GraalVM JavaScript
  - Node.js
  - Other scripting engines

---

# Common Mistakes

### Forgetting Exception Handling

`eval()` throws `ScriptException`.

```java
try {

    engine.eval("10 +");

} catch (ScriptException e) {

    e.printStackTrace();
}
```

---

### Engine Not Available

```java
ScriptEngine engine =
    manager.getEngineByName("nashorn");
```

In Java 15+, this returns `null` because Nashorn has been removed.

---

### Using Nashorn in New Projects

Avoid Nashorn for new applications. Use **GraalVM JavaScript** if JavaScript integration is required.

---

# Best Practices

- Use Nashorn only for maintaining legacy Java 8 applications.
- Always handle `ScriptException`.
- Validate scripts before execution.
- Avoid executing untrusted scripts.
- Consider GraalVM for modern Java applications.

---

# Summary

In this chapter, you learned:

- Nashorn JavaScript Engine
- Creating a ScriptEngine
- Executing JavaScript
- Passing data between Java and JavaScript
- Running script files
- Nashorn limitations

---

# Quick Revision

- Nashorn is Java 8's built-in JavaScript engine.
- `ScriptEngineManager` creates a scripting engine.
- `eval()` executes JavaScript code.
- `put()` passes Java variables to JavaScript.
- `get()` retrieves JavaScript variables.
- Nashorn is deprecated in Java 11 and removed in Java 15.

---

# Practice Questions

### Basic

1. What is Nashorn?
2. Which package contains `ScriptEngine`?
3. Which method executes JavaScript code?
4. How do you pass a Java variable to JavaScript?
5. Why was Nashorn removed?

### Intermediate

6. Explain the Nashorn execution workflow.
7. How can JavaScript access Java classes?
8. What are the limitations of Nashorn?

### Interview Questions

1. What is the Nashorn JavaScript Engine?
2. How do you execute JavaScript from Java?
3. Explain the use of `ScriptEngineManager`.
4. Why was Nashorn deprecated and removed?
5. What alternatives are available for JavaScript execution in modern Java?

---

# Hands-on Exercise

Create a **Script Executor** application that:

1. Create a `ScriptEngine` using Nashorn.
2. Execute a simple JavaScript expression.
3. Pass a Java variable to JavaScript using `put()`.
4. Retrieve a JavaScript variable using `get()`.
5. Create and execute a JavaScript function.
6. Execute a JavaScript file (`script.js`).
7. Handle `ScriptException` properly.
8. Research how the same functionality can be implemented using **GraalVM JavaScript**.
