# Validation in Spring MVC

## 🎯 What is Validation?

Validation is the process of checking whether incoming data meets predefined rules before the application processes it.

Example rules:

- Name cannot be empty.
- Email must have a valid format.
- Age must be between 18 and 60.
- Password must have a minimum length.

Validation helps ensure that only valid data enters your application.

---

## ❓ Why do we need Validation?

Imagine a registration form.

Without validation, users could submit:

```
Name:
(empty)

Email:
abc

Age:
-10
```

If this data reaches your database, it can cause incorrect records, application errors, or security problems.

Validation prevents such issues early in the request lifecycle.

---

## ⚙️ How does it work?

The validation process is:

```
Browser
      │
      ▼
HTML Form
      │
      ▼
Spring Data Binding
      │
      ▼
Validation
      │
      ├── Valid → Controller Logic
      │
      └── Invalid → Return Form with Errors
```

Validation happens **after data binding** but **before your business logic**.

---

## 💻 Example

```java
public class Student {

    @NotBlank
    private String name;

    @Email
    private String email;

    @Min(18)
    @Max(60)
    private int age;

}
```

These annotations define validation rules for the object's fields.

---

## 📌 Common Validation Annotations

| Annotation | Purpose |
|------------|---------|
| `@NotNull` | Value cannot be `null` |
| `@NotBlank` | String cannot be empty or whitespace |
| `@NotEmpty` | Collection or string cannot be empty |
| `@Size` | Restricts string/collection length |
| `@Email` | Valid email format |
| `@Min` | Minimum numeric value |
| `@Max` | Maximum numeric value |
| `@Pattern` | Matches a regular expression |

---

## 📌 Custom Messages

You can provide user-friendly messages.

```java
@NotBlank(message = "Name is required")
private String name;
```

Instead of a generic error, the user sees:

```
Name is required
```

---

## 🌍 Real-World Examples

- User Registration
- Checkout Forms
- Login
- Employee Creation
- Payment Details
- Customer Address Forms

Every production application validates incoming data.

---

## ✅ Benefits

- Prevents invalid data.
- Improves user experience.
- Protects business logic.
- Helps maintain database integrity.
- Reduces bugs caused by bad input.

---

## ⚡ Backend Engineer Tips

Validation belongs at the boundary of your application.

Validate data as soon as it enters the system so that downstream layers can work with trustworthy data.

---

## ❌ Common Mistakes

- Skipping validation.
- Relying only on client-side validation.
- Using unclear validation messages.
- Performing validation manually when standard annotations are sufficient.

---

## 📝 Quick Revision

- Validation checks incoming data.
- Use validation annotations on model fields.
- Validation occurs after data binding.
- Invalid data should be returned to the form with helpful error messages.
