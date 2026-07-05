# Spring IoC Container

## 🎯 What is it?

The Spring IoC (Inversion of Control) Container is the core component of the Spring Framework.

It is responsible for:

- Creating objects (Beans)
- Managing Beans
- Injecting dependencies
- Configuring Beans
- Managing the Bean lifecycle
- Providing Beans whenever the application needs them

Think of it as the **brain of a Spring application**.

Without the IoC Container, there is no Spring.

---

## ❓ Why do we need it?

Imagine an application with 500 classes.

Without a container, every class would need to:

- create its own dependencies
- manage object lifecycles
- share objects manually
- configure objects manually

This quickly becomes difficult to maintain.

The IoC Container centralizes all of these responsibilities.

---

## ⚙️ How does it work?

When a Spring application starts:

1. Spring reads the configuration.
2. It identifies the classes that should become Beans.
3. It creates those Beans.
4. It resolves dependencies between Beans.
5. It injects the dependencies.
6. It stores the Beans in the container.
7. Whenever a Bean is requested, the container returns it.

---

## 🏗️ What is a Bean?

A Bean is simply an object managed by the Spring IoC Container.

Not every Java object is a Bean.

Example:

```java
new Engine();
```

This object is **not** managed by Spring.

However:

```java
@Component
public class Engine {

}
```

Spring creates and manages this object.

It becomes a Bean.

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

When the application starts:

Spring creates:

- Engine Bean
- Car Bean

Then it injects the `Engine` Bean into the `Car` Bean automatically.

---

## ✅ Responsibilities of the IoC Container

- Bean creation
- Dependency Injection
- Bean configuration
- Bean lifecycle management
- Scope management
- Bean lookup

---

## ⚡ Backend Engineer Tips

The IoC Container should manage application components such as:

- Services
- Controllers
- Repositories
- Configurations

It should **not** manage simple data objects like DTOs or entities.

---

## ❌ Common Mistakes

❌ Thinking every object is a Bean.

❌ Creating Spring-managed services using `new`.

❌ Confusing a Bean with a Java class.

---

## 📝 Quick Revision

- The IoC Container is the heart of Spring.
- It creates and manages Beans.
- It performs Dependency Injection.
- A Bean is an object managed by Spring.
