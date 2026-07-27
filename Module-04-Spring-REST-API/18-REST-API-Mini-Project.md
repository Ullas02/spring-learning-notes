# REST API Mini Project

## 🎯 Project Goal

Build a Product Management REST API using Spring Boot.

The project should demonstrate the concepts learned throughout Module 4.

---

# Features

## Product Management

- Create Product
- View All Products
- View Product by ID
- Update Product
- Delete Product

---

# REST Endpoints

| Method | Endpoint | Purpose |
|---------|----------|----------|
| GET | /products | Get all products |
| GET | /products/{id} | Get product by ID |
| POST | /products | Create product |
| PUT | /products/{id} | Update product |
| DELETE | /products/{id} | Delete product |

---

# Validation

Validate:

- Product name
- Product price

Example:

```java
@NotBlank
private String name;

@Positive
private double price;
```

---

# Exception Handling

Use:

- ProductNotFoundException
- GlobalExceptionHandler

---

# HTTP Status Codes

Use:

- 200 OK
- 201 Created
- 204 No Content
- 400 Bad Request
- 404 Not Found

---

# Swagger

Document the API using:

- @Tag
- @Operation

---

# Architecture

```
Controller

↓

Service

↓

In-Memory List
```

Next module:

```
Controller

↓

Service

↓

Repository

↓

Database
```

---

# Backend Best Practices

- Constructor Injection
- Thin Controllers
- Business Logic inside Services
- Global Exception Handling
- Validation
- Meaningful HTTP Status Codes
- Consistent Error Responses

---

## 📝 Quick Revision

A production-style REST API should include:

- RESTful endpoints
- Layered architecture
- Validation
- Exception handling
- HTTP status codes
- API documentation
