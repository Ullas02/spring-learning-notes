# Bean Scopes

## 🎯 What is Bean Scope?

Bean Scope determines **how many instances** of a Bean Spring creates and how long those instances live.

When you request a Bean from the Spring IoC Container, the configured scope decides whether Spring returns:

- The same object every time.
- A new object each time.
- A request-specific object.
- A session-specific object.

---

## ❓ Why do we need Bean Scopes?

Different objects have different lifecycles.

Examples:

- A database service should usually have one shared instance.
- A temporary report generator may need a new instance for every use.
- A shopping cart may need one instance per user session.

Bean Scopes allow Spring to manage these different requirements.

---

## ⚙️ Common Bean Scopes

### Singleton (Default)

One Bean instance for the entire Spring IoC Container.

---

### Prototype

A new Bean instance is created every time it is requested.

---

### Request

One Bean per HTTP request.

(Used in Spring Web applications.)

---

### Session

One Bean per HTTP session.

(Used in Spring Web applications.)

---

### Application

One Bean shared across the entire web application.

---

## 💻 Example

```java
@Component
@Scope("singleton")
public class UserService {

}
```

```java
@Component
@Scope("prototype")
public class ReportGenerator {

}
```

---

## ✅ Benefits

- Efficient memory usage.
- Better resource management.
- Flexible object lifecycles.
- Improved scalability.

---

## ⚡ Backend Engineer Tips

Use the default singleton scope unless you have a clear reason not to.

Changing Bean scope should be a design decision, not a habit.

---

## ❌ Common Mistakes

- Assuming every Bean creates a new object.
- Using prototype scope unnecessarily.
- Storing user-specific data inside singleton Beans.

---

## 📝 Quick Revision

- Bean Scope determines how many instances Spring creates.
- Singleton = one shared instance.
- Prototype = new instance every request to the container.
- Web scopes are used in web applications.
