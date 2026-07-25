# @RequestBody

## 🎯 What is it?

`@RequestBody` tells Spring:

> "Read the HTTP request body, convert it into a Java object, and pass it to this method."

Instead of manually reading JSON from the request, Spring performs the conversion automatically.

---

## ❓ Why do we need it?

Imagine a client wants to create a new product.

The client sends:

POST /products

```json
{
  "name": "Laptop",
  "price": 79999.99
}
```

Without `@RequestBody`, Spring doesn't know that this JSON should be converted into a `Product` object.

With `@RequestBody`, Spring automatically performs that conversion.

---

## ⚙️ How does it work?

Client sends JSON

↓

DispatcherServlet

↓

@RestController

↓

@RequestBody

↓

HttpMessageConverter

↓

Jackson

↓

Java Object

↓

Controller Method

---

## 💻 Example

```java
@PostMapping("/products")
public Product createProduct(
        @RequestBody Product product) {

    return product;

}
```

Client sends:

```json
{
  "id":1,
  "name":"Laptop",
  "price":79999.99
}
```

Spring automatically creates:

```java
Product product
```

with:

```text
id = 1

name = Laptop

price = 79999.99
```

---

## What is Deserialization?

Deserialization means:

```
JSON

↓

Java Object
```

Example:

JSON

```json
{
  "id":10,
  "name":"Keyboard",
  "price":2499.00
}
```

↓

Java

```java
new Product(
    10L,
    "Keyboard",
    2499.00
)
```

Jackson performs this conversion automatically.

---

## Serialization vs Deserialization

Serialization

```
Java Object

↓

JSON
```

Deserialization

```
JSON

↓

Java Object
```

Remember:

Response → Serialization

Request → Deserialization

---

## Request Processing Flow

```
Client

↓

POST /products

↓

JSON Request Body

↓

DispatcherServlet

↓

@RequestBody

↓

HttpMessageConverter

↓

Jackson

↓

Product Object

↓

Controller Method

↓

Business Logic

↓

Response
```

---

## Required Conditions

For successful deserialization:

- Valid JSON
- Matching Java fields
- Default constructor (or appropriate Jackson configuration)
- Getters and setters (or equivalent mechanisms such as records/Lombok)

---

## ✅ Benefits

- Automatic JSON conversion
- Less boilerplate code
- Cleaner controllers
- Easy frontend integration
- Standard REST development

---

## ⚡ Backend Engineer Tips

Think of `@RequestBody` as the **entry point** into your backend.

Almost every POST, PUT, and PATCH endpoint you'll build in production accepts data through `@RequestBody`.

---

## ❌ Common Mistakes

- Forgetting `@RequestBody`.
- Sending invalid JSON.
- Mismatched JSON property names and Java fields.
- Missing constructors or setters required for deserialization.
- Confusing request parameters with request bodies.

---

## 📝 Quick Revision

- `@RequestBody` converts JSON into Java objects.
- Jackson performs deserialization.
- POST requests commonly use `@RequestBody`.
- Request → JSON → Java Object.
