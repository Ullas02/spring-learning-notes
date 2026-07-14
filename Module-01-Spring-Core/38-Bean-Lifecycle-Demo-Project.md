# Bean Lifecycle Demo Project

## 🎯 Objective

Build a Spring Core project that demonstrates the complete lifecycle of a Spring Bean.

The project will show exactly when Spring:

- Creates a Bean
- Injects dependencies
- Calls initialization methods
- Executes business logic
- Destroys the Bean

---

## 📁 Project Name

spring-core-bean-lifecycle-demo

---

## 📂 Recommended Project Structure

spring-core-bean-lifecycle-demo/
│
├── src/
│   └── main/
│       ├── java/
│       │   └── com/example/lifecycle/
│       │       ├── App.java
│       │       ├── AppConfig.java
│       │       │
│       │       ├── repository/
│       │       │      UserRepository.java
│       │       │
│       │       └── service/
│       │              UserService.java
│       │
│       └── resources/
│
└── pom.xml

---

## 🎯 Learning Outcomes

After completing this project you should understand:

- Complete Bean Lifecycle
- Dependency Injection timing
- @PostConstruct
- @PreDestroy
- ApplicationContext shutdown
- Lifecycle execution order

---

## ⚡ Backend Engineer Tips

Whenever your Bean owns external resources, use lifecycle callbacks instead of manually managing initialization and cleanup.

---

## 📝 Quick Revision

Constructor

↓

Dependency Injection

↓

@PostConstruct

↓

Business Logic

↓

@PreDestroy
