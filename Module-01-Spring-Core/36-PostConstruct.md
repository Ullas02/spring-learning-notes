# @PostConstruct

## 🎯 What is @PostConstruct?

`@PostConstruct` is a lifecycle annotation that tells Spring to automatically execute a method **after**:

1. The Bean has been created.
2. All dependencies have been injected.

It is commonly used to perform initialization tasks before the Bean starts serving requests.

---

## ❓ Why do we need it?

Without `@PostConstruct`, initialization methods must be called manually.

Using `@PostConstruct` ensures every Bean is fully prepared before it is used anywhere in the application.

---

## ⚙️ Execution Order

```
Bean Created
      │
      ▼
Dependencies Injected
      │
      ▼
@PostConstruct Method Executes
      │
      ▼
Bean Ready
```

---

## 💻 Example

```java
import jakarta.annotation.PostConstruct;
import org.springframework.stereotype.Service;

@Service
public class CacheService {

    @PostConstruct
    public void initialize() {
        System.out.println("Loading cache...");
    }
}
```

Spring automatically calls `initialize()`.

No manual method call is required.

---

## ✅ Benefits

- Automatic initialization.
- Cleaner code.
- Centralized startup logic.
- Improves Bean reliability.

---

## ⚡ Backend Engineer Tips

Use `@PostConstruct` for setup tasks only.

Business operations such as processing orders or sending emails should remain in normal service methods.

---

## ❌ Common Mistakes

- Calling `@PostConstruct` methods manually.
- Putting business logic inside `@PostConstruct`.
- Performing extremely slow operations during startup.

---

## 📝 Quick Revision

- `@PostConstruct` runs once.
- Executes after dependency injection.
- Used for initialization.
- Spring invokes it automatically.
