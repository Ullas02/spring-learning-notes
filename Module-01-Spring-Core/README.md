# Module 01 - Spring Core

## 📖 Module Overview

This module introduces the core concepts of the Spring Framework that form the foundation of modern Spring-based backend development.

The focus of this module is understanding how Spring manages objects, performs Dependency Injection, and promotes clean, maintainable application architecture.

By the end of this module, I should be able to build a Spring Core application from scratch using Java-based configuration and apply Spring's core features with confidence.

---

# 🎯 Learning Objectives

After completing this module, we should be able to:

* Understand the purpose of the Spring Framework.
* Explain Inversion of Control (IoC) and Dependency Injection (DI).
* Create and manage Spring Beans.
* Configure applications using Java Configuration.
* Use Component Scanning to discover Beans.
* Inject dependencies using Constructor Injection.
* Resolve multiple Bean implementations.
* Understand the Bean Lifecycle.
* Configure applications using Profiles and Properties.
* Apply Spring Core best practices in real-world applications.

---

# 📚 Topics Covered

* Spring Framework Introduction
* Why Spring?
* Problems Before Spring
* Spring Ecosystem Overview
* Spring vs Spring Boot
* Inversion of Control (IoC)
* Dependency Injection (DI)
* Spring IoC Container
* BeanFactory vs ApplicationContext
* Spring Beans
* Ways to Create Beans
* Stereotype Annotations
* Component Scanning
* Bean Lifecycle
* Bean Initialization and Destruction
* Bean Scopes
* Singleton vs Prototype
* Constructor Injection
* Setter Injection
* Field Injection
* `@Autowired`
* `@Qualifier`
* `@Primary`
* Resolving Multiple Bean Conflicts
* `@Bean`
* `@Configuration`
* Component vs Bean
* Third-Party Beans
* Java Configuration
* Lazy Initialization
* `@Value`
* Spring Profiles
* Bean Wiring Best Practices
* Spring Core Final Mini Project

---

# 📂 Repository Structure

```text
Module-01-Spring-Core/
│
├── 01-Spring-Framework-Introduction.md
├── 02-Why-Spring.md
├── ...
├── 37-Spring-Core-Final-Mini-Project.md
├── 38-Module-01-Revision-Guide.md
└── README.md
```

---

# 💻 Mini Project

## Spring Core Employee Management System

A layered Spring Core application demonstrating:

* Java Configuration
* Component Scanning
* Constructor Injection
* Bean Lifecycle
* Profiles
* `@Value`
* Layered Architecture

The project is available in the **`spring-learning-projects`** repository.

---

# 🏗️ Skills Acquired

After completing this module, I have learned to:

* Configure a Spring Core application.
* Create and manage Spring Beans.
* Perform Dependency Injection using best practices.
* Organize projects using layered architecture.
* Manage Bean lifecycle events.
* Configure applications using Profiles.
* Externalize configuration using `@Value`.
* Build maintainable Spring applications.

---

# 🏆 Backend Best Practices

* Prefer Constructor Injection.
* Keep service classes stateless.
* Program to interfaces.
* Use `@Bean` for third-party classes.
* Use `@Component` and its specialized annotations for application classes.
* Organize configuration classes by responsibility.
* Avoid hardcoded configuration values.
* Use Profiles for environment-specific configuration.
* Follow clean package naming conventions.
* Design classes with a single responsibility.

---

# 📖 Learning Outcome

By completing Module 1, I have built a strong foundation in Spring Core.

I now understand how Spring creates, manages, and wires objects together, allowing me to build applications that are modular, maintainable, and testable.

This knowledge forms the basis for all advanced Spring technologies, including Spring Boot, Spring MVC, Spring Data JPA, and Spring Security.

---
