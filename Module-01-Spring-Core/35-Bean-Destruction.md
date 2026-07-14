# Bean Destruction

## 🎯 What is Bean Destruction?

Bean Destruction is the final phase of a Spring Bean's lifecycle.

When the Spring IoC Container is shutting down, it gives managed Beans an opportunity to release resources before removing them from memory.

---

## ❓ Why do we need Bean Destruction?

Many resources should not simply disappear when the application stops.

Examples include:

- Database connection pools
- Network sockets
- File streams
- Thread pools
- Cache connections
- Message broker connections

Proper cleanup prevents resource leaks and ensures a graceful application shutdown.

---

## ⚙️ Destruction Order

```
Application Running
        │
        ▼
Shutdown Begins
        │
        ▼
Destruction Callback
        │
        ▼
Resources Released
        │
        ▼
Bean Removed
```

---

## 💻 Example

```java
@Service
public class FileService {

    public void closeResources() {
        System.out.println("Closing file resources...");
    }
}
```

When destruction callbacks are configured, Spring executes cleanup logic before removing the Bean.

---

## ✅ Benefits

- Prevents resource leaks.
- Supports graceful shutdown.
- Closes external connections safely.
- Improves application stability.

---

## ⚡ Backend Engineer Tips

If a Bean opens resources during initialization, it should also release them during destruction.

Think of initialization and destruction as complementary phases.

---

## ❌ Common Mistakes

- Forgetting to close database connections.
- Leaving background threads running.
- Assuming the JVM automatically cleans up every resource correctly.

---

## 📝 Quick Revision

- Destruction occurs during application shutdown.
- Spring provides lifecycle callbacks for cleanup.
- Always release resources that your Bean owns.
