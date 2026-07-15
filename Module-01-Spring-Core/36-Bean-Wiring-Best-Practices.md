# Bean Wiring Best Practices

## 🎯 What is Bean Wiring?

Bean wiring is the process of connecting Spring Beans together so they can collaborate to perform application tasks.

Spring manages this process through Dependency Injection (DI).

---

## ❓ Why do Best Practices Matter?

Spring offers multiple ways to create and inject Beans.

Just because something works doesn't mean it's the best choice.

Following consistent practices makes applications:

- Easier to maintain
- Easier to test
- Less error-prone
- Easier for teams to understand

---

## ✅ Recommended Practices

### 1. Prefer Constructor Injection

```java
@Service
public class UserService {

    private final UserRepository repository;

    public UserService(UserRepository repository) {
        this.repository = repository;
    }
}
```

Why?

- Dependencies are mandatory.
- Objects become immutable.
- Easier unit testing.
- No partially initialized objects.

---

### 2. Avoid Field Injection

```java
@Autowired
private UserRepository repository;
```

Problems:

- Difficult to test.
- Hidden dependencies.
- Harder to create immutable classes.

Use field injection only when there's a specific reason.

---

### 3. Use Setter Injection for Optional Dependencies

Setter injection is appropriate when a dependency is optional or may change after object creation.

---

### 4. Use `@Component` for Your Own Classes

```java
@Service
public class OrderService {

}
```

Spring automatically discovers your application classes through component scanning.

---

### 5. Use `@Bean` for External Libraries

```java
@Bean
public ObjectMapper objectMapper() {
    return new ObjectMapper();
}
```

Use `@Bean` when you cannot modify the source code of the class.

---

### 6. Use `@Primary` Carefully

Use `@Primary` when one implementation should be the default.

---

### 7. Use `@Qualifier` When You Need a Specific Bean

```java
public PaymentService(
        @Qualifier("paypalPaymentService")
        PaymentGateway gateway) {

}
```

This removes ambiguity when multiple implementations exist.

---

### 8. Keep Services Stateless

Avoid storing request-specific data in service fields.

Good:

```java
public User findById(Long id) {

}
```

Avoid:

```java
private User currentUser;
```

Stateless services are safer because singleton Beans are shared across the application.

---

### 9. Group Related Configuration

Instead of placing every `@Bean` method in one large configuration class, organize them by responsibility.

Example:

- DatabaseConfig
- SecurityConfig
- CacheConfig

---

## ⚡ Backend Engineer Tips

When reviewing Spring code, ask yourself:

- Are dependencies explicit?
- Is constructor injection used?
- Is the service stateless?
- Is the correct Bean selected?
- Is configuration organized?

---

## ❌ Common Mistakes

- Using field injection everywhere.
- Creating giant configuration classes.
- Overusing `@Primary`.
- Storing mutable state inside singleton services.

---

## 📝 Quick Revision

- Prefer constructor injection.
- Use `@Component` for your code.
- Use `@Bean` for third-party classes.
- Use `@Qualifier` to resolve ambiguity.
- Keep singleton services stateless.
