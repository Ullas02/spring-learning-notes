# CRUD REST API

## 🎯 What is CRUD?

CRUD stands for:

- Create
- Read
- Update
- Delete

Almost every backend application performs these four operations.

Examples:

E-commerce

- Create Product
- Read Product
- Update Product
- Delete Product

Student Management

- Add Student
- View Student
- Edit Student
- Delete Student

Employee Management

- Add Employee
- View Employee
- Update Employee
- Delete Employee

---

## CRUD and HTTP Methods

| CRUD | HTTP Method |
|-------|-------------|
| Create | POST |
| Read | GET |
| Update | PUT / PATCH |
| Delete | DELETE |

---

## 🏗 Architecture

Even though we don't have a database yet, we'll use a production-style structure.

```
Client

↓

Controller

↓

Service

↓

In-Memory List
```

Later this becomes:

```
Client

↓

Controller

↓

Service

↓

Repository

↓

Database
```

Notice that only the Service implementation changes.

The Controller remains almost identical.

---

## API Design

| Method | URL | Purpose |
|---------|-----|----------|
| GET | /products | Get all products |
| GET | /products/{id} | Get one product |
| POST | /products | Create product |
| PUT | /products/{id} | Replace product |
| DELETE | /products/{id} | Delete product |

---

## Why a Service Layer?

A beginner often writes:

```
Controller

↓

Business Logic
```

This becomes difficult to maintain.

Instead:

```
Controller

↓

Service

↓

Repository
```

The controller only receives requests.

The service contains business logic.

---

## Why not connect directly to a database?

Because we're learning REST.

Adding a database now would mix two different concepts.

Module 5 will replace the in-memory list with Spring Data JPA.

The REST API itself will hardly change.

---

## ✅ Benefits

- Clean architecture
- Easy testing
- Easier maintenance
- Scalable design
- Ready for database integration

---

## ⚡ Backend Engineer Tips

Always design your REST API independently of your database.

The client should never know:

- which database you use
- how tables are structured
- whether data comes from MySQL, PostgreSQL, MongoDB, or an in-memory collection

The API contract should remain stable even if the storage implementation changes.

---

## ❌ Common Mistakes

- Putting business logic inside controllers.
- Skipping the service layer.
- Designing endpoints around database tables instead of business resources.
- Returning inconsistent responses.

---

## 📝 Quick Revision

- CRUD = Create, Read, Update, Delete.
- REST maps CRUD operations to HTTP methods.
- Keep controllers thin.
- Put business logic in services.
- Build APIs independently of database technology.
