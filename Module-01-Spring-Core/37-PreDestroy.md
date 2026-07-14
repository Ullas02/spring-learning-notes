# @PreDestroy

## 🎯 What is @PreDestroy?

`@PreDestroy` is a lifecycle annotation that tells Spring to automatically execute a method **just before a Spring-managed Bean is destroyed**.

It is typically used to release resources that the Bean owns.

---

## ❓ Why do we need it?

Many Beans manage resources that should be cleaned up properly before the application shuts down.

Examples include:

- Closing database connections
- Closing file streams
- Stopping background threads
- Releasing network connections
- Flushing buffered data

`@PreDestroy` allows Spring to perform this cleanup automatically.

---

## ⚙️ Execution Order

```
Application Running
        │
        ▼
Shutdown Begins
        │
        ▼
@PreDestroy Method Executes
        │
        ▼
Bean Destroyed
```

---

## 💻 Example

```java
import jakarta.annotation.PreDestroy;
import org.springframework.stereotype.Service;

@Service
public class CacheService {

    @PreDestroy
    public void cleanup() {
        System.out.println("Releasing cache resources...");
    }
}
```

Spring automatically calls `cleanup()` when the application context is closed.

---

## ✅ Benefits

- Automatic resource cleanup
- Graceful application shutdown
- Prevents resource leaks
- Keeps cleanup logic centralized

---

## ⚡ Backend Engineer Tips

Anything opened during initialization should generally be released during destruction.

Initialization and destruction should complement each other.

---

## ❌ Common Mistakes

- Forgetting to close the application context in standalone Spring applications.
- Performing important cleanup in ordinary methods instead of lifecycle callbacks.
- Assuming `@PreDestroy` executes for objects created using `new`.

---

## 📝 Quick Revision

- `@PreDestroy` runs once.
- Executes before the Bean is destroyed.
- Used for cleanup.
- Spring invokes it automatically.
