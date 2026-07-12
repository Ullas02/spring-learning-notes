# Dependency Injection Demo Project

## 🎯 Objective

Build a Spring Core application that demonstrates:

- Constructor Injection
- Setter Injection
- Field Injection
- `@Autowired`
- `@Qualifier`
- `@Primary`
- Interface-based programming
- Multiple Bean implementations
- Spring Component Scanning

---

## 📁 Project Name

spring-core-dependency-injection-demo

---

## 📂 Recommended Project Structure

src
└── main
    └── java
        └── com.example.di
            ├── App.java
            ├── config
            │     └── AppConfig.java
            ├── component
            │     ├── Car.java
            │     ├── Engine.java
            │     └── payment
            │           ├── PaymentGateway.java
            │           ├── UpiPayment.java
            │           ├── CreditCardPayment.java
            │           └── PaypalPayment.java
            └── service
                  ├── VehicleService.java
                  └── PaymentService.java

---

## 🎯 Learning Outcomes

After completing this project you should understand:

- How Spring performs Dependency Injection
- Different injection techniques
- Interface-based design
- Bean conflict resolution
- Best practices for production applications

---

## ⚡ Backend Engineer Tips

Use this project as your reference implementation whenever you work with Spring Dependency Injection.

---

## 📝 Quick Revision

- Constructor Injection is the preferred approach.
- `@Primary` defines the default Bean.
- `@Qualifier` selects a specific Bean.
- Spring manages object creation and dependency wiring.
