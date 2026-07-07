# Component Scanning

## 🎯 What is Component Scanning?

Component Scanning is a feature that allows Spring to automatically discover classes annotated with stereotype annotations and register them as Beans.

Instead of manually creating Beans using `@Bean`, Spring scans specified packages and creates the Beans automatically.

---

## ❓ Why do we need it?

Imagine an application with:

- 50 Services
- 30 Repositories
- 20 Controllers
- 15 Utility Components

Writing a `@Bean` method for every class would be repetitive and difficult to maintain.

Component Scanning eliminates this boilerplate.

---

## ⚙️ How does it work?

When the application starts:

1. Spring creates the `ApplicationContext`.
2. It scans the configured packages.
3. It finds classes annotated with:
   - `@Component`
   - `@Service`
   - `@Repository`
   - `@Controller`
   - `@RestController`
4. It creates Beans for those classes.
5. It resolves dependencies.
6. It stores the Beans in the IoC Container.

---

## 💻 Example

```java
@Component
public class Engine {

}
```

```java
@Component
public class Car {

    private final Engine engine;

    public Car(Engine engine) {
        this.engine = engine;
    }

}
```

With component scanning enabled, Spring automatically creates both Beans and injects `Engine` into `Car`.

---

## ✅ Benefits

- Less configuration
- Cleaner code
- Easier maintenance
- Better scalability
- Standard approach in modern Spring projects

---

## ⚡ Backend Engineer Tips

Component Scanning is ideal for your own application classes.

Use `@Bean` when you need custom object creation or when working with third-party libraries.

---

## ❌ Common Mistakes

❌ Forgetting to enable component scanning.

❌ Placing classes outside the scanned package.

❌ Mixing manual object creation (`new`) with Spring-managed dependencies.

---

## 📝 Quick Revision

- Component Scanning automatically registers annotated classes as Beans.
- It works with stereotype annotations.
- It reduces manual Bean configuration.
