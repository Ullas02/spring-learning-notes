# Stereotype Annotations in Spring

## 🎯 What are Stereotype Annotations?

Stereotype annotations tell Spring **what role a class plays** in the application.

All stereotype annotations create Spring Beans, but each one represents a different layer of the application.

The most common stereotype annotations are:

- `@Component`
- `@Service`
- `@Repository`
- `@Controller`
- `@RestController`

---

## ❓ Why do we need them?

Imagine a project with 500 classes.

If every class is marked with only:

```java
@Component
```

it's difficult to understand each class's responsibility.

Using stereotype annotations makes the architecture self-documenting.

---

## ⚙️ Common Stereotype Annotations

### `@Component`

A generic Spring Bean.

Use it when none of the more specific stereotypes apply.

---

### `@Service`

Represents the business logic layer.

Example:

```java
@Service
public class OrderService {

}
```

---

### `@Repository`

Represents the data access layer.

Example:

```java
@Repository
public class UserRepository {

}
```

---

### `@Controller`

Handles web requests in Spring MVC.

Example:

```java
@Controller
public class HomeController {

}
```

---

### `@RestController`

Handles REST API requests.

Example:

```java
@RestController
public class ProductController {

}
```

---

## 💻 Example Architecture

```
Controller
     │
     ▼
Service
     │
     ▼
Repository
     │
     ▼
Database
```

Each layer has a specific responsibility.

---

## ✅ Benefits

- Better readability
- Cleaner architecture
- Easier maintenance
- Additional Spring features
- Self-documenting code

---

## ⚡ Backend Engineer Tips

Always choose the most specific stereotype annotation available.

It makes your code easier to understand and aligns with Spring best practices.

---

## ❌ Common Mistakes

❌ Using `@Component` for everything.

❌ Placing database logic inside `@Service`.

❌ Placing business logic inside `@Controller`.

---

## 📝 Quick Revision

- All stereotype annotations create Beans.
- Each annotation represents a different architectural layer.
- Use the most appropriate stereotype instead of always using `@Component`.
