# MVC Architecture

## 🎯 What is it?

MVC (Model-View-Controller) is an architectural pattern that divides a web application into three independent responsibilities.

Instead of putting everything in one class, MVC separates:

- Data
- Business Logic
- User Interface

This separation makes applications easier to understand, test, maintain, and scale.

---

## ❓ Why do we need it?

Imagine building an online shopping application without MVC.

A single Java class might:

- Receive the HTTP request
- Validate user input
- Calculate prices
- Save orders to the database
- Generate HTML
- Return the response

Soon, that class becomes thousands of lines long.

Problems include:

- Difficult debugging
- Poor readability
- Hard testing
- Tight coupling
- Difficult teamwork

MVC solves this by assigning one responsibility to each component.

---

# ⚙️ The Three Components

## 1. Model

The Model represents the application's data.

It carries information between different layers.

Examples:

- User
- Product
- Order
- Employee

Example:

```java
public class Student {

    private int id;
    private String name;

    // getters and setters
}
```

Think of the Model as the application's data container.

---

## 2. View

The View is responsible for presenting data to the user.

Examples:

- Thymeleaf template
- JSP page
- HTML page

Example:

```html
<h1>Welcome Darvin</h1>
```

The View should not contain business logic.

Its job is only to display data.

---

## 3. Controller

The Controller acts as the traffic manager.

Responsibilities:

- Receive HTTP requests
- Validate input
- Call the Service layer
- Receive results
- Pass data to the View
- Return the response

Example:

```java
@Controller
public class StudentController {

    @GetMapping("/student")
    public String studentPage() {
        return "student";
    }

}
```

Notice that the controller is coordinating work—it is not performing the business logic itself.

---

# 📊 Overall Flow

```text
User

↓

HTTP Request

↓

Controller

↓

Service

↓

Repository

↓

Database

↓

Repository

↓

Service

↓

Controller

↓

Model

↓

View

↓

HTTP Response

↓

User
```

Although MVC focuses on Model, View, and Controller, real Spring applications also include Service and Repository layers to keep responsibilities well separated.

---

## 💻 Real-World Example

Consider an Employee Management System.

Request:

```
GET /employees
```

Flow:

Controller

↓

EmployeeService

↓

EmployeeRepository

↓

Database

↓

Employee List

↓

Model

↓

employees.html

↓

Browser

Every component performs one clearly defined responsibility.

---

## ✅ Benefits

- Separation of concerns
- Easier debugging
- Better testing
- Reusable code
- Cleaner architecture
- Scalable applications
- Team-friendly development

---

## ⚡ Backend Engineer Tips

A good rule followed in production systems is:

- Controller → Handle HTTP
- Service → Business rules
- Repository → Database
- Model → Data
- View → Presentation

Never merge these responsibilities into one class.

Doing so makes the application harder to maintain and evolve.

---

## ❌ Common Mistakes

- Writing database code in Controllers
- Putting business logic inside Views
- Using Models for business operations
- Returning HTML directly from Controllers
- Creating "God classes" that handle everything

---

## 📝 Quick Revision

- MVC separates responsibilities.
- Model stores data.
- View displays data.
- Controller coordinates requests.
- Service contains business logic.
- Repository communicates with the database.
- Separation of concerns leads to maintainable applications.
