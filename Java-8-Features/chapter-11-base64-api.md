# Chapter 11: Base64 API

## 📖 Overview

The **Base64 API** was introduced in **Java 8** to easily encode and decode binary data into text. It is part of the `java.util.Base64` package and is commonly used in web applications, REST APIs, email attachments, and authentication.

Base64 converts binary data into ASCII characters, making it safe to transmit over text-based protocols such as HTTP and SMTP.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Base64 encoding
- Encode and decode data
- Use different Base64 encoders
- Work with URL-safe Base64
- Apply Base64 in real-world applications

---

# What is Base64?

Base64 is an encoding scheme that converts binary data into readable text.

Example:

Original Text

```
Java
```

Encoded

```
SmF2YQ==
```

Decoded

```
Java
```

---

# Base64 Package

```java
import java.util.Base64;
```

The API provides three types of encoders:

| Encoder | Purpose |
|----------|---------|
| Basic | Standard Base64 encoding |
| URL | URL-safe encoding |
| MIME | Email and MIME encoding |

---

# Basic Encoding

```java
import java.util.Base64;

String text = "Hello Java";

String encoded =
    Base64.getEncoder()
          .encodeToString(text.getBytes());

System.out.println(encoded);
```

Example Output

```
SGVsbG8gSmF2YQ==
```

---

# Basic Decoding

```java
String encoded =
    "SGVsbG8gSmF2YQ==";

String decoded =
    new String(
        Base64.getDecoder()
              .decode(encoded)
    );

System.out.println(decoded);
```

Output

```
Hello Java
```

---

# URL Encoder

Used when encoded data is part of a URL.

```java
String encoded =
    Base64.getUrlEncoder()
          .encodeToString(
              "Java 8".getBytes()
          );

System.out.println(encoded);
```

URL encoding avoids characters such as `+` and `/`.

---

# URL Decoder

```java
String decoded =
    new String(
        Base64.getUrlDecoder()
              .decode(encoded)
    );
```

---

# MIME Encoder

Used for encoding email attachments or large text.

```java
String encoded =
    Base64.getMimeEncoder()
          .encodeToString(
              text.getBytes()
          );
```

---

# Encoding Binary Data

```java
byte[] data = {10, 20, 30, 40};

String encoded =
    Base64.getEncoder()
          .encodeToString(data);

System.out.println(encoded);
```

---

# Decoding Binary Data

```java
byte[] decoded =
    Base64.getDecoder()
          .decode(encoded);

System.out.println(decoded.length);
```

---

# Base64 Workflow

```
Original Data
      │
      ▼
Base64 Encoder
      │
      ▼
Encoded Text
      │
      ▼
Base64 Decoder
      │
      ▼
Original Data
```

---

# Common Base64 Methods

| Method | Purpose |
|---------|---------|
| `getEncoder()` | Standard encoder |
| `getDecoder()` | Standard decoder |
| `getUrlEncoder()` | URL-safe encoder |
| `getUrlDecoder()` | URL-safe decoder |
| `getMimeEncoder()` | MIME encoder |
| `getMimeDecoder()` | MIME decoder |
| `encodeToString()` | Encode to String |
| `decode()` | Decode Base64 data |

---

# Real-World Applications

Base64 is commonly used in:

- JWT (JSON Web Tokens)
- Basic Authentication
- REST APIs
- Email attachments
- Image encoding
- File upload/download
- XML and JSON data exchange

---

# Common Mistakes

### Base64 Is Not Encryption

Incorrect assumption:

```
Base64 = Secure
```

Base64 only **encodes** data.

Anyone can decode it easily.

---

### Decoding Invalid Data

```java
Base64.getDecoder()
      .decode("Invalid@@");
```

This throws:

```
IllegalArgumentException
```

---

### Forgetting Character Encoding

Prefer:

```java
text.getBytes(StandardCharsets.UTF_8);
```

instead of relying on the platform's default charset.

---

# Best Practices

- Use UTF-8 when converting strings to bytes.
- Use URL Encoder for URLs and tokens.
- Use MIME Encoder for email content.
- Never use Base64 as a security mechanism.
- Validate Base64 input before decoding.

---

# Summary

In this chapter, you learned:

- Base64 API
- Encoding and decoding
- URL-safe encoding
- MIME encoding
- Binary data encoding
- Best practices

---

# Quick Revision

- Base64 converts binary data into text.
- `getEncoder()` performs standard encoding.
- `getDecoder()` decodes Base64 data.
- URL Encoder is used for URLs.
- MIME Encoder is used for email content.
- Base64 is encoding, **not encryption**.

---

# Practice Questions

### Basic

1. What is Base64?
2. Which package contains the Base64 API?
3. How do you encode a string?
4. How do you decode Base64 data?
5. What is URL-safe Base64?

### Intermediate

6. Differentiate Basic, URL, and MIME encoders.
7. Why is Base64 commonly used in REST APIs?
8. Why should UTF-8 be preferred during encoding?

### Interview Questions

1. What is the purpose of the Base64 API?
2. Is Base64 an encryption technique? Explain.
3. Explain the different types of Base64 encoders.
4. Where is Base64 used in enterprise applications?
5. What exceptions can occur during Base64 decoding?

---

# Hands-on Exercise

Create a **Secure File Encoder** application that:

1. Read a text string from the user.
2. Encode the text using the Base64 Basic Encoder.
3. Decode the encoded text back to its original form.
4. Generate a URL-safe Base64 string.
5. Encode and decode a byte array.
6. Handle invalid Base64 input using exception handling.
7. Display all encoded and decoded results in a readable format.
8. Compare Base64 encoding with encryption and explain the difference.
