# Path Variables (`@PathVariable`)

## 🎯 What is it?

A **Path Variable** is a value embedded directly inside the URL path.

Instead of using a fixed URL, part of the URL becomes dynamic.

Example:

```
/students/101
```

Here,

```
101
```

is the path variable.

Spring automatically extracts this value and passes it to your controller method.

---

## ❓ Why do we need Path Variables?

Imagine a Student Management System.

Suppose you have 10,000 students.

Creating endpoints like:

```
/student1

/student2

/student3

...

/student10000
```

would obviously be impossible.

Instead, we create one dynamic URL:

```
/students/{id}
```

Now every student can be accessed using:

```
/students/1

/students/2

/students/100

/students/5000
```

One endpoint handles all IDs.

---

## ⚙️ How does it work?

Spring recognizes placeholders enclosed in curly braces.

Example:

```java
@GetMapping("/students/{id}")
```

The value inside the URL is injected into the method parameter using `@PathVariable`.

```java
@GetMapping("/students/{id}")
public String student(@PathVariable int id) {

    return "Student ID : " + id;
}
```

If the browser requests:

```
/students/101
```

Spring executes:

```java
student(101);
```

---

## 💻 Example

```java
@Controller
@RequestMapping("/students")
public class StudentController {

    @GetMapping("/{id}")
    @ResponseBody
    public String student(@PathVariable int id) {

        return "Student ID = " + id;

    }

}
```

Request:

```
GET /students/25
```

Response:

```
Student ID = 25
```

---

## 📌 Named Path Variables

The placeholder name and parameter name don't have to match.

Example:

```java
@GetMapping("/students/{studentId}")
@ResponseBody
public String student(
        @PathVariable("studentId") int id) {

    return "ID = " + id;

}
```

Spring maps:

```
studentId

↓

id
```

---

## 📌 Multiple Path Variables

Spring can extract multiple values.

```java
@GetMapping("/students/{studentId}/courses/{courseId}")
@ResponseBody
public String details(
        @PathVariable int studentId,
        @PathVariable int courseId) {

    return studentId + " " + courseId;

}
```

Request:

```
/students/15/courses/8
```

Extracted values:

```
studentId = 15

courseId = 8
```

---

## 🌍 Real-World Examples

```
GET /users/25

GET /orders/1001

GET /products/200

GET /employees/15
```

These URLs identify a **specific resource**.

---

## ✅ Benefits

- Clean URLs
- REST-friendly
- Easy routing
- Dynamic endpoints
- Better readability

---

## ⚡ Backend Engineer Tips

Use path variables when identifying **one specific resource**.

Examples:

```
Student ID

Employee ID

Order ID

Product ID
```

If the value identifies **which resource** the client wants, `@PathVariable` is usually the right choice.

---

## ❌ Common Mistakes

- Using path variables for optional filters.
- Forgetting `{}` in the URL mapping.
- Using incorrect data types.
- Confusing path variables with query parameters.

---

## 📝 Quick Revision

- Path variables are embedded in the URL.
- Use `{}` to define placeholders.
- `@PathVariable` extracts the value.
- Best used for resource identifiers.
