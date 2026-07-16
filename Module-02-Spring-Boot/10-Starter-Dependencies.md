# Starter Dependencies

## 🎯 What are Starter Dependencies?

Starter Dependencies are curated collections of commonly used libraries for a particular feature.

Instead of adding many individual libraries yourself, you add **one starter**, and Spring Boot includes the required dependencies.

For example:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

This single dependency provides everything needed to build a typical web application.

---

## ❓ Why do we need them?

Before Spring Boot, developers had to:

- Search for required libraries.
- Choose compatible versions.
- Add each dependency manually.
- Resolve version conflicts.

Example for a web application:

- Spring MVC
- Tomcat
- Jackson
- Logging
- Validation
- Servlet API

Managing these individually was time-consuming and error-prone.

Spring Boot starters solve this by providing a tested, compatible set of dependencies.

---

## ⚙️ How does it work?

A starter dependency is **not** a library that contains business functionality.

Instead, it is a dependency that **references other dependencies**.

When Maven processes your `pom.xml`, it downloads the starter and all the libraries it depends on.

This is called a **transitive dependency**.

---

## 💻 Common Starter Dependencies

| Starter | Purpose |
|---------|---------|
| `spring-boot-starter-web` | Build web and REST applications |
| `spring-boot-starter-data-jpa` | Database access using JPA/Hibernate |
| `spring-boot-starter-security` | Authentication and authorization |
| `spring-boot-starter-validation` | Bean validation |
| `spring-boot-starter-test` | Unit and integration testing |
| `spring-boot-starter-actuator` | Monitoring and production endpoints |

As we progress through the course, we'll introduce these starters when they're actually needed.

---

## 🌍 Real-World Example

Suppose your team starts building a REST API.

Without starters, every developer would need to know exactly which libraries to include.

With starters, everyone simply adds:

```xml
<artifactId>spring-boot-starter-web</artifactId>
```

The project becomes consistent across the team.

---

## ✅ Benefits

- Simpler dependency management.
- Compatible library versions.
- Faster project setup.
- Reduced configuration.
- Consistent projects across teams.

---

## ⚡ Backend Engineer Tips

Don't add starter dependencies "just in case."

Every dependency increases:

- Build time
- Application size
- Startup time
- Security surface

Only include starters that your application actually requires.

---

## ❌ Common Mistakes

- Adding multiple starters without understanding their purpose.
- Mixing incompatible library versions manually.
- Assuming a starter contains only one library.
- Ignoring transitive dependencies.

---

## 📝 Quick Revision

- Starters are curated dependency bundles.
- They simplify dependency management.
- Maven downloads transitive dependencies automatically.
- Use only the starters your project needs.
