# @Component vs @Bean

## 🎯 What is the difference?

Both `@Component` and `@Bean` register objects as Spring Beans, but they do so in different ways.

- `@Component` uses **automatic component scanning**.
- `@Bean` uses **explicit Java configuration**.

The result is the same: the object becomes a Spring-managed Bean.

The difference is **how the Bean is created and who controls its creation**.

---

## ❓ When should we use each?

### Use `@Component` when:

- You own the class.
- The class is part of your application.
- Spring can discover it through component scanning.

Examples:

- `@Service`
- `@Repository`
- `@Controller`
- Utility components

### Use `@Bean` when:

- You do not own the class.
- The class belongs to a third-party library.
- Bean creation requires custom initialization.
- You want explicit control over object creation.

---

## ⚙️ How do they work?

### `@Component`

Spring scans packages.

```
@Component
        │
        ▼
Component Scan
        │
        ▼
Bean Registered
```

### `@Bean`

Spring scans configuration classes.

```
@Configuration
        │
        ▼
@Bean Method
        │
        ▼
Method Executes
        │
        ▼
Returned Object Registered
```

---

## 💻 Example

### Using `@Component`

```java
@Component
public class EmailService {

}
```

### Using `@Bean`

```java
@Configuration
public class AppConfig {

    @Bean
    public EmailService emailService() {
        return new EmailService();
    }
}
```

Both create a Spring Bean.

---

## ✅ Benefits

### `@Component`

- Less boilerplate
- Automatic registration
- Great for application classes

### `@Bean`

- Full control
- Works with third-party classes
- Supports custom creation logic

---

## ⚡ Backend Engineer Tips

A common rule:

- Application code → `@Component`
- Infrastructure and third-party objects → `@Bean`

---

## ❌ Common Mistakes

- Using `@Bean` for every class.
- Forgetting that `@Bean` methods belong inside `@Configuration`.
- Annotating third-party classes (which you usually cannot modify).

---

## 📝 Quick Revision

- `@Component` = automatic registration.
- `@Bean` = manual registration.
- Both create Spring-managed Beans.
