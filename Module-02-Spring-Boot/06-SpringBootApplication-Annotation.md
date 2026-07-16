# @SpringBootApplication

## 🎯 What is it?

`@SpringBootApplication` is the main annotation used in every Spring Boot application.

Although it appears to be a single annotation, it is actually a combination of three important Spring annotations.

```java
@SpringBootApplication
public class DemoApplication {

    public static void main(String[] args) {
        SpringApplication.run(DemoApplication.class, args);
    }

}
```

This single annotation enables most of Spring Boot's automatic behavior.

---

## ❓ Why do we need it?

Without `@SpringBootApplication`, we would have to configure several features manually.

Instead of writing multiple annotations ourselves, Spring Boot bundles them together into one convenient annotation.

This keeps applications simpler and more readable.

---

## ⚙️ What's Inside?

`@SpringBootApplication` is equivalent to:

```java
@Configuration
@EnableAutoConfiguration
@ComponentScan
```

Let's understand each one.

---

### 1. @Configuration

Marks the class as a source of Spring bean definitions.

It tells Spring:

> "This class contains application configuration."

You'll use it later when creating custom configuration classes.

---

### 2. @EnableAutoConfiguration

This is one of Spring Boot's biggest features.

It tells Spring Boot:

> "Look at my project's dependencies and automatically configure what I need."

Example:

If your project contains:

```xml
spring-boot-starter-web
```

Spring Boot automatically configures:

- Embedded Tomcat
- DispatcherServlet
- Jackson
- Spring MVC infrastructure

without requiring manual configuration.

---

### 3. @ComponentScan

You already learned this in Module 1.

It instructs Spring to scan the package containing the main application class and its subpackages for components such as:

- `@Controller`
- `@RestController`
- `@Service`
- `@Repository`
- `@Component`

These discovered classes become Spring-managed beans.

---

## 💻 Example

Suppose your project is:

```
com.example.demo
│
├── DemoApplication.java
│
├── controller
│   └── HelloController.java
│
├── service
│   └── UserService.java
│
└── repository
    └── UserRepository.java
```

Because `DemoApplication` is in the root package (`com.example.demo`), `@ComponentScan` automatically discovers the controller, service, and repository.

If you moved `HelloController` outside the scanned package hierarchy, Spring would not detect it unless you explicitly configured component scanning.

---

## ✅ Benefits

- Less configuration.
- Automatic component scanning.
- Automatic application configuration.
- Clean startup class.
- Easier project maintenance.

---

## ⚡ Backend Engineer Tips

Place your main application class in the **root package** of your project.

This ensures component scanning naturally includes all controllers, services, repositories, and configuration classes beneath it.

This is the standard layout used in production Spring Boot applications.

---

## ❌ Common Mistakes

- Placing the main class in a nested package, causing some components not to be scanned.
- Assuming `@EnableAutoConfiguration` configures everything regardless of dependencies.
- Creating multiple application classes with `@SpringBootApplication` unintentionally.

---

## 📝 Quick Revision

- `@SpringBootApplication` combines three annotations.
- `@Configuration` defines configuration.
- `@EnableAutoConfiguration` configures Spring Boot automatically.
- `@ComponentScan` discovers Spring-managed components.
- Place the main class in the root package.
