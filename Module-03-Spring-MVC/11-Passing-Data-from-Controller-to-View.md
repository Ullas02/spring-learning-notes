# Passing Data from Controller to View

## 🎯 What is it?

Passing data from the Controller to the View means making backend data available to the HTML page so that it can be displayed to the user.

The Controller prepares the data.

The Model carries the data.

The View displays the data.

```
Controller
      │
      ▼
Model
      │
      ▼
View
      │
      ▼
Browser
```

---

## ❓ Why do we need it?

Imagine a university portal.

When a student opens:

```
/profile
```

the page should display:

```
Student Name : Darvin

Department : CSE

CGPA : 8.75
```

These values are different for every student.

They cannot be hardcoded inside the HTML page.

Instead, the Controller sends them dynamically through the Model.

---

## ⚙️ How does it work?

### Step 1

The browser sends a request.

```
GET /profile
```

---

### Step 2

The Controller prepares the data.

```java
model.addAttribute("name", "Darvin");
model.addAttribute("department", "CSE");
```

---

### Step 3

The Controller returns a logical view.

```java
return "profile";
```

---

### Step 4

Spring forwards both:

- the Model
- the view name

to the ViewResolver.

---

### Step 5

The View receives the Model and displays the values.

---

## 💻 Example

```java
@GetMapping("/profile")
public String profile(Model model) {

    model.addAttribute("name", "Darvin");
    model.addAttribute("department", "CSE");
    model.addAttribute("cgpa", 8.75);

    return "profile";
}
```

The Controller doesn't generate HTML.

It only prepares data and chooses which view should render it.

---

## 📌 Passing Objects

Instead of individual values, you can pass a complete object.

```java
Student student = new Student();

student.setName("Darvin");
student.setDepartment("CSE");

model.addAttribute("student", student);
```

The View can later access the object's fields.

---

## 📌 Passing Collections

You can also pass collections.

```java
List<Student> students = List.of(
    new Student("John"),
    new Student("Alice"),
    new Student("Emma")
);

model.addAttribute("students", students);
```

Later, Thymeleaf can iterate over this list and display every student.

---

## 🌍 Real-World Examples

E-commerce

```java
model.addAttribute("products", productList);
```

Banking

```java
model.addAttribute("accounts", accounts);
```

Hospital

```java
model.addAttribute("patients", patientList);
```

Employee Portal

```java
model.addAttribute("employee", employee);
```

---

## ✅ Benefits

- Dynamic pages
- Reusable templates
- Separation of concerns
- Cleaner controllers
- Better maintainability

---

## ⚡ Backend Engineer Tips

Controllers should prepare data—not format it.

Good:

```
Controller
    ↓
Model
    ↓
View formats HTML
```

Avoid generating HTML inside Java code.

---

## ❌ Common Mistakes

- Hardcoding dynamic values in HTML.
- Returning HTML strings from MVC controllers.
- Mixing presentation logic with business logic.
- Forgetting to add required model attributes.

---

## 📝 Quick Revision

- Controllers prepare data.
- Model transports data.
- Views display data.
- Objects and collections can also be passed.
