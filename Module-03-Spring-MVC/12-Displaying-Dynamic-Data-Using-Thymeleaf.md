# Displaying Dynamic Data using Thymeleaf

## 🎯 What is Thymeleaf?

Thymeleaf is a **server-side Java template engine**.

Its job is to generate HTML pages by combining:

- Static HTML
- Data from the Spring Model

Instead of writing values directly in HTML, Thymeleaf inserts them while rendering the page.

---

## ❓ Why do we need Thymeleaf?

Consider this HTML page:

```html
<h2>Welcome</h2>

<p>Name : ???</p>
```

HTML itself has no way of knowing the user's name.

The controller knows it.

```java
model.addAttribute("name", "Darvin");
```

Thymeleaf bridges the gap between the controller and HTML.

```
Controller

↓

Model

↓

Thymeleaf

↓

Final HTML

↓

Browser
```

---

## ⚙️ How does it work?

### Controller

```java
@GetMapping("/profile")
public String profile(Model model) {

    model.addAttribute("name", "Darvin");

    return "profile";
}
```

The controller adds:

```
name = Darvin
```

to the Model.

---

### HTML Template

```html
<p th:text="${name}"></p>
```

When Thymeleaf processes this template, it replaces `${name}` with the value from the Model.

Final HTML sent to the browser:

```html
<p>Darvin</p>
```

The browser never sees `th:text` or `${name}`—it only receives the rendered HTML.

---

## 💻 Example

Controller:

```java
@GetMapping("/student")
public String student(Model model) {

    model.addAttribute("name", "Darvin");
    model.addAttribute("department", "CSE");

    return "student";
}
```

Template:

```html
<h2>Student Profile</h2>

<p>Name:
    <span th:text="${name}"></span>
</p>

<p>Department:
    <span th:text="${department}"></span>
</p>
```

Rendered HTML:

```html
<h2>Student Profile</h2>

<p>Name:
    <span>Darvin</span>
</p>

<p>Department:
    <span>CSE</span>
</p>
```

---

## 📌 Displaying Object Properties

Suppose the controller passes:

```java
Student student =
        new Student(
                "Darvin",
                "CSE",
                8.75
        );

model.addAttribute("student", student);
```

The template can access object properties:

```html
<p th:text="${student.name}"></p>

<p th:text="${student.department}"></p>

<p th:text="${student.cgpa}"></p>
```

Thymeleaf calls the object's getter methods internally.

For example:

```java
student.getName()
```

provides the value for:

```text
${student.name}
```

---

## 📌 Displaying Lists

Suppose the controller sends:

```java
List<Student> students = List.of(
    new Student("John", "CSE", 8.5),
    new Student("Alice", "ECE", 9.0)
);

model.addAttribute("students", students);
```

The template can iterate over the list:

```html
<tr th:each="student : ${students}">
    <td th:text="${student.name}"></td>
    <td th:text="${student.department}"></td>
</tr>
```

We'll study `th:each` in more detail later when we build tables.

---

## 🌍 Real-World Examples

E-commerce:

```text
Product Name

Price

Availability
```

Employee Portal:

```text
Employee Name

Department

Salary
```

Banking Dashboard:

```text
Account Number

Balance

Transactions
```

All these values come from the Model and are rendered by Thymeleaf.

---

## ✅ Benefits

- Dynamic HTML generation
- Clean separation of backend and frontend
- Natural HTML templates
- Easy integration with Spring MVC
- Supports loops, conditions, forms, and fragments

---

## ⚡ Backend Engineer Tips

Keep HTML focused on presentation.

The controller should prepare data.

The service should contain business logic.

Thymeleaf should only display data—not calculate it.

---

## ❌ Common Mistakes

- Forgetting to add attributes to the Model.
- Misspelling attribute names.
- Writing business logic in HTML templates.
- Expecting Thymeleaf expressions to work in static HTML files opened directly in a browser.

---

## 📝 Quick Revision

- Thymeleaf renders HTML using Model data.
- `th:text` displays values.
- `${...}` accesses Model attributes.
- Object properties are accessed with dot notation.
- Controllers prepare data; Thymeleaf displays it.
