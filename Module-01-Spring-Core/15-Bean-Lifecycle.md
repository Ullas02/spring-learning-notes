# Bean Lifecycle

## 🎯 What is Bean Lifecycle?

The Bean Lifecycle is the sequence of stages a Spring Bean goes through from creation until destruction.

Spring doesn't just create objects—it manages them throughout their entire lifetime.

---

## ❓ Why do we need it?

Many objects require setup and cleanup.

Examples:

- Open a database connection.
- Load configuration.
- Initialize a cache.
- Close files.
- Release network resources.

Spring provides lifecycle callbacks to perform these tasks automatically.

---

## ⚙️ Bean Lifecycle Stages

1. Spring creates the Bean.
2. Spring injects dependencies.
3. Initialization callback executes.
4. Bean is ready for use.
5. Application runs.
6. Destruction callback executes.
7. Bean is removed from memory.

---

## 💻 Example

```java
@Component
public class DatabaseConnection {

    @PostConstruct
    public void init() {
        System.out.println("Connecting to database...");
    }

    @PreDestroy
    public void destroy() {
        System.out.println("Closing database connection...");
    }
}
```

---

## ✅ Benefits

- Automatic resource management.
- Cleaner code.
- Centralized initialization and cleanup.
- Better reliability.

---

## ⚡ Backend Engineer Tips

Use lifecycle callbacks only for initialization and cleanup.

Avoid putting business logic inside them.

---

## ❌ Common Mistakes

- Opening resources but never closing them.
- Writing business logic inside lifecycle methods.
- Assuming every Bean supports destruction callbacks (prototype Beans behave differently).

---

## 📝 Quick Revision

- Bean lifecycle begins with creation.
- Dependencies are injected before initialization.
- `@PostConstruct` runs after dependency injection.
- `@PreDestroy` runs before Bean destruction (for managed singleton Beans).
