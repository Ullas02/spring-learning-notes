# Multiple Request Handlers & Best Practices

## 🎯 What is it?

As an application grows, a single controller handles multiple related requests.

Instead of creating one method for the entire application, we create **multiple request handlers**, where each method has a single responsibility.

Example:

```
StudentController

├── listStudents()
├── showStudent()
├── showRegistrationForm()
├── registerStudent()
├── updateStudent()
└── deleteStudent()
```

Each method handles one specific request.

---

## ❓ Why do we need multiple request handlers?

Imagine a Student Management System.

Users should be able to:

- View students
- Register students
- Edit students
- Delete students
- Search students

If everything were written in one method:

```java
public String processEverything() {

}
```

the code would quickly become difficult to read and maintain.

Instead, Spring encourages small, focused handler methods.

---

## ⚙️ How does it work?

Each request handler is mapped to a unique combination of:

- URL
- HTTP Method

Example:

```java
@GetMapping("/students")
public String listStudents() {
    return "students";
}

@GetMapping("/students/{id}")
public String studentDetails() {
    return "details";
}

@PostMapping("/students")
public String saveStudent() {
    return "success";
}
```

Although two methods refer to `/students`, Spring distinguishes them by both the URL pattern and the HTTP method.

---

## 💻 Example

```java
@Controller
@RequestMapping("/students")
public class StudentController {

    @GetMapping
    public String listStudents() {
        return "students";
    }

    @GetMapping("/register")
    public String showRegistrationForm() {
        return "register";
    }

    @PostMapping("/register")
    public String registerStudent() {
        return "success";
    }

    @GetMapping("/contact")
    public String contact() {
        return "contact";
    }
}
```

Each method has a clear purpose and is easy to understand.

---

## 📂 Recommended Organization

As your application grows, split controllers by business domain.

```
controller

├── HomeController
├── StudentController
├── EmployeeController
├── ProductController
├── OrderController
└── AuthController
```

Avoid placing unrelated features in the same controller.

---

## 🏗 Production Example

An e-commerce application may have:

```
OrderController

GET    /orders

GET    /orders/{id}

POST   /orders

PUT    /orders/{id}

DELETE /orders/{id}
```

All these operations belong to the **Order** domain, so they stay together in one controller.

---

## ✅ Best Practices

### 1. One Controller = One Domain

Good:

```
StudentController

EmployeeController

OrderController
```

Avoid:

```
MainController

AppController

EverythingController
```

---

### 2. One Method = One Responsibility

Good:

```java
listStudents()

registerStudent()

deleteStudent()
```

Avoid:

```java
processAllStudents()
```

---

### 3. Keep Controllers Thin

A controller should coordinate work, not perform it.

Good:

```java
@GetMapping("/students")
public String students() {

    studentService.getAllStudents();

    return "students";
}
```

Avoid:

```java
@GetMapping("/students")
public String students() {

    // Database query
    // Validation
    // Business calculations
    // Email sending
    // File creation

}
```

Those responsibilities belong to other layers.

---

### 4. Use Meaningful Method Names

Good:

```java
showRegistrationForm()

saveStudent()

deleteStudent()
```

Avoid:

```java
abc()

test()

method1()
```

Method names should describe what they do.

---

### 5. Follow URL Conventions

Good:

```
/students

/students/register

/orders

/employees
```

Avoid:

```
/page1

/data123

/test
```

Meaningful URLs make APIs easier to understand.

---

## ⚡ Backend Engineer Tips

Controllers are like receptionists.

They:

- Welcome requests.
- Verify basic information.
- Forward work to specialists (services).
- Return the final response.

They do **not** perform the specialized work themselves.

---

## ❌ Common Mistakes

- One controller for the whole application.
- Large controller methods.
- Database code inside controllers.
- Business logic inside controllers.
- Poor naming conventions.
- Mixing unrelated domains.

---

## 📝 Quick Revision

- One controller handles one domain.
- One handler method performs one task.
- Controllers should remain thin.
- Delegate business logic to services.
- Use meaningful URLs and method names.
