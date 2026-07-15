# Module 01 Revision Guide

## Spring Core – Quick Revision

---

# 1. Spring Framework

* Java framework for building enterprise applications.
* Provides IoC (Inversion of Control) and Dependency Injection.
* Promotes loose coupling and maintainable code.

---

# 2. Why Spring?

Before Spring:

* Objects created manually using `new`
* Tight coupling
* Difficult testing
* Difficult maintenance

Spring solves these problems by managing object creation and dependencies.

---

# 3. IoC (Inversion of Control)

Instead of creating objects yourself:

```java
UserService service = new UserService();
```

Spring creates and manages the object.

---

# 4. Dependency Injection (DI)

Dependencies are provided by Spring.

Recommended approach:

```java
public UserService(UserRepository repository) {
    this.repository = repository;
}
```

Prefer **Constructor Injection**.

---

# 5. IoC Container

Responsible for:

* Creating Beans
* Managing Beans
* Injecting Dependencies
* Managing Bean Lifecycle

Main implementations:

* BeanFactory
* ApplicationContext (recommended)

---

# 6. Spring Bean

A Bean is simply an object managed by the Spring IoC Container.

Examples:

* Services
* Repositories
* Controllers
* Configuration classes

---

# 7. Ways to Create Beans

* `@Component`
* `@Service`
* `@Repository`
* `@Controller`
* `@Bean`

---

# 8. Component Scanning

```java
@ComponentScan("com.example")
```

Automatically discovers Spring-managed classes.

---

# 9. Bean Lifecycle

```
Bean Created
      ↓
Dependencies Injected
      ↓
@PostConstruct
      ↓
Bean Ready
      ↓
Application Running
      ↓
@PreDestroy
```

---

# 10. Bean Scopes

* Singleton (Default)
* Prototype

Remember:

Singleton → One shared instance

Prototype → New instance every request

---

# 11. Dependency Injection Types

✅ Constructor Injection (Preferred)

⚠️ Setter Injection (Optional dependencies)

❌ Field Injection (Avoid in production)

---

# 12. @Autowired

Automatically injects dependencies.

Spring 4.3+ automatically performs constructor injection when there is only one constructor.

---

# 13. @Qualifier

Used when multiple Beans implement the same interface.

```java
@Qualifier("paypalService")
```

---

# 14. @Primary

Marks the default Bean.

Used only when one implementation should normally be selected.

---

# 15. @Bean

Creates Spring Beans manually.

Useful for:

* Third-party libraries
* External classes
* Custom object creation

---

# 16. @Configuration

Contains one or more `@Bean` methods.

Acts as Java-based configuration.

---

# 17. @Value

Injects configuration values.

Example:

```java
@Value("${application.name}")
private String appName;
```

---

# 18. Lazy Initialization

Default:

```
Application Starts
↓

Bean Created
```

Using `@Lazy`

```
Application Starts
↓

Bean NOT Created

↓

First Usage

↓

Bean Created
```

---

# 19. Spring Profiles

Separate environments.

Examples:

* dev
* test
* prod

Each profile can load different Beans.

---

# 20. Bean Wiring Best Practices

✔ Constructor Injection

✔ Stateless Services

✔ Interface-based Programming

✔ `@Bean` for third-party classes

✔ `@Component` for your own classes

✔ Organize configuration classes

---

# 21. Final Mini Project

Employee Management System

Concepts used:

* Java Configuration
* Component Scanning
* Constructor Injection
* Bean Lifecycle
* Profiles
* `@Value`
* Layered Architecture

---

# 🏆 Spring Core Best Practices

* Prefer Constructor Injection.
* Avoid Field Injection.
* Keep Services stateless.
* Program to interfaces.
* Keep configuration modular.
* Use Profiles for environment-specific configuration.
* Avoid hardcoded values.
* Use meaningful package names.
* Keep classes focused on a single responsibility.

---
