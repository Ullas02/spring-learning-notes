# Ways to Create Beans in Spring

## 🎯 What is it?

Spring provides multiple ways to register Beans with the IoC Container.

The two most common approaches are:

1. Java Configuration using `@Bean`
2. Component Scanning using `@Component`

Both create Spring-managed Beans.

The difference is **who is responsible for creating them**.

---

## ❓ Why do we need two approaches?

Some classes belong to your application and can be discovered automatically.

Other objects require custom creation logic or come from third-party libraries that you cannot modify.

Spring supports both scenarios.

---

## ⚙️ Method 1: `@Bean`

```java
@Configuration
public class AppConfig {

    @Bean
    public Engine engine() {
        return new Engine();
    }

}
```

Here:

- You explicitly tell Spring how to create the object.
- Spring executes the method.
- The returned object becomes a Bean.

---

## ⚙️ Method 2: `@Component`

```java
@Component
public class Engine {

}
```

Spring discovers this class during component scanning.

No `@Bean` method is required.

---

## 💻 Example

### Using `@Bean`

```java
@Bean
public Car car() {
    return new Car(engine());
}
```

---

### Using `@Component`

```java
@Component
public class Car {

}
```

Spring creates the object automatically.

---

## ✅ Benefits

### `@Bean`

- Full control over object creation.
- Ideal for third-party libraries.
- Supports custom initialization.

### `@Component`

- Less configuration.
- Cleaner code.
- Easier to maintain.
- Preferred for application classes.

---

## ⚡ Backend Engineer Tips

A common guideline is:

- **Your own classes** (`Service`, `Repository`, `Controller`, etc.) → Use `@Component` or a specialized stereotype.
- **External or specially configured objects** → Use `@Bean`.

---

## ❌ Common Mistakes

❌ Using `@Bean` for every class.

❌ Using `@Component` for classes from third-party libraries (you usually can't modify them).

❌ Mixing approaches without understanding why.

---

## 📝 Quick Revision

- `@Bean` uses Java configuration.
- `@Component` relies on component scanning.
- Both register Beans with the IoC Container.
- Choose the approach based on the use case.
