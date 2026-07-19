# Request Mapping (`@RequestMapping`)

## 🎯 What is it?

`@RequestMapping` is a Spring MVC annotation used to map an incoming HTTP request to a controller or a controller method.

It tells Spring:

> "When this URL is requested, execute this code."

Every request handled by Spring MVC is matched using some form of request mapping.

---

## ❓ Why do we need it?

Imagine your application has these URLs:

```
/
```

```
/students
```

```
/students/add
```

```
/students/delete
```

Without request mapping, Spring wouldn't know which Java method should handle each URL.

`@RequestMapping` creates the connection between URLs and controller methods.

---

## ⚙️ How does it work?

Spring scans every controller during application startup.

For every method annotated with `@RequestMapping`, it stores mapping information internally.

Example:

```java
@RequestMapping("/students")
public String students() {
    return "students";
}
```

When a request comes for:

```
GET /students
```

Spring finds the matching method and executes it.

---

# Method-Level Mapping

```java
@Controller
public class HomeController {

    @RequestMapping("/")
    public String home() {
        return "home";
    }

}
```

Flow:

```
GET /

↓

DispatcherServlet

↓

HomeController.home()

↓

home.html
```

---

# Class-Level Mapping

Instead of repeating the same URL prefix on every method, we can define it once at the class level.

Example:

```java
@Controller
@RequestMapping("/students")
public class StudentController {

    @RequestMapping("/list")
    public String listStudents() {
        return "students";
    }

    @RequestMapping("/add")
    public String addStudent() {
        return "addStudent";
    }

}
```

Generated URLs:

```
/students/list

/students/add
```

Spring combines:

```
Class Mapping

+

Method Mapping
```

to create the final URL.

---

# Request Methods

By default:

```java
@RequestMapping("/login")
```

accepts:

- GET
- POST
- PUT
- DELETE
- PATCH

and any other HTTP method.

If you want to restrict it:

```java
@RequestMapping(
    value = "/login",
    method = RequestMethod.GET
)
```

Only GET requests will be accepted.

Because this is verbose, Spring introduced specialized annotations:

- `@GetMapping`
- `@PostMapping`
- `@PutMapping`
- `@DeleteMapping`
- `@PatchMapping`

We'll study these next.

---

## 💻 Example

```java
@Controller
@RequestMapping("/student")
public class StudentController {

    @RequestMapping("/details")
    public String details() {
        return "details";
    }

}
```

Final URL:

```
/student/details
```

---

## ✅ Benefits

- Simple URL mapping
- Organized routing
- Supports class-level grouping
- Supports all HTTP methods
- Improves readability

---

## ⚡ Backend Engineer Tips

Use class-level `@RequestMapping` to group related endpoints.

Example:

```
/students/...

/employees/...

/products/...

/orders/...
```

This keeps controllers organized and scales well as your application grows.

---

## ❌ Common Mistakes

- Repeating the same URL prefix on every method.
- Creating one controller for unrelated features.
- Forgetting that class-level and method-level mappings are combined.
- Using generic URLs like `/page1` or `/test`.

Choose descriptive, resource-oriented URLs.

---

## 📝 Quick Revision

- `@RequestMapping` maps URLs to controller methods.
- It can be used on classes and methods.
- Class-level and method-level mappings combine.
- By default, it supports all HTTP methods.
- Specialized annotations like `@GetMapping` simplify common use cases.
