# @Autowired Annotation

## 🎯 What is `@Autowired`?

`@Autowired` is a Spring annotation used to tell the Spring IoC Container to automatically inject a matching Bean into another Bean.

Instead of creating dependencies manually using `new`, Spring finds the required Bean and injects it.

---

## ❓ Why do we need it?

Without `@Autowired`, developers would have to manually create and manage every dependency.

Spring automates this process, making applications:

- Loosely coupled
- Easier to maintain
- Easier to test
- More scalable

---

## ⚙️ How does it work?

When Spring creates a Bean:

1. It scans the class.
2. Finds places marked with `@Autowired`.
3. Searches the IoC Container for a matching Bean.
4. Injects the Bean automatically.

If no suitable Bean is found, Spring throws an exception (unless the dependency is optional).

---

## 💻 Example

### Constructor Injection

```java
@Component
public class Car {

    private final Engine engine;

    @Autowired
    public Car(Engine engine) {
        this.engine = engine;
    }
}
```

### Setter Injection

```java
@Autowired
public void setEngine(Engine engine) {
    this.engine = engine;
}
```

### Field Injection

```java
@Autowired
private Engine engine;
```

---

## ✅ Benefits

- Automatic dependency resolution.
- Less boilerplate code.
- Promotes loose coupling.
- Simplifies object creation.

---

## ⚡ Backend Engineer Tips

In Spring Framework 4.3+, if a class has only one constructor, `@Autowired` on that constructor is optional.

---

## ❌ Common Mistakes

- Expecting Spring to inject objects created with `new`.
- Forgetting to annotate classes as Spring Beans (`@Component`, `@Service`, etc.).
- Having multiple matching Beans without telling Spring which one to use.

---

## 📝 Quick Revision

- `@Autowired` performs automatic dependency injection.
- Spring injects only Spring-managed Beans.
- Single-constructor classes do not require `@Autowired`.
