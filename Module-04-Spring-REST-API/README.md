# Module 04 - REST API

## 📖 Module Overview

This module introduced RESTful web service development using Spring Boot. It covered REST principles, endpoint design, request/response handling, validation, exception handling, HTTP status codes, API versioning, and automatic API documentation.

Unlike Spring MVC (Module 3), this module focused on building APIs that exchange JSON rather than rendering HTML views.

---

## 📚 Topics Covered

1. What is REST?
2. REST Architectural Constraints
3. REST vs SOAP
4. HTTP Methods
5. Designing RESTful URLs
6. `@RestController`
7. `@ResponseBody`
8. Returning JSON Responses
9. `ResponseEntity`
10. `@RequestBody`
11. CRUD REST API
12. HTTP Status Codes
13. Exception Handling
14. Validation with `@Valid`
15. Validation Error Handling
16. REST API Versioning
17. OpenAPI / Swagger
18. REST API Mini Project

---

## 📂 Repository Structure

```text
Module-04-REST-API/
├── README.md
├── 01-What-is-REST.md
├── 02-REST-Architectural-Constraints.md
├── 03-REST-vs-SOAP.md
├── 04-HTTP-Methods.md
├── 05-Designing-RESTful-URLs.md
├── 06-RestController.md
├── 07-ResponseBody.md
├── 08-Returning-JSON-Responses.md
├── 09-ResponseEntity.md
├── 10-RequestBody.md
├── 11-CRUD-REST-API.md
├── 12-HTTP-Status-Codes.md
├── 13-Exception-Handling.md
├── 14-Validation-with-Valid.md
├── 15-Validation-Error-Handling.md
├── 16-REST-API-Versioning.md
├── 17-REST-API-Documentation-OpenAPI-Swagger.md
└── 18-REST-API-Mini-Project.md
```

---

## 🛠 Skills Learned

- Design RESTful APIs
- Build CRUD endpoints
- Handle JSON requests and responses
- Use `ResponseEntity`
- Validate client input
- Handle exceptions globally
- Return appropriate HTTP status codes
- Version REST APIs
- Generate OpenAPI/Swagger documentation

---

## ⚡ Backend Best Practices

- Keep controllers thin.
- Put business logic in services.
- Validate input at the API boundary.
- Use centralized exception handling.
- Return meaningful HTTP status codes.
- Document APIs for consumers.
- Design APIs independently of the persistence layer.

---

## 🚀 Mini Project

**Product Management REST API**

Features:

- CRUD operations
- Validation
- Global exception handling
- OpenAPI documentation
- In-memory data storage

