# @ResponseBody

## 🎯 What is it?

`@ResponseBody` tells Spring:

> "Take the value returned by this method and write it directly into the HTTP response body."

Without `@ResponseBody`, Spring assumes the returned value is the **name of a view** (such as a Thymeleaf or JSP page).

With `@ResponseBody`, Spring treats the returned value as **response data**.

---

## ❓ Why do we need it?

Imagine the following controller:

```java
@Controller
public class HelloController {

    @GetMapping("/hello")
    public String hello() {
        return "Hello Spring";
    }

}
```

A beginner may expect:

```
Hello Spring
```

But that's **not** what Spring does.

Instead, Spring searches for a view named:

```
hello.html
```

or

```
hello.jsp
```

because `@Controller` is designed for Spring MVC applications that render web pages.

---

To return actual data, we use:

```java
@Controller
public class HelloController {

    @GetMapping("/hello")
    @ResponseBody
    public String hello() {
        return "Hello Spring";
    }

}
```

Now Spring writes:

```
Hello Spring
```

directly into the HTTP response body.

---

## ⚙️ How does it work?

When a request arrives:

```
Client
   │
   ▼
DispatcherServlet
   │
   ▼
Controller Method
   │
   ▼
@ResponseBody?
   │
   ├── No
   │     ▼
   │  Treat return value as View Name
   │
   └── Yes
         ▼
HttpMessageConverter
         ▼
HTTP Response Body
```

The presence of `@ResponseBody` completely changes how Spring interprets the returned value.

---

## 💻 Example 1

```java
@Controller
public class GreetingController {

    @GetMapping("/greeting")
    @ResponseBody
    public String greeting() {
        return "Welcome to Spring Boot";
    }

}
```

Request:

```
GET /greeting
```

Response:

```
Welcome to Spring Boot
```

---

## 💻 Example 2

Returning an object:

```java
@Controller
public class StudentController {

    @GetMapping("/student")
    @ResponseBody
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
  "course":"Computer Science"
}
```

using Jackson.

---

# @RestController Internally

Many developers think `@RestController` is a completely different annotation.

Internally, it is equivalent to:

```java
@Controller
@ResponseBody
public class StudentController {

}
```

In fact, `@RestController` is a **composed annotation** that combines both behaviors.

Conceptually:

```
@RestController

=

@Controller
+
@ResponseBody
```

This is why every method in a `@RestController` automatically returns response data.

---

## When should you use which?

### Use `@Controller`

When your application returns:

- HTML
- JSP
- Thymeleaf templates

Example:

```
Login Page

Dashboard

Home Page
```

---

### Use `@RestController`

When your application returns:

- JSON
- XML
- Plain text
- API responses

Example:

```
Mobile App

React Frontend

Angular Frontend

Public API
```

---

## 🏗 Behind the Scenes

After your controller returns an object:

```
Student Object
```

Spring chooses an appropriate `HttpMessageConverter`.

If the client accepts JSON:

```
MappingJackson2HttpMessageConverter
```

is used to produce:

```json
{
  "id":1,
  "name":"Alice"
}
```

This happens automatically—no manual serialization is required.

---

## ✅ Benefits

- Clean API development
- Automatic serialization
- Less boilerplate code
- Clear separation between MVC and REST
- Simplifies frontend-backend communication

---

## ⚡ Backend Engineer Tips

Always choose the controller type based on the application you're building.

A common pattern in large applications is:

```
@Controller

↓

Web Pages (Admin Portal)
```

and

```
@RestController

↓

REST APIs (Mobile App, React, Angular)
```

Both can exist in the same Spring Boot application if needed.

---

## ❌ Common Mistakes

- Forgetting `@ResponseBody` when using `@Controller`.
- Using `@Controller` for REST APIs unintentionally.
- Thinking `@RestController` and `@Controller` are interchangeable.
- Returning view names from a `@RestController`.

---

## 📝 Quick Revision

- `@ResponseBody` writes the returned value into the HTTP response body.
- Without it, `@Controller` treats returned strings as view names.
- `@RestController` is equivalent to `@Controller + @ResponseBody`.
- Spring automatically converts Java objects into JSON.
