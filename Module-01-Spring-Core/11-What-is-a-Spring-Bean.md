# What is a Spring Bean?

## 🎯 What is it?

A Spring Bean is an object whose complete lifecycle is managed by the Spring IoC Container.

If Spring creates, configures, injects, and manages an object, that object is called a **Bean**.

---

## ❓ Why do we need Beans?

Without Beans:

- Every object must be created manually.
- Dependencies must be connected manually.
- Object lifecycle becomes difficult to manage.

Beans allow Spring to centralize these responsibilities.

---

## ⚙️ How does it work?

Application starts

↓

Spring scans configuration

↓

Creates Bean

↓

Injects dependencies

↓

Stores Bean in IoC Container

↓

Returns Bean whenever needed

---

## 💻 Example

```java
@Bean
public Engine engine() {
    return new Engine();
}
```

The returned `Engine` object becomes a Spring Bean.

---

## ✅ Benefits

- Centralized object management
- Dependency Injection
- Lifecycle management
- Better maintainability

---

## ⚡ Backend Engineer Tips

Remember:

> Every Bean is a Java object.

But:

> Not every Java object is a Spring Bean.

---

## ❌ Common Mistakes

- Assuming every class is automatically a Bean.
- Creating Spring-managed services using `new`.

---

## 📝 Quick Revision

- Bean = Spring-managed object.
- Beans live inside the IoC Container.
- Spring creates and manages Beans.
