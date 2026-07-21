# @ModelAttribute

## 🎯 What is `@ModelAttribute`?

`@ModelAttribute` tells Spring MVC:

> "Take the incoming request data, create a Java object, populate its fields, and pass the object to my controller."

It works together with Spring's **Data Binding** mechanism.

```
Browser Form
      │
      ▼
HTTP Request
      │
      ▼
Spring Data Binder
      │
      ▼
Student Object
      │
      ▼
Controller
```

Instead of manually reading each form field, Spring creates the object for you.

---

## ❓ Why do we need `@ModelAttribute`?

Imagine a registration form with 15 fields.

Without `@ModelAttribute`, you would write:

```java
@PostMapping("/register")
public String register(
        @RequestParam String name,
        @RequestParam String department,
        @RequestParam String email,
        @RequestParam int age,
        @RequestParam String phone
        // ...10 more fields
) {

}
```

This quickly becomes difficult to read and maintain.

With `@ModelAttribute`:

```java
@PostMapping("/register")
public String register(
        @ModelAttribute Student student
) {

}
```

Spring automatically fills the `Student` object.

---

## ⚙️ How does it work?

### Step 1

The browser submits:

```
Name = Darvin

Department = CSE
```

---

### Step 2

Spring creates:

```java
Student student = new Student();
```

---

### Step 3

Spring calls:

```java
student.setName("Darvin");

student.setDepartment("CSE");
```

---

### Step 4

The completed object is passed into the controller.

---

## 💻 Example

```java
@PostMapping("/register")
public String registerStudent(
        @ModelAttribute Student student) {

    System.out.println(student.getName());

    System.out.println(student.getDepartment());

    return "success";
}
```

No manual extraction is required.

---

## 📌 Data Binding Flow

```
HTML Form

↓

name

department

↓

Spring

↓

setName()

setDepartment()

↓

Student Object

↓

Controller
```

---

## 📌 Matching Rules

Spring matches:

HTML field names

↓

Java property names

Example:

HTML

```html
<input th:field="*{name}">
```

Java

```java
private String name;
```

Spring uses the setter:

```java
setName(...)
```

---

## 🌍 Real-World Examples

- User Registration
- Employee Creation
- Product Creation
- Customer Profile Update
- Shipping Address Form

Almost every Spring MVC application uses `@ModelAttribute`.

---

## ✅ Benefits

- Less boilerplate
- Cleaner controllers
- Automatic object creation
- Automatic data binding
- Easy integration with validation

---

## ⚡ Backend Engineer Tips

Keep controller methods focused on request handling.

Business logic should still be delegated to the service layer.

Example:

```java
@PostMapping("/register")
public String register(
        @ModelAttribute Student student) {

    studentService.register(student);

    return "success";
}
```

---

## ❌ Common Mistakes

- Missing getters or setters.
- Missing no-argument constructor.
- Field names not matching Java properties.
- Expecting `@ModelAttribute` to perform validation automatically (validation is a separate step).

---

## 📝 Quick Revision

- `@ModelAttribute` binds request data to Java objects.
- Spring creates and populates the object automatically.
- Property names must match form field names.
- Commonly used for HTML form submissions.
