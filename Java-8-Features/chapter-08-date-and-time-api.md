# Chapter 08: Date and Time API

## 📖 Overview

The **Date and Time API** introduced in **Java 8** (`java.time` package) replaces the older `Date` and `Calendar` classes. It provides an immutable, thread-safe, and easy-to-use API for handling dates, times, durations, and time zones.

The new API is widely used in enterprise applications for scheduling, logging, reporting, and financial systems.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the Java 8 Date and Time API
- Work with dates and times
- Format and parse dates
- Perform date and time calculations
- Use time zones
- Follow best practices

---

# Why a New Date API?

The old API had several limitations:

- Mutable classes
- Not thread-safe
- Difficult to use
- Confusing methods

Java 8 introduced the `java.time` package to solve these problems.

---

# Main Classes

| Class | Purpose |
|--------|---------|
| `LocalDate` | Date only |
| `LocalTime` | Time only |
| `LocalDateTime` | Date and time |
| `ZonedDateTime` | Date, time, and timezone |
| `Period` | Difference between dates |
| `Duration` | Difference between times |
| `DateTimeFormatter` | Format and parse dates |

---

# LocalDate

Represents only a date.

```java
import java.time.LocalDate;

LocalDate today = LocalDate.now();

System.out.println(today);
```

Output

```
2026-07-27
```

---

# Creating a Date

```java
LocalDate birthday =
    LocalDate.of(1995, 5, 20);

System.out.println(birthday);
```

Output

```
1995-05-20
```

---

# LocalTime

Represents only time.

```java
import java.time.LocalTime;

LocalTime now = LocalTime.now();

System.out.println(now);
```

Example Output

```
10:45:30.123
```

---

# LocalDateTime

Represents both date and time.

```java
import java.time.LocalDateTime;

LocalDateTime current =
    LocalDateTime.now();

System.out.println(current);
```

Example Output

```
2026-07-27T10:45:30
```

---

# Adding and Subtracting

```java
LocalDate today =
    LocalDate.now();

System.out.println(
    today.plusDays(10)
);

System.out.println(
    today.minusMonths(2)
);
```

---

# Comparing Dates

```java
LocalDate date1 =
    LocalDate.of(2026, 1, 1);

LocalDate date2 =
    LocalDate.now();

System.out.println(
    date1.isBefore(date2)
);

System.out.println(
    date1.isAfter(date2)
);

System.out.println(
    date1.isEqual(date2)
);
```

---

# Formatting Dates

```java
import java.time.format.DateTimeFormatter;

LocalDate today =
    LocalDate.now();

DateTimeFormatter formatter =
    DateTimeFormatter.ofPattern("dd-MM-yyyy");

String formatted =
    today.format(formatter);

System.out.println(formatted);
```

Example Output

```
27-07-2026
```

---

# Parsing Dates

```java
String date = "15-08-2026";

DateTimeFormatter formatter =
    DateTimeFormatter.ofPattern("dd-MM-yyyy");

LocalDate parsed =
    LocalDate.parse(date, formatter);

System.out.println(parsed);
```

Output

```
2026-08-15
```

---

# Period

Calculates the difference between two dates.

```java
LocalDate start =
    LocalDate.of(2020, 1, 1);

LocalDate end =
    LocalDate.now();

Period period =
    Period.between(start, end);

System.out.println(period.getYears());
```

---

# Duration

Calculates the difference between two times.

```java
LocalTime start =
    LocalTime.of(9, 0);

LocalTime end =
    LocalTime.of(17, 30);

Duration duration =
    Duration.between(start, end);

System.out.println(
    duration.toHours()
);
```

Output

```
8
```

---

# ZonedDateTime

Represents date and time with a timezone.

```java
import java.time.ZonedDateTime;
import java.time.ZoneId;

ZonedDateTime india =
    ZonedDateTime.now(
        ZoneId.of("Asia/Kolkata")
    );

System.out.println(india);
```

---

# Common Date Methods

| Method | Purpose |
|---------|---------|
| `now()` | Current date/time |
| `of()` | Create a date/time |
| `plusDays()` | Add days |
| `minusDays()` | Subtract days |
| `isBefore()` | Compare dates |
| `isAfter()` | Compare dates |
| `format()` | Format date |
| `parse()` | Convert string to date |

---

# Old API vs New API

| Old API | Java 8 API |
|---------|------------|
| `Date` | `LocalDate` |
| `Calendar` | `LocalDateTime` |
| `SimpleDateFormat` | `DateTimeFormatter` |
| Mutable | Immutable |
| Not thread-safe | Thread-safe |

---

# Real-World Applications

The Date and Time API is used in:

- Banking systems
- Appointment scheduling
- Employee attendance
- Flight booking
- Event management
- Log timestamps

---

# Common Mistakes

### Using Wrong Date Pattern

Incorrect:

```java
DateTimeFormatter.ofPattern("DD-MM-YYYY");
```

Correct:

```java
DateTimeFormatter.ofPattern("dd-MM-yyyy");
```

---

### Using LocalDate for Time

Incorrect:

```java
LocalDate.now();
```

When both date and time are needed.

Use:

```java
LocalDateTime.now();
```

---

### Ignoring Time Zones

For international applications, use:

```java
ZonedDateTime
```

instead of `LocalDateTime`.

---

# Best Practices

- Prefer the `java.time` package over `Date` and `Calendar`.
- Use `LocalDate` for dates only.
- Use `LocalTime` for time only.
- Use `LocalDateTime` for local date and time.
- Use `ZonedDateTime` when working across time zones.
- Use `DateTimeFormatter` for formatting and parsing.

---

# Summary

In this chapter, you learned:

- Java 8 Date and Time API
- LocalDate
- LocalTime
- LocalDateTime
- ZonedDateTime
- Period and Duration
- Date formatting and parsing
- Best practices

---

# Quick Revision

- `LocalDate` stores only the date.
- `LocalTime` stores only the time.
- `LocalDateTime` stores both date and time.
- `DateTimeFormatter` formats and parses dates.
- `Period` calculates differences between dates.
- `Duration` calculates differences between times.
- The Java 8 Date API is immutable and thread-safe.

---

# Practice Questions

### Basic

1. Why was the Java 8 Date and Time API introduced?
2. What is the difference between `LocalDate` and `LocalDateTime`?
3. Which class formats dates?
4. What does `Period` represent?
5. Which class supports time zones?

### Intermediate

6. Explain the difference between `Period` and `Duration`.
7. How do you format and parse dates?
8. Why is the Java 8 Date API thread-safe?

### Interview Questions

1. What are the advantages of the Java 8 Date and Time API?
2. Compare the old Date API with the Java 8 Date API.
3. When should `ZonedDateTime` be used?
4. Explain `DateTimeFormatter` with an example.
5. Why are `LocalDate` and `LocalDateTime` immutable?

---

# Hands-on Exercise

Create an **Event Scheduler** that:

1. Display the current date and time.
2. Create an event scheduled for a specific date and time.
3. Format the event date as `dd-MM-yyyy HH:mm`.
4. Calculate the number of days remaining until the event.
5. Calculate the duration between two times.
6. Display the current date and time for:
   - Asia/Kolkata
   - Europe/London
   - America/New_York
7. Print all results in a readable format.
