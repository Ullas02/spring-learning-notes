# @GetMapping vs @PostMapping

## 🎯 What are they?

`@GetMapping` and `@PostMapping` are specialized Spring MVC annotations that map HTTP **GET** and **POST** requests to controller methods.

They are shortcuts for `@RequestMapping` with a specific HTTP method.

Example:

```java
@GetMapping("/students")
```

is equivalent to:

```java
@RequestMapping(
    value = "/students",
    method = RequestMethod.GET
)
```

Similarly,

```java
@PostMapping("/students")
```

is equivalent to:

```java
@RequestMapping(
    value = "/students",
    method = RequestMethod.POST
)
```

---

## ❓ Why do we need different HTTP methods?

HTTP methods describe **the intention of the request**, not just the URL.

For example:

```
GET /students
```

means:

> "Show me the students."

Whereas:

```
POST /students
```

means:

> "Create a new student."

Both use the same URL, but they perform different operations.

---

## ⚙️ GET Request

### Purpose

Retrieve information.

Examples:

```
GET /students

GET /employees

GET /products
```

Characteristics:

- Reads data
- Should not modify data
- Safe to repeat
- Can be bookmarked
- Can be cached

Example:

```java
@GetMapping("/students")
public String students() {
    return "students";
}
```

---

## ⚙️ POST Request

### Purpose

Submit data to the server.

Examples:

```
POST /students

POST /login

POST /orders
```

Characteristics:

- Creates or submits data
- May change application state
- Usually sends data in the request body
- Not cached by browsers
- Should not be repeated accidentally

Example:

```java
@PostMapping("/students")
public String saveStudent() {

    // Save student

    return "success";
}
```

---

## 💻 Real-World Example

Imagine a student registration page.

### Step 1

User visits:

```
GET /students/register
```

Spring returns:

```
register.html
```

The browser displays the registration form.

---

### Step 2

The user fills in the form and clicks **Submit**.

The browser sends:

```
POST /students/register
```

Spring now executes another controller method to process the submitted data.

Notice:

Same URL.

Different HTTP method.

Different controller method.

---

## 💻 Example

```java
@Controller
@RequestMapping("/students")
public class StudentController {

    @GetMapping("/register")
    public String showForm() {
        return "register";
    }

    @PostMapping("/register")
    public String saveStudent() {

        // Save data

        return "success";
    }

}
```

This is a common pattern in Spring MVC applications.

---

## 📊 GET vs POST

| GET | POST |
|------|------|
| Retrieve data | Submit data |
| Safe | Changes state |
| Can be cached | Usually not cached |
| Can be bookmarked | Cannot be bookmarked meaningfully |
| Used for reading | Used for creating/submitting |

---

## ✅ Benefits

- Clearer code
- Matches HTTP semantics
- Easier maintenance
- Better REST compatibility
- Prevents accidental misuse of endpoints

---

## ⚡ Backend Engineer Tips

Choose the HTTP method based on **what the endpoint does**, not based on convenience.

Ask yourself:

- Is the client reading data? → `GET`
- Is the client creating or submitting data? → `POST`

Correct HTTP semantics improve API design and make your application easier for other developers to understand.

---

## ❌ Common Mistakes

- Using `GET` to insert or update data.
- Using `POST` when only reading data.
- Assuming different operations always require different URLs.
- Ignoring the meaning of HTTP methods.

---

## 📝 Quick Revision

- `@GetMapping` handles GET requests.
- `@PostMapping` handles POST requests.
- The same URL can have different methods.
- GET retrieves data.
- POST submits or creates data.
