# Controllers (@Controller)

## 🎯 What is it?

A Controller is a Spring-managed class responsible for receiving HTTP requests, coordinating the required work, and returning a response.

It acts as the entry point into your application.

Every browser request first reaches the DispatcherServlet, which forwards it to the appropriate controller method.

---

## ❓ Why do we need Controllers?

Without controllers, Spring would have no idea which Java code should execute when a user visits a URL.

For example:

```
GET /students
```

Who should handle this request?

The answer is:

A controller method mapped to `/students`.

Controllers provide a structured way to organize request-handling logic.

---

## ⚙️ How does it work?

A class becomes a controller by adding the `@Controller` annotation.

Example:

```java
@Controller
public class HomeController {

}
```

During application startup, Spring scans the project for classes annotated with `@Controller`.

Each controller is registered as a Spring Bean inside the IoC container.

When a request arrives, Spring finds the correct controller method and executes it.

---

## 💻 Example

```java
package com.example.springmvc.controller;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;

@Controller
public class HomeController {

    @GetMapping("/")
    public String home() {
        return "home";
    }

}
```

Flow:

```
Browser

↓

GET /

↓

DispatcherServlet

↓

HomeController.home()

↓

home.html

↓

Browser
```

---

## 📂 Recommended Project Structure

```
src/main/java
└── com.example.springmvc
    ├── controller
    │      ├── HomeController.java
    │      ├── StudentController.java
    │      └── AdminController.java
    │
    ├── service
    ├── repository
    ├── model
    └── config
```

Each controller should focus on one domain of your application.

---

## ✅ Benefits

- Centralized request handling
- Clear separation of concerns
- Easy testing
- Easy maintenance
- Better readability

---

## ⚡ Backend Engineer Tips

A good controller should:

- Receive requests
- Validate input
- Call a service
- Return a response

A controller should **not**:

- Execute SQL queries
- Contain business rules
- Perform heavy calculations

Controllers should remain thin.

---

## ❌ Common Mistakes

- Writing business logic inside controllers
- Accessing repositories directly from controllers
- Creating one huge controller for the entire application
- Returning database entities directly to views without considering the application's design

---

## 📝 Quick Revision

- `@Controller` marks a class as a Spring MVC controller.
- Controllers receive HTTP requests.
- Controllers delegate work to services.
- Controllers return views or responses.
- Keep controllers focused and lightweight.
