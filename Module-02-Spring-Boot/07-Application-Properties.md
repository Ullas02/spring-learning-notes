# application.properties

## 🎯 What is it?

`application.properties` is Spring Boot's default configuration file.

It allows you to configure your application **without modifying Java code**.

Spring Boot automatically reads this file during application startup.

---

## ❓ Why do we need it?

Applications behave differently in different environments.

For example:

Development:

- Local database
- Debug logging
- Port 8080

Production:

- Production database
- Info logging
- Port 80 or 443

Instead of changing Java source code, we keep these values in configuration files.

---

## ⚙️ How does it work?

During startup:

1. Spring Boot loads configuration files.
2. Reads key-value pairs.
3. Applies them to the application.

Example:

```properties
server.port=8081
```

Spring Boot configures the embedded server to listen on port **8081**.

---

## 💻 Common Properties

### Change Server Port

```properties
server.port=8081
```

---

### Change Application Name

```properties
spring.application.name=learning-demo
```

---

### Enable Debug Mode

```properties
debug=true
```

---

### Change Context Path

```properties
server.servlet.context-path=/api
```

Now:

```
http://localhost:8081/api/hello
```

instead of:

```
http://localhost:8081/hello
```

---

## 🌍 Real-World Example

Suppose your application connects to a database.

Instead of writing:

```java
String url = "...";
```

you configure:

```properties
spring.datasource.url=...
```

This allows the same application to connect to different databases simply by changing configuration.

---

## ✅ Benefits

- No hardcoded configuration.
- Environment-specific settings.
- Easier deployment.
- Better maintainability.
- Cleaner code.

---

## ⚡ Backend Engineer Tips

Business logic belongs in Java classes.

Configuration belongs in configuration files.

Mixing the two makes applications difficult to maintain.

---

## ❌ Common Mistakes

- Hardcoding ports and URLs.
- Storing secrets directly in source code.
- Forgetting to restart the application after changing configuration.
- Putting business logic into configuration files.

---

## 📝 Quick Revision

- `application.properties` stores configuration.
- Spring Boot loads it automatically.
- Configuration can change without changing Java code.
- Use it for ports, logging, databases, and other environment-specific settings.
