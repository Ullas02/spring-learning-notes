# Field Injection

## 🎯 What is Field Injection?

Field Injection is a Dependency Injection technique where Spring injects a dependency directly into a class field.

Instead of using a constructor or a setter method, Spring writes the dependency into the field using reflection.

---

## ❓ Why do we need it?

Field Injection provides a short and convenient way to inject dependencies.

Example:

```java
@Component
public class Car {

    @Autowired
    private Engine engine;

}
```

Spring automatically injects the `Engine` Bean into the field.

---

## ⚙️ How does it work?

Spring performs these steps:

1. Creates the Bean.
2. Uses reflection to access the private field.
3. Assigns the dependency.
4. Bean becomes ready for use.

---

## 💻 Example

```java
@Component
public class Car {

    @Autowired
    private Engine engine;

    public void drive() {
        engine.start();
    }

}
```

---

## ✅ Advantages

- Less code.
- Easy to read in small examples.
- Common in older Spring projects.

---

## ❌ Disadvantages

- Cannot use `final` fields.
- Hidden dependencies.
- Harder to unit test.
- Breaks immutability.
- Not recommended for new production code.

---

## ⚡ Backend Engineer Tips

Prefer Constructor Injection for required dependencies.

Use Field Injection only when maintaining legacy code or in rare framework-driven scenarios.

---

## ❌ Common Mistakes

- Using Field Injection everywhere because it is shorter.
- Hiding required dependencies.
- Creating classes that are difficult to test.

---

## 📝 Quick Revision

- Field Injection injects dependencies directly into fields.
- It relies on reflection.
- It works, but Constructor Injection is generally preferred for production applications.
