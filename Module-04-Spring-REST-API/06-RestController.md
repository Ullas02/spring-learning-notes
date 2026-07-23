# @RestController

## 🎯 What is it?

`@RestController` tells Spring Boot:

> "This class handles HTTP requests, and the return value of its methods should be written directly into the HTTP response body."

Instead of returning HTML pages (views), a REST controller typically returns:

- JSON
- XML (less common)
- Plain text
- Java objects (automatically converted to JSON)

It is the most commonly used annotation when building REST APIs with Spring Boot.

---

## ❓ Why do we need it?

Recall Module 3 (Spring MVC).

A normal MVC controller returns a **view name**.

Example:

```java
@Controller
public class HomeController {

    @GetMapping("/")
    public String home() {
        return "home";
    }
}
```

Spring looks for:

```
home.html
```

or

```
home.jsp
```

because the application is rendering a webpage.

---

REST APIs are different.

A mobile app doesn't want HTML.

A React frontend doesn't want JSP.

They want data.

Example:

```json
{
    "id":1,
    "name":"Alice"
}
```

So we need a controller that returns data instead of views.

That's exactly why `@RestController` exists.

---

## ⚙️ How does it work?

Suppose the client sends:

GET /employees

Spring Boot processes it as follows:

```
Client
   │
   ▼
DispatcherServlet
   │
   ▼
Find matching @RestController
   │
   ▼
Find matching @GetMapping
   │
   ▼
Execute method
   │
   ▼
Return Java Object/String
   │
   ▼
Convert response (usually JSON)
   │
   ▼
HTTP Response
```

Although `DispatcherServlet` is involved (from Spring MVC), in REST applications its job is to route requests to REST controllers instead of controllers returning views.

---

## 💻 Example 1

```java
@RestController
public class HelloController {

    @GetMapping("/hello")
    public String hello() {
        return "Hello Spring REST";
    }

}
```

Request:

```
GET /hello
```

Response:

```
Hello Spring REST
```

No HTML page is rendered.

---

## 💻 Example 2

```java
@RestController
@RequestMapping("/students")
public class StudentController {

    @GetMapping
    public Student getStudent() {

        return new Student(
                1,
                "Alice",
                "Computer Science"
        );

    }

}
```

Spring automatically converts:

```java
Student
```

↓

into

```json
{
  "id":1,
  "name":"Alice",
  "department":"Computer Science"
}
```

You don't manually convert Java objects into JSON.

Spring Boot does it automatically.

---

## 🏗 Behind the Scenes

When a request arrives:

1. Spring receives the HTTP request.
2. DispatcherServlet intercepts it.
3. Spring finds the correct controller.
4. Spring executes the mapped method.
5. The returned object is passed to an `HttpMessageConverter`.
6. The converter transforms the object into JSON.
7. JSON is sent back to the client.

We'll study `HttpMessageConverter` later in this module.

---

## ✅ Benefits

- Easy REST API development
- Automatic JSON conversion
- Clean code
- No manual serialization
- Perfect for frontend-backend communication

---

## ⚡ Backend Engineer Tips

In production projects:

```
Controller
↓

Service
↓

Repository
↓

Database
```

The controller should only:

- receive requests
- validate basic input
- delegate work to the service layer
- return responses

Business logic should not live inside controllers.

We'll follow this architecture throughout the remaining modules.

---

## ❌ Common Mistakes

- Writing business logic inside controllers.
- Returning HTML from REST APIs.
- Mixing MVC controllers and REST controllers without understanding the difference.
- Creating very large controller classes with dozens of unrelated endpoints.

---

## 📝 Quick Revision

- `@RestController` creates REST endpoints.
- Methods return data, not views.
- Java objects are automatically converted into JSON.
- DispatcherServlet routes requests to the correct controller.
- Controllers should remain thin and delegate business logic.
