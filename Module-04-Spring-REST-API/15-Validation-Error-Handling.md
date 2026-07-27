# Validation Error Handling

## 🎯 What is Validation Error Handling?

When validation fails, Spring throws an exception before your controller method executes.

Instead of exposing Spring's default error format, we can intercept the exception and return our own structured response.

---

## ❓ Why Customize Validation Errors?

Suppose the client sends:

```json
{
    "name": "",
    "price": -100
}
```

Spring's default response contains a lot of framework-specific information.

While useful for debugging, it's usually too verbose for production APIs.

Instead, we can return:

```json
{
    "timestamp": "2026-07-27T10:30:15",
    "status": 400,
    "error": "Validation Failed",
    "errors": {
        "name": "Product name is required.",
        "price": "Price must be greater than zero."
    }
}
```

This response is:

- Easier to understand
- Easier for frontend applications to parse
- Consistent across the entire API

---

## Validation Flow

```
Client

↓

JSON Request

↓

@RequestBody

↓

@Valid

↓

Validation Fails

↓

MethodArgumentNotValidException

↓

@ControllerAdvice

↓

Custom JSON Response
```

---

## What is MethodArgumentNotValidException?

When an object annotated with `@Valid` fails validation, Spring throws:

```java
MethodArgumentNotValidException
```

This exception contains:

- Which fields failed validation
- The validation messages
- Additional metadata

We can extract only the information we want.

---

## Standard Error Response

A common production response contains:

- timestamp
- status
- error
- errors

Example:

```json
{
    "timestamp": "...",
    "status": 400,
    "error": "Validation Failed",
    "errors": {
        "name": "Product name is required.",
        "price": "Price must be greater than zero."
    }
}
```

---

## ✅ Benefits

- Consistent API responses
- Cleaner frontend integration
- Easier debugging
- Better API documentation

---

## ⚡ Backend Engineer Tips

Design one error format and use it everywhere.

Whether the error is:

- Validation
- Resource not found
- Unauthorized
- Server error

the response structure should remain consistent.

---

## ❌ Common Mistakes

- Returning Spring's default response directly in production.
- Returning different formats for different endpoints.
- Ignoring validation messages.
- Exposing unnecessary internal details.

---

## 📝 Quick Revision

- Validation failures throw `MethodArgumentNotValidException`.
- Handle it globally using `@ControllerAdvice`.
- Return a clean JSON structure.
- Keep error responses consistent across the application.
