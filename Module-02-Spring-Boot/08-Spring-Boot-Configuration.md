# Spring Boot Configuration

## 🎯 What is it?

Spring Boot allows application behavior to be controlled through external configuration instead of hardcoded values.

Configuration can be written using either:

- application.properties
- application.yml

Both formats contain the same information—the difference is only the syntax.

---

## ❓ Why do we need it?

Imagine deploying the same application to:

- Local laptop
- QA server
- Staging server
- Production

Each environment needs different:

- Database URLs
- Ports
- Logging levels
- API keys

Changing Java code for each environment would be error-prone and difficult to maintain.

External configuration solves this problem.

---

## ⚙️ application.properties

Example:

```properties
spring.application.name=learning-demo
server.port=8081
logging.level.root=INFO
```

Simple key-value format.

---

## ⚙️ application.yml

The same configuration in YAML:

```yaml
spring:
  application:
    name: learning-demo

server:
  port: 8081

logging:
  level:
    root: INFO
```

YAML uses indentation to represent hierarchy.

---

## ⚙️ Which One Should You Choose?

### application.properties

Pros:

- Easy for beginners.
- Explicit.
- Familiar key-value syntax.

Cons:

- Long nested keys become repetitive.

---

### application.yml

Pros:

- Cleaner for complex configurations.
- Easier to organize nested properties.

Cons:

- Indentation is significant.
- Incorrect spacing can cause configuration errors.

Neither is "better." Teams usually standardize on one format for consistency.

---

## ⚙️ Property Loading (High-Level)

When Spring Boot starts, it loads configuration before creating most of the application context.

At a high level:

```
Application Starts
        ↓
Read Configuration
        ↓
Apply Properties
        ↓
Create Beans
        ↓
Start Server
```

We'll revisit configuration precedence in more detail when discussing external configuration sources.

---

## 🌍 Real-World Example

A company might use:

Development:

```properties
server.port=8081
logging.level.root=DEBUG
```

Production:

```properties
server.port=80
logging.level.root=WARN
```

The application code remains unchanged; only the configuration differs.

---

## ✅ Benefits

- Environment-specific behavior.
- Cleaner code.
- Easier deployments.
- Improved maintainability.
- Better separation of concerns.

---

## ⚡ Backend Engineer Tips

Avoid hardcoding values that vary between environments.

Examples:

- Database URLs
- Ports
- API endpoints
- Credentials

These belong in configuration, not Java code.

---

## ❌ Common Mistakes

- Mixing `.properties` and `.yml` without understanding precedence.
- Incorrect YAML indentation.
- Storing secrets directly in version control.
- Hardcoding configuration values in source code.

---

## 📝 Quick Revision

- Spring Boot supports `.properties` and `.yml`.
- Both formats configure the same application.
- Configuration should be externalized.
- Different environments use different configurations.
