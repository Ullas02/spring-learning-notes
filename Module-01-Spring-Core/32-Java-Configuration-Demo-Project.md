# Java Configuration Demo Project

## 🎯 Objective

Build a Spring Core application that demonstrates:

- `@Configuration`
- `@Bean`
- `@Component`
- `@Service`
- Component Scanning
- Third-party Bean Registration
- Constructor Injection
- Clean package structure

---

## 📁 Project Name

spring-core-java-configuration-demo

---

## 📂 Recommended Project Structure

```
spring-core-java-configuration-demo/
│
├── src/main/java/
│   └── com/example/javaconfigdemo/
│       ├── App.java
│       │
│       ├── config/
│       │   ├── AppConfig.java
│       │   └── NotificationConfig.java
│       │
│       ├── component/
│       │   ├── Engine.java
│       │   └── Car.java
│       │
│       ├── service/
│       │   ├── VehicleService.java
│       │   └── NotificationService.java
│       │
│       └── thirdparty/
│           └── NotificationClient.java
│
└── pom.xml
```

---

## 🎯 Learning Outcomes

After completing this project you will understand:

- Automatic Bean registration
- Manual Bean registration
- Configuration classes
- Third-party Bean integration
- Constructor Injection
- Package organization

---

## ⚡ Backend Engineer Tips

Use this project as your reference whenever you need to create custom configuration in Spring applications.

---

## 📝 Quick Revision

- `@Component` → Automatic Bean registration
- `@Bean` → Manual Bean registration
- `@Configuration` → Bean definition class
- Third-party classes are usually registered using `@Bean`
