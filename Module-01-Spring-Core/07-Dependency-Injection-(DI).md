# Dependency Injection (DI)

## 🎯 What is it?

Dependency Injection (DI) is a technique used to achieve Inversion of Control (IoC).

Instead of a class creating the objects it depends on, those objects are provided (or "injected") from the outside.

In simple terms:

> **Don't create your dependencies. Receive them.**

---

## ❓ Why do we need it?

Imagine a `UserService` that needs:

- EmailService
- NotificationService
- UserRepository

Without DI, `UserService` creates all of them itself.

```java
public class UserService {

    private EmailService emailService = new EmailService();
    private NotificationService notificationService = new NotificationService();
    private UserRepository userRepository = new UserRepository();

}
```

Problems:

- Tight coupling
- Difficult to test
- Hard to replace implementations
- Difficult to maintain

With DI, Spring creates these objects and injects them into `UserService`.

---

## ⚙️ How does it work?

Spring follows these steps:

1. Create all required Beans.
2. Resolve dependencies between Beans.
3. Inject the dependencies.
4. Return a fully initialized object.

Your class only declares what it needs.

---

## 💻 Example

```java
@Service
public class UserService {

    private final EmailService emailService;

    public UserService(EmailService emailService) {
        this.emailService = emailService;
    }

}
```

Notice there is no:

```java
new EmailService();
```

Spring injects the dependency automatically.

---

## 🔄 Types of Dependency Injection

### 1. Constructor Injection ✅ (Recommended)

```java
public class UserService {

    private final EmailService emailService;

    public UserService(EmailService emailService) {
        this.emailService = emailService;
    }

}
```

Best choice because:

- Required dependencies are guaranteed.
- Supports immutable fields (`final`).
- Easier to test.
- Preferred by Spring.

---

### 2. Setter Injection

```java
public class UserService {

    private EmailService emailService;

    public void setEmailService(EmailService emailService) {
        this.emailService = emailService;
    }

}
```

Useful for optional dependencies.

---

### 3. Field Injection ❌ (Not Recommended)

```java
@Autowired
private EmailService emailService;
```

Although concise, it has drawbacks:

- Harder to unit test.
- Hidden dependencies.
- Cannot use `final`.
- Makes immutability difficult.

---

## ✅ Benefits

- Loose coupling
- Easier testing
- Better maintainability
- Better readability
- Flexible implementations
- Cleaner architecture

---

## ⚡ Backend Engineer Tips

Prefer Constructor Injection for required dependencies.

If a class has many constructor parameters (for example, more than 5–7), it's often a sign that the class has too many responsibilities and should be refactored.

---

## ❌ Common Mistakes

❌ Using Field Injection everywhere.

❌ Creating dependencies with `new` inside Spring-managed services.

❌ Confusing DI with IoC.

Remember:

- IoC = Design principle
- DI = One implementation technique

---

## 📝 Quick Revision

- DI provides dependencies from outside the class.
- Spring performs Dependency Injection automatically.
- Constructor Injection is the recommended approach.
- DI helps achieve loose coupling and easier testing.
