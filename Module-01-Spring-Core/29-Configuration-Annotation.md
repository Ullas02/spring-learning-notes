 # @Configuration Annotation

## 🎯 What is `@Configuration`?

`@Configuration` is a Spring annotation that marks a class as a source of Bean definitions.

It tells Spring:

> "This class contains methods that create and configure Spring Beans."

Spring processes these classes during application startup and registers the returned objects in the IoC Container.

---

## ❓ Why do we need it?

Without `@Configuration`, Spring would not know that a class is intended to define application Beans.

It provides:

- Centralized Bean configuration
- Java-based configuration (instead of XML)
- Proper singleton management
- Dependency handling between `@Bean` methods

---

## ⚙️ How does it work?

1. Spring scans for classes annotated with `@Configuration`.
2. It finds methods annotated with `@Bean`.
3. It executes each `@Bean` method.
4. The returned objects are registered in the IoC Container.
5. Future requests for those Beans return the managed instance.

---

## 💻 Example

```java
@Configuration
public class AppConfig {

    @Bean
    public Engine engine() {
        return new Engine();
    }

    @Bean
    public Car car() {
        return new Car(engine());
    }
}
```

Spring ensures that both `car()` and any other consumer receive the same managed `Engine` Bean.

---

## ✅ Benefits

- Java-based configuration
- Centralized Bean creation
- Better readability than XML
- Supports dependency wiring between Beans

---

## ⚡ Backend Engineer Tips

Use `@Configuration` for application configuration classes. Group related Bean definitions together (for example, database configuration, security configuration, or messaging configuration).

---

## ❌ Common Mistakes

- Placing `@Bean` methods in random classes.
- Confusing `@Configuration` with `@Component`.
- Manually creating objects with `new` outside Spring when they should be managed Beans.

---

## 📝 Quick Revision

- `@Configuration` marks a class that defines Spring Beans.
- It works together with `@Bean`.
- Spring enhances `@Configuration` classes to preserve Bean lifecycle and scope.
