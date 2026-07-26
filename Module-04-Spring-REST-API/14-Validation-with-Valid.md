# Validation with @Valid

## 🎯 What is Validation?

Validation is the process of checking whether incoming data satisfies predefined rules before it is processed.

For example, a product should not have:

- An empty name
- A negative price
- A missing required field

Instead of writing these checks manually in every controller, Spring Boot can perform them automatically.

---

## ❓ Why do we need Validation?

Imagine a client sends:

```json
{
    "name": "",
    "price": -500
}
```

Without validation:

```
Client

↓

Controller

↓

Service

↓

Invalid Data Stored
```

With validation:

```
Client

↓

Validation

↓

❌ Invalid Request Rejected

↓

Controller (never executed)
```

This protects your application from bad input.

---

## What is Bean Validation?

Bean Validation is a Java specification for validating objects.

Spring Boot integrates it seamlessly using:

- Jakarta Bean Validation
- Hibernate Validator (the default implementation)

When validation fails, Spring automatically returns an error response.

---

## What is @Valid?

`@Valid` tells Spring:

> "Validate this object before executing the controller method."

Example:

```java
@PostMapping("/products")
public ResponseEntity<Product> createProduct(
        @Valid @RequestBody Product product) {

    return ResponseEntity
            .status(HttpStatus.CREATED)
            .body(product);

}
```

If validation fails, the controller method is not executed.

---

# Common Validation Annotations

## @NotNull

Field must not be `null`.

```java
@NotNull
private Double price;
```

---

## @NotBlank

String must not be:

- null
- empty
- only whitespace

```java
@NotBlank
private String name;
```

---

## @Size

Restricts string length.

```java
@Size(min = 3, max = 50)
private String name;
```

---

## @Min

Minimum numeric value.

```java
@Min(1)
private int quantity;
```

---

## @Max

Maximum numeric value.

```java
@Max(100)
private int quantity;
```

---

## @Positive

Value must be greater than zero.

```java
@Positive
private double price;
```

---

## Validation Flow

```
Client

↓

JSON

↓

@RequestBody

↓

@Valid

↓

Validation Successful?

↓

Yes → Controller

↓

Service

↓

Response
```

If validation fails:

```
Client

↓

JSON

↓

@Valid

↓

Validation Failed

↓

400 Bad Request
```

---

## ✅ Benefits

- Cleaner controllers
- Less repetitive code
- Automatic validation
- Consistent error handling
- Better API reliability

---

## ⚡ Backend Engineer Tips

Keep validation close to the data it validates.

Instead of checking values inside controllers:

```java
if(product.getPrice() < 0){
    ...
}
```

place validation rules on the model:

```java
@Positive
private double price;
```

This makes validation reusable across your application.

---

## ❌ Common Mistakes

- Forgetting `@Valid`.
- Using `@NotNull` instead of `@NotBlank` for strings.
- Performing validation manually in every controller.
- Assuming validation happens automatically without annotations.

---

## 📝 Quick Revision

- Validation checks incoming data.
- `@Valid` triggers validation.
- Validation occurs before the controller method executes.
- Invalid requests usually return `400 Bad Request`.
