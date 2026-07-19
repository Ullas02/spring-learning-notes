# Spring MVC Request Lifecycle

## 🎯 What is it?

The Spring MVC Request Lifecycle is the sequence of steps that occurs from the moment a client sends an HTTP request until it receives an HTTP response.

Understanding this lifecycle is one of the most important concepts in Spring MVC because every request—whether it returns an HTML page or a REST response—passes through this process.

---

## ❓ Why do we need it?

Imagine an application with hundreds of controllers and thousands of URLs.

When a request arrives:

- Which controller should handle it?
- How is the correct method selected?
- Who creates the controller object?
- How is data passed to the view?
- Who generates the final response?

Instead of every controller handling these responsibilities, Spring centralizes them through the **DispatcherServlet**.

This makes applications:
- Consistent
- Easier to maintain
- Easier to extend
- Easier to test

---

## ⚙️ Request Lifecycle

### Step 1 – Browser Sends Request

Example:

```
GET /students
```

The browser sends an HTTP request to your Spring Boot application.

---

### Step 2 – DispatcherServlet Receives the Request

The **DispatcherServlet** is called the **Front Controller**.

Every incoming request reaches it first.

It is responsible for coordinating the entire request-processing workflow.

It does **not** contain your business logic.

Instead, it delegates work to the appropriate Spring components.

---

### Step 3 – Handler Mapping Finds the Controller

Spring examines the request URL.

Example:

```
GET /students
```

It searches for a controller method such as:

```java
@GetMapping("/students")
public String students() {
    ...
}
```

This lookup is performed by **HandlerMapping**.

---

### Step 4 – Controller Executes

The controller method is invoked.

Example:

```java
@Controller
public class StudentController {

    @GetMapping("/students")
    public String students(Model model) {

        List<Student> students = studentService.getAllStudents();

        model.addAttribute("students", students);

        return "students";
    }

}
```

Notice the controller:

- receives the request
- calls the service
- prepares data
- returns the view name

It does **not** query the database directly.

---

### Step 5 – Service Layer Executes

The controller delegates business logic to a service.

```java
studentService.getAllStudents();
```

The service:

- validates business rules
- performs calculations
- coordinates operations
- calls repositories

---

### Step 6 – Repository Accesses Database

The repository communicates with the database.

```
Database

↓

StudentRepository

↓

StudentService
```

It retrieves the required data and returns it to the service.

---

### Step 7 – Model is Prepared

The controller stores data in the `Model`.

```java
model.addAttribute("students", students);
```

The Model is simply a container that carries data from the controller to the view.

---

### Step 8 – View Resolver Finds the View

The controller returns:

```java
return "students";
```

This is **not** the HTML file itself.

Spring's **ViewResolver** converts the logical view name into the actual template.

For example:

```
students

↓

students.html
```

---

### Step 9 – View Renders HTML

Thymeleaf receives the model data and generates the final HTML page.

Example:

```html
<h2>Students</h2>

<ul>
    <li>John</li>
    <li>Emma</li>
</ul>
```

---

### Step 10 – Response Returns to Browser

The generated HTML is sent back to the browser as the HTTP response.

The user now sees the page.

---

# Complete Lifecycle

```text
Browser
    │
    ▼
HTTP Request
    │
    ▼
DispatcherServlet
    │
    ▼
HandlerMapping
    │
    ▼
Controller
    │
    ▼
Service
    │
    ▼
Repository
    │
    ▼
Database
    │
    ▲
Repository
    │
    ▲
Service
    │
    ▲
Controller
    │
    ▼
Model
    │
    ▼
ViewResolver
    │
    ▼
View (Thymeleaf)
    │
    ▼
HTTP Response
    │
    ▼
Browser
```

---

## 💻 Example

```java
@GetMapping("/welcome")
public String welcome(Model model) {

    model.addAttribute("name", "Darvin");

    return "welcome";
}
```

Flow:

Browser

↓

DispatcherServlet

↓

Controller

↓

Model

↓

ViewResolver

↓

welcome.html

↓

Browser

---

## ✅ Benefits

- Centralized request handling
- Cleaner architecture
- Easy URL mapping
- Loose coupling
- Better maintainability
- Consistent request processing

---

## ⚡ Backend Engineer Tips

Think of the DispatcherServlet as an **orchestra conductor**.

It doesn't play every instrument itself.

Instead, it coordinates specialists:

- HandlerMapping finds the controller.
- Controller handles the request.
- Service applies business rules.
- Repository accesses data.
- ViewResolver locates the view.
- View renders the response.

Each component focuses on one responsibility.

---

## ❌ Common Mistakes

- Thinking the DispatcherServlet executes business logic
- Accessing the database directly from the controller
- Confusing the Model with database entities
- Returning HTML directly from controllers in MVC applications
- Assuming `return "students"` returns raw HTML

---

## 📝 Quick Revision

- Every request first reaches the DispatcherServlet.
- HandlerMapping locates the controller.
- Controller delegates work to the service.
- Service communicates with repositories.
- Repository accesses the database.
- Controller places data in the Model.
- ViewResolver finds the view.
- View renders the final response.
