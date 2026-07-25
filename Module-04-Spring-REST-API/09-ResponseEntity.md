# ResponseEntity

## 🎯 What is it?

`ResponseEntity` is a Spring class that represents an **entire HTTP response**.

Unlike returning only an object, `ResponseEntity` allows you to control:

- Response Body
- HTTP Status Code
- HTTP Headers

Think of it as a complete HTTP response wrapper.

---

## ❓ Why do we need it?

Suppose you return:

```java
@GetMapping("/product")
public Product getProduct() {
    return new Product(1L, "Laptop", 79999.99);
}
```

Spring automatically responds with:

```
HTTP/1.1 200 OK
```

You have no control over the status code.

But what if:

- Product created successfully?
- Product not found?
- Validation failed?
- Resource deleted?

Different situations require different HTTP status codes.

That's where `ResponseEntity` comes in.

---

## ⚙️ How does it work?

Instead of returning:

```java
return product;
```

You return:

```java
return ResponseEntity.ok(product);
```

Spring now understands:

- Body → product
- Status → 200 OK

---

# Basic Example

```java
@GetMapping("/product")
public ResponseEntity<Product> getProduct() {

    Product product = new Product(
            1L,
            "Laptop",
            79999.99
    );

    return ResponseEntity.ok(product);

}
```

Response

```
HTTP/1.1 200 OK
```

```json
{
  "id":1,
  "name":"Laptop",
  "price":79999.99
}
```

---

# Returning 201 Created

When creating a resource:

```java
@PostMapping("/products")
public ResponseEntity<Product> createProduct() {

    Product product = new Product(
            10L,
            "Monitor",
            15999.99
    );

    return ResponseEntity
            .status(HttpStatus.CREATED)
            .body(product);

}
```

Response

```
HTTP/1.1 201 Created
```

---

# Returning 204 No Content

Sometimes no response body is needed.

Example:

```java
@DeleteMapping("/products/{id}")
public ResponseEntity<Void> deleteProduct(
        @PathVariable Long id) {

    return ResponseEntity.noContent().build();

}
```

Response

```
HTTP/1.1 204 No Content
```

No JSON body is returned.

---

# Returning 404 Not Found

Example:

```java
@GetMapping("/products/{id}")
public ResponseEntity<Product> getProduct(
        @PathVariable Long id) {

    return ResponseEntity.notFound().build();

}
```

Response

```
HTTP/1.1 404 Not Found
```

---

# Returning Custom Headers

Headers contain additional information.

Example:

```java
@GetMapping("/status")
public ResponseEntity<String> status() {

    return ResponseEntity
            .ok()
            .header("Application-Version", "1.0.0")
            .header("Environment", "Development")
            .body("Application Running");

}
```

Response

Headers

```
Application-Version: 1.0.0

Environment: Development
```

Body

```
Application Running
```

---

## Common Factory Methods

```java
ResponseEntity.ok(body)
```

Returns:

```
200 OK
```

---

```java
ResponseEntity.status(HttpStatus.CREATED)
```

Returns:

```
201 Created
```

---

```java
ResponseEntity.noContent()
```

Returns:

```
204 No Content
```

---

```java
ResponseEntity.notFound()
```

Returns:

```
404 Not Found
```

---

```java
ResponseEntity.badRequest()
```

Returns:

```
400 Bad Request
```

---

## ✅ Benefits

- Full HTTP response control
- Better API design
- Clear communication with clients
- Industry standard
- Easier error handling

---

## ⚡ Backend Engineer Tips

A production REST API should use meaningful HTTP status codes.

Example:

```
200 OK

↓

Request succeeded.
```

```
201 Created

↓

New resource created.
```

```
404 Not Found

↓

Requested resource doesn't exist.
```

```
400 Bad Request

↓

Client sent invalid data.
```

Clients should understand the outcome simply by reading the HTTP status.

---

## ❌ Common Mistakes

- Returning 200 OK for every request.
- Returning a body with 204 No Content.
- Returning 500 Internal Server Error for client mistakes.
- Ignoring appropriate HTTP status codes.

---

## 📝 Quick Revision

- `ResponseEntity` represents the complete HTTP response.
- It controls body, headers, and status code.
- Use 201 for creation.
- Use 204 for successful deletion with no response body.
- Use 404 when a resource isn't found.
