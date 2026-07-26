# Exception Handling

## 🎯 What is Exception Handling?

Exception handling is the process of dealing with unexpected situations (errors) that occur while processing a request.

Instead of allowing the application to fail with an ugly stack trace or inconsistent response, we return a meaningful HTTP response to the client.

---

## ❓ Why do we need it?

Suppose a client requests:

GET /products/999

The product doesn't exist.

A beginner might write:

```java
if (product == null) {
    return ResponseEntity.notFound().build();
}
```

Now imagine 50 endpoints.

The same check appears everywhere.

This violates the **DRY (Don't Repeat Yourself)** principle.

Instead, let the service throw an exception.

---

## Before

```
Controller

↓

Check for null

↓

Return 404
```

## After

```
Controller

↓

Service

↓

Throw Exception

↓

Global Exception Handler

↓

404 Response
```

Controllers become much cleaner.

---

## Creating a Custom Exception

```java
public class ProductNotFoundException
        extends RuntimeException {

    public ProductNotFoundException(Long id) {
        super("Product with ID " + id + " was not found.");
    }

}
```

Why extend `RuntimeException`?

Spring automatically propagates unchecked exceptions, making them ideal for business errors like "Product not found."

---

## Throwing the Exception

Instead of:

```java
return null;
```

Use:

```java
throw new ProductNotFoundException(id);
```

The service now communicates the failure clearly.

---

## Handling Exceptions

Spring allows you to catch exceptions using:

```java
@ExceptionHandler
```

Example:

```java
@ExceptionHandler(ProductNotFoundException.class)
public ResponseEntity<String> handleProductNotFound(
        ProductNotFoundException ex) {

    return ResponseEntity
            .status(HttpStatus.NOT_FOUND)
            .body(ex.getMessage());

}
```

---

## Global Exception Handling

Rather than placing exception handlers inside every controller, create one global handler.

```java
@ControllerAdvice
public class GlobalExceptionHandler {

}
```

`@ControllerAdvice` applies to all controllers in the application.

---

## Returning Structured Error Responses

Instead of returning plain text:

```
Product with ID 999 was not found.
```

Return JSON.

Example:

```json
{
    "timestamp": "2026-07-26T10:15:30",
    "status": 404,
    "error": "Not Found",
    "message": "Product with ID 999 was not found."
}
```

This format is easier for frontend applications to process.

---

## ✅ Benefits

- Centralized error handling
- Cleaner controllers
- Reusable error logic
- Consistent API responses
- Easier maintenance

---

## ⚡ Backend Engineer Tips

Avoid returning `null` to indicate business failures.

Instead:

- Throw a meaningful exception.
- Let a global exception handler convert it into the appropriate HTTP response.

This keeps the business logic expressive and the controllers concise.

---

## ❌ Common Mistakes

- Returning `null` from services.
- Catching every exception inside controllers.
- Returning different error formats across endpoints.
- Exposing internal stack traces to clients.

---

## 📝 Quick Revision

- Throw exceptions from the service layer.
- Handle them centrally using `@ControllerAdvice`.
- Use `@ExceptionHandler` for specific exception types.
- Return consistent JSON error responses.
