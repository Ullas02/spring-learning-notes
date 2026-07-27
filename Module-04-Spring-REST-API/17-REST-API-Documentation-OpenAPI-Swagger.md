# REST API Documentation using OpenAPI & Swagger

## 🎯 What is OpenAPI?

**OpenAPI** is a specification (standard) for describing REST APIs.

It defines:

- Available endpoints
- HTTP methods
- Request parameters
- Request body
- Response body
- HTTP status codes

Think of OpenAPI as the **blueprint** of your REST API.

---

## ❓ What is Swagger UI?

Swagger UI is a web application that reads an OpenAPI specification and generates an interactive documentation page.

Instead of reading a PDF or text document, developers can:

- Browse endpoints
- Read request/response details
- Execute API requests
- View responses

all from the browser.

---

## OpenAPI vs Swagger UI

| OpenAPI | Swagger UI |
|----------|------------|
| API specification | Interactive documentation |
| Describes APIs | Displays APIs |
| Machine-readable | Human-friendly |
| Standard | Visualization tool |

---

## Why do we need API Documentation?

Imagine joining a company with 200 REST endpoints.

Without documentation, you'd need to inspect controller code to understand:

- Available endpoints
- Request format
- Required fields
- Response format

Good documentation solves this problem.

---

## How does it work?

```
Controller

↓

Spring Boot

↓

OpenAPI

↓

Swagger UI

↓

Interactive Documentation
```

---

## Common Swagger URL

After running the application:

```
http://localhost:8080/swagger-ui/index.html
```

OpenAPI specification:

```
http://localhost:8080/v3/api-docs
```

---

## Common OpenAPI Annotations

### @Tag

Groups related endpoints.

```java
@Tag(name = "Products")
```

---

### @Operation

Describes an endpoint.

```java
@Operation(summary = "Get product by ID")
```

---

### @Parameter

Documents request parameters.

```java
@Parameter(description = "Product ID")
```

---

### @ApiResponse

Documents HTTP responses.

```java
@ApiResponse(responseCode = "200")
```

---

## ✅ Benefits

- Automatic documentation
- Interactive testing
- Easier frontend integration
- Better onboarding for new developers
- Improved API maintenance

---

## ⚡ Backend Engineer Tips

Treat your API documentation as part of the product.

Outdated documentation can be as harmful as no documentation.

---

## ❌ Common Mistakes

- Forgetting to update annotations after changing endpoints.
- Writing vague endpoint descriptions.
- Ignoring error responses in documentation.
- Assuming controller names are enough documentation.

---

## 📝 Quick Revision

- OpenAPI is the API specification.
- Swagger UI displays the specification.
- Documentation is generated automatically.
- Swagger UI allows browser-based API testing.
