# Forms & Data Binding

## 🎯 What is Data Binding?

Data Binding is the process of automatically mapping HTML form data to a Java object.

Instead of reading every form field manually, Spring populates the object's properties for you.

```
HTML Form
     │
     ▼
Spring MVC
     │
     ▼
Student Object
```

---

## ❓ Why do we need Data Binding?

Imagine a registration form:

- Name
- Department
- Email
- Phone
- Age

Without data binding, you would need to read each field separately.

With data binding, Spring creates and fills a `Student` object automatically.

This reduces boilerplate code and makes controllers much cleaner.

---

## ⚙️ How does it work?

### Step 1

Create a Java class.

```java
public class Student {

    private String name;
    private String department;
    private String email;

    // getters and setters
}
```

---

### Step 2

Create a form.

```html
<form>

    <input>

    <input>

</form>
```

---

### Step 3

Bind the form to the object.

```html
<form th:object="${student}">
```

---

### Step 4

Bind each field.

```html
<input th:field="*{name}">
```

Spring now knows that this input corresponds to the `name` property of the `Student` object.

---

## 💻 Example

```html
<form
        th:action="@{/students/register}"
        method="post"
        th:object="${student}">

    Name

    <input type="text"
           th:field="*{name}">

    Department

    <input type="text"
           th:field="*{department}">

    <button type="submit">
        Register
    </button>

</form>
```

When the form is submitted:

```
Student

↓

name

department
```

are automatically populated.

---

## 📌 th:object

```html
th:object="${student}"
```

This tells Thymeleaf:

"This form is associated with the `student` object from the Model."

Every `th:field` inside the form refers to this object.

---

## 📌 th:field

```html
<input th:field="*{name}">
```

This binds the input to:

```java
student.setName(...)
```

Likewise,

```html
<input th:field="*{department}">
```

maps to:

```java
student.setDepartment(...)
```

---

## 🌍 Real-World Examples

Registration forms

Employee creation

Product creation

Customer onboarding

Profile updates

Almost every enterprise web application uses data binding.

---

## ✅ Benefits

- Less boilerplate code
- Automatic object population
- Cleaner controllers
- Easier maintenance
- Seamless integration with validation

---

## ⚡ Backend Engineer Tips

Design your form-backed objects carefully.

Field names in the HTML should match the Java property names.

For example:

```java
private String email;
```

should correspond to:

```html
<input th:field="*{email}">
```

Spring relies on these property names during binding.

---

## ❌ Common Mistakes

- Missing getters or setters.
- Mismatched field names.
- Forgetting `th:object`.
- Using `name` attributes that don't correspond to object properties.

---

## 📝 Quick Revision

- Data Binding maps form fields to Java objects.
- `th:object` binds the entire form.
- `th:field` binds individual fields.
- Matching property names are essential.
