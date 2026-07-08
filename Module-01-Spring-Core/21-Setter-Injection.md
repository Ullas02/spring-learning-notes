# Setter Injection

## 🎯 What is Setter Injection?

Setter Injection is a Dependency Injection technique where Spring injects dependencies using setter methods after creating the object.

Unlike Constructor Injection, the object is created first, and then its dependencies are assigned.

---

## ❓ Why do we need Setter Injection?

Setter Injection is useful when a dependency is **optional** or may need to be changed after object creation.

Typical use cases include:

- Optional services
- Configurable components
- Legacy applications

---

## ⚙️ How does it work?

Spring performs these steps:

1. Creates the Bean.
2. Calls the setter method.
3. Injects the dependency.
4. Bean becomes ready for use.

---

## 💻 Example

```java
@Component
public class Car {

    private Engine engine;

    @Autowired
    public void setEngine(Engine engine) {
        this.engine = engine;
    }

}
```

---

## ✅ Benefits

- Suitable for optional dependencies.
- Easier to reconfigure after object creation.
- Common in older Spring projects.

---

## ❌ Drawbacks

- Dependency is not mandatory.
- Bean can exist in an incomplete state.
- Harder to create immutable classes.
- Easier to accidentally forget dependency injection.

---

## ⚡ Backend Engineer Tips

Use Setter Injection only for optional dependencies.

For required dependencies, prefer Constructor Injection.

---

## ❌ Common Mistakes

- Using Setter Injection for every dependency.
- Forgetting to initialize required dependencies.
- Making required dependencies mutable.

---

## 📝 Quick Revision

- Setter Injection uses setter methods.
- Object is created first.
- Dependencies are injected later.
- Best for optional dependencies.
