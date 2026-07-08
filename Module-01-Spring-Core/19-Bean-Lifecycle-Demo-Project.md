# Bean Lifecycle Demo Project

## 🎯 Objective

Build a Spring Core application that demonstrates how Spring manages the complete lifecycle of Beans.

The project covers:

- Component Scanning
- Dependency Injection
- Bean Lifecycle
- Bean Scopes
- Singleton vs Prototype

---

## 📁 Project Name

spring-core-bean-lifecycle-demo

---

## 📂 Recommended Project Structure

```text
src
└── main
    └── java
        └── com.example.lifecycle
            ├── App.java
            ├── config
            │     └── AppConfig.java
            ├── component
            │     ├── Engine.java
            │     ├── Car.java
            │     └── DatabaseManager.java
            └── service
                  └── VehicleService.java
```

---


## 🎯 Learning Outcomes

After completing this project, you should understand:

- How Spring creates Beans
- When constructors execute
- When `@PostConstruct` executes
- When `@PreDestroy` executes
- Difference between Singleton and Prototype
- How Dependency Injection works with Component Scanning

---

## ⚡ Backend Engineer Tips

This project demonstrates the internal behavior of the Spring IoC Container.

Understanding it will make debugging dependency injection and lifecycle issues much easier in real backend applications.

---

## 📝 Quick Revision

- Spring manages Bean lifecycle.
- Component Scanning discovers Beans automatically.
- Singleton is the default scope.
- Prototype creates a new instance for each lookup.
- Lifecycle callbacks execute automatically for singleton Beans.
