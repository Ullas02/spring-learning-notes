# Registering Third-Party Library Beans

## 🎯 What are Third-Party Beans?

Third-party Beans are objects created from libraries that your application depends on but does not own.

Since you cannot modify these classes to add Spring annotations like `@Component`, you register them using `@Bean`.

---

## ❓ Why do we need them?

Many important libraries are external to your application, such as:

- Database connection pools
- HTTP clients
- JSON serializers
- Cloud SDK clients
- Cache clients
- Messaging clients

Spring still needs to manage these objects so they can be injected into your services.

---

## ⚙️ How does it work?

1. Add the external library as a dependency.
2. Create a `@Configuration` class.
3. Create a `@Bean` method that returns the library object.
4. Spring registers the returned object as a Bean.

---

## 💻 Example

```java
@Configuration
public class AppConfig {

    @Bean
    public ObjectMapper objectMapper() {
        return new ObjectMapper();
    }
}
```

Now any Spring Bean can inject `ObjectMapper`.

---

## ✅ Benefits

- Integrates external libraries with Spring.
- Centralizes configuration.
- Allows custom initialization.
- Supports dependency injection throughout the application.

---

## ⚡ Backend Engineer Tips

Keep infrastructure Beans (database, messaging, cloud clients, HTTP clients) in dedicated configuration classes instead of mixing them with business logic.

---

## ❌ Common Mistakes

- Trying to annotate third-party classes with `@Component`.
- Creating a new library object every time it is needed instead of using a Spring-managed Bean.
- Putting unrelated Bean definitions into one large configuration class.

---

## 📝 Quick Revision

- Third-party classes cannot usually be annotated.
- Register them using `@Bean`.
- Group related Beans into dedicated configuration classes.
