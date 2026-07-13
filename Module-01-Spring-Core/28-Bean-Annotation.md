# @Bean Annotation

## 🎯 What is `@Bean`?

`@Bean` is a Spring annotation used to explicitly create and register an object as a Spring Bean.

Unlike `@Component`, where Spring creates the object automatically during component scanning, `@Bean` allows you to define exactly how the object should be created.

---

## ❓ Why do we need it?

Not every class can be annotated with `@Component`.

Examples include:

- Third-party library classes
- Legacy classes
- Objects requiring custom initialization
- Beans whose creation depends on runtime configuration

`@Bean` lets you register these objects with the Spring IoC Container.

---

## ⚙️ How does it work?

1. Spring scans a class annotated with `@Configuration`.
2. It finds methods annotated with `@Bean`.
3. It executes those methods.
4. The returned object is registered as a Spring Bean.

---

## 💻 Example

```java
@Configuration
public class AppConfig {

    @Bean
    public Engine engine() {
        return new Engine();
    }
}
```

Spring executes the `engine()` method once and stores the returned object in the IoC Container.

---

## ✅ Benefits

- Full control over object creation.
- Supports third-party classes.
- Allows custom initialization.
- Keeps configuration centralized.

---

## ⚡ Backend Engineer Tips

Use `@Component` for your own application classes.

Use `@Bean` when you need explicit control over Bean creation or when the class cannot be modified.

---

## ❌ Common Mistakes

- Forgetting to place `@Bean` methods inside a `@Configuration` class.
- Creating objects manually with `new` instead of letting Spring manage them.
- Using `@Bean` for every class, even when `@Component` is sufficient.

---

## 📝 Quick Revision

- `@Bean` registers an object with Spring.
- It must be declared inside a `@Configuration` class.
- It is commonly used for third-party or specially configured objects.
