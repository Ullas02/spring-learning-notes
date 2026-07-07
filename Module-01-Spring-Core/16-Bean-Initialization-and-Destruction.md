# Bean Initialization and Destruction

## 🎯 What is it?

Spring allows a Bean to execute custom code:

- Immediately after it has been created and all dependencies have been injected.
- Just before it is destroyed.

These lifecycle callback methods are commonly used for resource initialization and cleanup.

---

## ❓ Why do we need it?

Some resources require setup before they can be used and cleanup before the application shuts down.

Examples:

- Opening database connections
- Loading configuration files
- Initializing caches
- Closing files
- Disconnecting from external services

---

## ⚙️ How does it work?

Spring follows this sequence:

1. Create the Bean.
2. Inject dependencies.
3. Execute the initialization callback (`@PostConstruct`).
4. Use the Bean.
5. Execute the destruction callback (`@PreDestroy`) when the application shuts down.

---

## 💻 Example

```java
@Component
public class DatabaseManager {

    @PostConstruct
    public void initialize() {
        System.out.println("Connecting to database...");
    }

    @PreDestroy
    public void cleanup() {
        System.out.println("Closing database connection...");
    }
}
```

---

## ✅ Benefits

- Automatic setup and cleanup.
- Cleaner code.
- Better resource management.
- Reduced memory and resource leaks.

---

## ⚡ Backend Engineer Tips

Keep lifecycle methods focused on infrastructure tasks.

Avoid placing business logic inside them.

---

## ❌ Common Mistakes

- Forgetting to release resources.
- Performing long-running operations during initialization.
- Assuming `@PreDestroy` is called for prototype-scoped Beans.

---

## 📝 Quick Revision

- `@PostConstruct` runs after dependency injection.
- `@PreDestroy` runs before Spring destroys a managed singleton Bean.
- Use lifecycle callbacks for initialization and cleanup.
