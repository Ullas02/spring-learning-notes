# Logging in Spring Boot

## 🎯 What is Logging?

Logging is the process of recording information about what your application is doing while it is running.

Instead of printing messages to the console using `System.out.println()`, Spring Boot provides a structured logging framework.

Logging helps developers:

- Debug problems
- Monitor application behavior
- Track errors
- Understand application flow

---

## ❓ Why do we need Logging?

Imagine an e-commerce application.

A customer reports:

> "I clicked 'Place Order' but nothing happened."

Without logs:

- You have no idea what occurred.

With logs:

```
INFO  Order request received
INFO  Validating payment
ERROR Payment gateway timeout
```

You immediately know where the request failed.

Logging is one of the most valuable tools for diagnosing issues in production.

---

## ⚙️ Spring Boot's Default Logging

Spring Boot uses **SLF4J** as the logging API and **Logback** as the default logging implementation.

This combination is included automatically when you use starters such as:

```xml
spring-boot-starter-web
```

No additional configuration is required to start logging.

---

## ⚙️ Log Levels

Spring Boot supports several log levels.

| Level | Purpose |
|--------|---------|
| TRACE | Very detailed information for deep debugging |
| DEBUG | Helpful information while developing |
| INFO | Normal application events |
| WARN | Something unexpected happened, but the application can continue |
| ERROR | A serious problem occurred |

---

## 💻 Example

```java
package com.example.demo.controller;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.web.bind.annotation.*;

@RestController
public class HelloController {

    private static final Logger logger =
            LoggerFactory.getLogger(HelloController.class);

    @GetMapping("/hello")
    public String hello() {

        logger.info("Request received for /hello endpoint");

        return "Hello Spring Boot!";
    }

}
```

Whenever someone visits `/hello`, an INFO log is written.

---

## ⚙️ Configuring Log Levels

In `application.properties`:

```properties
logging.level.root=INFO
```

Or for a specific package:

```properties
logging.level.com.example.demo=DEBUG
```

This allows you to increase or reduce logging without changing Java code.

---

## 🌍 Real-World Example

During development:

```properties
logging.level.com.example.demo=DEBUG
```

In production:

```properties
logging.level.com.example.demo=INFO
```

This keeps production logs concise while still recording important events.

---

## ✅ Benefits

- Easier debugging
- Better monitoring
- Production diagnostics
- Cleaner than `System.out.println()`
- Configurable without code changes

---

## ⚡ Backend Engineer Tips

Never use `System.out.println()` for application logging.

Professional applications rely on logging frameworks because they support:

- Log levels
- Formatting
- File logging
- External log aggregation

---

## ❌ Common Mistakes

- Leaving excessive DEBUG logs in production.
- Logging sensitive information such as passwords or tokens.
- Using ERROR for normal events.
- Replacing proper logging with `System.out.println()`.

---

## 📝 Quick Revision

- Logging records application events.
- Spring Boot uses SLF4J + Logback by default.
- Choose the appropriate log level.
- Configure logging through `application.properties`.
