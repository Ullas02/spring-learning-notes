# Bean Scopes

## 🎯 What is Bean Scope?

Bean Scope determines **how many instances of a Bean** Spring creates and how long those instances live within the Spring IoC Container.

In other words, Bean Scope answers:

> "Should Spring create one object or multiple objects?"

---

## ❓ Why do we need Bean Scopes?

Not every object should behave the same way.

Some objects should be shared across the entire application, while others should be newly created whenever they are needed.

Spring provides Bean Scopes to support these different requirements.

---

## ⚙️ Common Bean Scopes

| Scope | Description |
|--------|-------------|
| `singleton` | One shared instance per Spring IoC Container (default). |
| `prototype` | A new instance is created every time the Bean is requested. |

For web applications, Spring also provides scopes such as:

- `request`
- `session`
- `application`
- `websocket`

We'll focus on `singleton` and `prototype` first because they apply to all Spring applications.

---

## 💻 Example

```java
@Service
@Scope("singleton")
public class UserService {

}
```

```java
@Service
@Scope("prototype")
public class ReportGenerator {

}
```

---

## ✅ Benefits

- Controls object creation.
- Optimizes memory usage.
- Supports different application requirements.
- Improves flexibility.

---

## ⚡ Backend Engineer Tips

Most service, repository, and configuration classes should remain `singleton`.

Use `prototype` only when you genuinely need a new object each time.

---

## ❌ Common Mistakes

- Assuming every Bean is recreated on each request.
- Using `prototype` unnecessarily.
- Forgetting that `singleton` is the default scope.

---

## 📝 Quick Revision

- Bean Scope controls how many Bean instances Spring creates.
- `singleton` = one shared object.
- `prototype` = new object each request.
- Default scope is `singleton`.
