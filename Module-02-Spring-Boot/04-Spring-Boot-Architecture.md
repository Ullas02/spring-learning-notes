# Spring Boot Architecture (High-Level)

## 🎯 What is it?

Spring Boot Architecture describes how different components work together to start, configure, and run your application.

At a high level, Spring Boot acts as an intelligent layer on top of the Spring Framework. It analyzes your project, configures the required components automatically, and starts the application.

As a backend engineer, you don't need to memorize every internal class. Instead, you should understand the overall flow of how a Spring Boot application starts.

---

## ❓ Why do we need to understand the architecture?

Understanding the architecture helps you:

- Debug startup issues.
- Understand auto-configuration.
- Customize default behavior.
- Design applications more effectively.
- Read Spring Boot logs with confidence.

Without this understanding, Spring Boot may feel like "magic." The goal is to replace that magic with a clear mental model.

---

## ⚙️ High-Level Architecture

```
                    +----------------------+
                    |   Your Application   |
                    |  (@SpringBootApplication)
                    +----------+-----------+
                               |
                               v
                    +----------------------+
                    | SpringApplication    |
                    +----------+-----------+
                               |
                               v
                    +----------------------+
                    | Auto Configuration   |
                    +----------+-----------+
                               |
                +--------------+--------------+
                |                             |
                v                             v
      Spring Framework              Starter Dependencies
 (IoC, DI, MVC, AOP, etc.)       (Web, JPA, Security...)
                |                             |
                +--------------+--------------+
                               |
                               v
                    Embedded Web Server
                  (Tomcat / Jetty / Undertow)
                               |
                               v
                    Running Application
```

---

## ⚙️ Main Components

### 1. Your Application

Every Spring Boot application starts with a class like this:

```java
@SpringBootApplication
public class SpringBootApplication {

    public static void main(String[] args) {
        SpringApplication.run(SpringBootApplication.class, args);
    }

}
```

This is the entry point of the application.

---

### 2. SpringApplication

`SpringApplication.run()` is responsible for bootstrapping the application.

It performs tasks such as:

- Creating the Spring container.
- Loading configuration.
- Starting auto-configuration.
- Initializing beans.
- Starting the embedded server (if needed).

Think of it as the **orchestrator** that coordinates the startup process.

---

### 3. Auto Configuration

Auto Configuration examines:

- Dependencies on the classpath.
- Existing beans.
- Configuration properties.

Based on this information, it automatically creates and configures many beans.

For example:

If you include `spring-boot-starter-web`, Spring Boot automatically configures:

- DispatcherServlet
- Jackson
- Embedded Tomcat
- Request mapping infrastructure

You can override these defaults whenever necessary.

---

### 4. Starter Dependencies

Starter dependencies are curated collections of libraries for a specific purpose.

Examples:

- `spring-boot-starter-web`
- `spring-boot-starter-data-jpa`
- `spring-boot-starter-security`
- `spring-boot-starter-test`

Instead of selecting many individual libraries, you add one starter dependency.

---

### 5. Spring Framework

The Spring Framework provides the core functionality:

- IoC Container
- Dependency Injection
- Bean Lifecycle
- Spring MVC
- Spring AOP
- Transaction Management

Spring Boot uses these capabilities—it does not replace them.

---

### 6. Embedded Server

For web applications, Spring Boot starts an embedded server automatically.

Common choices are:

- Tomcat (default)
- Jetty
- Undertow

Because the server is packaged with your application, you can run it directly as an executable JAR.

---

## 💻 Startup Flow

When you run your application:

1. The `main()` method is executed.
2. `SpringApplication.run()` starts.
3. Spring creates the IoC container.
4. Auto Configuration configures required components.
5. Beans are created and wired together.
6. Embedded Tomcat starts (for web applications).
7. The application is ready to accept requests.

---

## 🌍 Real-World Example

Imagine opening a new restaurant every month.

Without Spring Boot:

Each time, you would need to:

- Hire staff manually.
- Install kitchen equipment.
- Arrange tables.
- Configure billing systems.
- Train everyone from scratch.

With Spring Boot:

You receive a standardized restaurant setup:

- Kitchen already installed.
- Billing system ready.
- Tables arranged.
- Staff guidelines prepared.

You focus on creating the menu (your business logic), while the standard infrastructure is handled for you.

---

## ✅ Benefits

- Clear startup process.
- Automatic configuration.
- Reduced manual setup.
- Faster development.
- Easier maintenance.
- Consistent architecture across projects.

---

## ⚡ Backend Engineer Tips

As your applications grow, you'll occasionally need to customize or disable Spring Boot's default behavior.

Understanding where Auto Configuration fits into the startup process makes these customizations much easier and helps you troubleshoot startup failures efficiently.

---

## ❌ Common Mistakes

- Thinking Auto Configuration creates everything automatically without conditions.
- Ignoring startup logs when troubleshooting.
- Assuming embedded Tomcat is always used (Jetty and Undertow are also supported).
- Treating `SpringApplication.run()` as a simple method call without understanding its responsibilities.

---

## 📝 Quick Revision

- Every application starts from `main()`.
- `SpringApplication.run()` bootstraps the application.
- Auto Configuration configures components automatically.
- Starter dependencies simplify dependency management.
- Spring Framework provides the core features.
- Embedded server runs the web application.
