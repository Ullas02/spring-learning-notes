# BeanFactory vs ApplicationContext

## 🎯 What is it?

Both **BeanFactory** and **ApplicationContext** are Spring IoC Containers.

Their primary job is to:

- Create Beans
- Manage Beans
- Inject dependencies

The difference is that **ApplicationContext** provides many additional enterprise features, making it the preferred choice for almost all modern Spring applications.

---

## ❓ Why do we need two containers?

Spring was originally designed to be lightweight.

Some applications only needed basic Bean management, so Spring introduced `BeanFactory`.

As enterprise applications grew more complex, developers needed features like:

- Event handling
- Internationalization (i18n)
- Annotation support
- Automatic Bean post-processing
- Easy integration with other Spring modules

To support these, Spring introduced `ApplicationContext`.

---

## ⚙️ How do they work?

### BeanFactory

Provides only the essential IoC features:

- Creates Beans
- Injects dependencies
- Manages Bean lifecycle

---

### ApplicationContext

Includes everything in BeanFactory, plus:

- Event publishing
- Message resources (i18n)
- Annotation processing
- Automatic BeanPostProcessor registration
- Easy integration with Spring Boot, Spring MVC, Spring Security, etc.

---

## 💻 Example

```java
ApplicationContext context =
        new AnnotationConfigApplicationContext(AppConfig.class);

UserService userService =
        context.getBean(UserService.class);
```

The `ApplicationContext` creates the `UserService` Bean and injects all required dependencies automatically.

---

## ✅ Benefits of ApplicationContext

- Rich feature set
- Better integration with the Spring ecosystem
- Production-ready
- Supports annotations like `@Component`, `@Service`, and `@Repository`
- Preferred by Spring Boot

---

## ⚡ Backend Engineer Tips

Unless you're learning Spring internals or working with a very specialized use case, you'll almost always use `ApplicationContext`.

Spring Boot creates and manages an `ApplicationContext` for you automatically.

---

## ❌ Common Mistakes

❌ Thinking `ApplicationContext` and `BeanFactory` are different frameworks.

❌ Using `BeanFactory` in a production Spring Boot application.

❌ Believing `ApplicationContext` replaces IoC.

It **is** an IoC Container.

---

## 📝 Quick Revision

- Both are IoC Containers.
- `BeanFactory` provides basic Bean management.
- `ApplicationContext` extends `BeanFactory`.
- Modern Spring applications use `ApplicationContext`.
