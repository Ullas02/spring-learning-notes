# First Spring Core Project

## 🎯 What are we building?

Our first Spring Core application using:

- Maven
- Spring Context
- Java Configuration
- ApplicationContext
- Spring-managed Beans

The goal is to understand how Spring creates and manages objects.

---

## ❓ Why are we building this?

So far we've learned:

- IoC
- Dependency Injection
- IoC Container
- ApplicationContext

Now we'll see these concepts working in a real application.

---

## 🏗️ Project Structure

```
spring-learning-projects/
└── spring-core/
    └── spring-core-day-02-first-project/
        ├── pom.xml
        └── src/
            └── main/
                └── java/
                    └── com/
                        └── example/
                            └── springcore/
                                ├── App.java
                                ├── AppConfig.java
                                ├── Engine.java
                                └── Car.java
```

---

## ⚙️ How does it work?

1. Start the application.
2. Create an ApplicationContext.
3. Load configuration.
4. Spring creates Beans.
5. Spring injects dependencies.
6. Retrieve a Bean.
7. Use the Bean.

---

## ✅ What you'll learn

- Java Configuration
- @Bean
- ApplicationContext
- Bean creation
- Constructor Injection

---

## ⚡ Backend Engineer Tips

Always let Spring create your services.

Avoid creating Spring-managed objects using `new`.

---

## ❌ Common Mistakes

- Forgetting to register a Bean.
- Mixing manual object creation with Spring-managed objects.
- Creating multiple ApplicationContexts unnecessarily.

---

## 📝 Quick Revision

- ApplicationContext manages Beans.
- Beans are created from configuration.
- Dependencies are injected automatically.
- Business classes don't create their own dependencies.
