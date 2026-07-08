# Constructor Injection - Deep Dive

## 🎯 What is Constructor Injection?

Constructor Injection is a Dependency Injection technique where Spring provides all required dependencies through a class constructor.

Instead of creating dependencies using `new`, Spring creates them and passes them to the constructor.

---

## ❓ Why do we need it?

Without Dependency Injection, classes become tightly coupled.

Example:

```java
public class Car {

    private Engine engine = new Engine();

}
```

Problems:

- Difficult to test
- Difficult to replace implementations
- Violates the Dependency Inversion Principle
- Strong coupling

Constructor Injection solves these problems.

---

## ⚙️ How does it work?

Spring:

1. Creates the dependency Bean.
2. Creates the target Bean.
3. Calls the constructor.
4. Injects the dependency.

---

## 💻 Example

```java
@Component
public class Car {

    private final Engine engine;

    public Car(Engine engine) {
        this.engine = engine;
    }

}
```

Spring automatically injects the `Engine` Bean.

---

## ✅ Benefits

- Immutable dependencies
- Easier testing
- Mandatory dependencies
- Better readability
- Recommended by Spring

---

## ⚡ Backend Engineer Tips

If a dependency is required for a class to work, inject it through the constructor.

---

## ❌ Common Mistakes

- Creating dependencies using `new`.
- Using constructor injection for optional dependencies.
- Having constructors with too many dependencies (often indicates the class has too many responsibilities).

---

## 📝 Quick Revision

- Constructor Injection is Spring's recommended approach.
- Dependencies are provided through the constructor.
- It promotes loose coupling and testability.
