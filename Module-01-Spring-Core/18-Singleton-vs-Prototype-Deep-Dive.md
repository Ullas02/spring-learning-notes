# Singleton vs Prototype – Deep Dive

## 🎯 What is it?

Singleton and Prototype are two Bean scopes that determine how Spring creates and manages Bean instances.

Choosing the correct scope affects:

- Memory usage
- Performance
- Thread safety
- Application design

---

## ❓ Why is Singleton the default?

Most Spring Beans are **stateless**.

Stateless Beans:

- Don't store user-specific data.
- Can safely be shared.
- Consume less memory.
- Improve application startup performance.

For these reasons, Spring uses Singleton as the default scope.

---

## ⚙️ Singleton vs Prototype

| Feature | Singleton | Prototype |
|---------|-----------|-----------|
| Number of instances | One | New instance per request |
| Managed by Spring | Entire lifecycle | Creation only |
| Memory usage | Low | Higher |
| Performance | Better | More object creation |
| Default scope | ✅ | ❌ |

---

## 💻 Example

```java
@Component
public class UserService {

}
```

This is automatically a singleton Bean.

```java
@Component
@Scope("prototype")
public class ReportGenerator {

}
```

Each lookup creates a new object.

---

## ✅ Benefits

### Singleton

- Less memory usage
- Better performance
- Shared across the application

### Prototype

- Independent objects
- Suitable for temporary state
- No shared mutable data

---

## ⚡ Backend Engineer Tips

Use Singleton unless the Bean genuinely needs its own state for each use.

---

## ❌ Common Mistakes

- Storing request-specific data in singleton Beans.
- Using prototype scope to solve thread-safety issues without understanding the root cause.
- Expecting Spring to automatically destroy prototype Beans.

---

## 📝 Quick Revision

- Singleton is the default.
- Prototype creates a new Bean each time.
- Singleton Beans should generally be stateless.
