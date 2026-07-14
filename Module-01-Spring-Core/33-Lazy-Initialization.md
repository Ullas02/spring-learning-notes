# Lazy Initialization

## 🎯 What is Lazy Initialization?

By default, Spring creates singleton Beans when the Application Context starts. This is called **Eager Initialization**.

With **Lazy Initialization**, Spring delays creating a Bean until it is actually requested for the first time.

---

## ❓ Why do we need it?

Some Beans are:

- Expensive to create
- Rarely used
- Needed only in specific scenarios

Creating them during application startup wastes time and memory.

Lazy initialization creates these Beans only when required.

---

## ⚙️ Default (Eager) vs Lazy

### Eager Initialization (Default)

```
Application Starts
        │
        ▼
Spring Creates Bean
        │
        ▼
Application Ready
```

### Lazy Initialization

```
Application Starts
        │
        ▼
Bean NOT Created
        │
        ▼
First getBean() Call
        │
        ▼
Spring Creates Bean
```

---

## 💻 Example

```java
import org.springframework.context.annotation.Lazy;
import org.springframework.stereotype.Service;

@Service
@Lazy
public class ReportService {

    public ReportService() {
        System.out.println("ReportService created.");
    }
}
```

---

## ✅ Benefits

- Faster application startup
- Reduced memory usage
- Delays creation of expensive objects
- Useful for optional features

---

## ⚡ Backend Engineer Tips

Use lazy initialization only when there is a clear benefit.

Most service and repository Beans should remain eagerly initialized.

---

## ❌ Common Mistakes

- Using `@Lazy` everywhere.
- Assuming lazy Beans improve every application.
- Forgetting that the first access will be slower.

---

## 📝 Quick Revision

- Spring creates singleton Beans eagerly by default.
- `@Lazy` delays Bean creation until first use.
- Use it for expensive or infrequently used Beans.
