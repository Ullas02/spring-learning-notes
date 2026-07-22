# What is REST?

## 🎯 What is it?

REST (Representational State Transfer) is an architectural style for designing web APIs.

It was introduced by Roy Fielding in his 2000 Ph.D. dissertation.

REST is not a framework, library, or protocol. It is a set of architectural principles that help build scalable, maintainable, and loosely coupled web services.

In Spring Boot, when we build REST APIs, we are implementing these principles.

---

## ❓ Why do we need it?

Imagine an e-commerce application.

- Mobile App
- Web Application
- Admin Dashboard
- Third-party Partners

All of them need product data.

Instead of each application connecting directly to the database, they communicate with a backend API.

REST provides a standard way for different clients to communicate with the backend.

---

## 🌍 Real-world Example

Consider Amazon.

The mobile app requests:

GET /products/15

The backend returns:

```json
{
  "id": 15,
  "name": "Laptop",
  "price": 75000
}
```

The mobile app doesn't know how the backend stores the data.

It only communicates through HTTP requests.

This separation makes applications easier to maintain.

---

## ⚙️ How does it work?

A client sends an HTTP request.

↓

The server processes it.

↓

The server returns an HTTP response.

Usually in JSON format.

Example:

Client

GET /users/10

↓

Server

200 OK

```json
{
  "id":10,
  "name":"Alice"
}
```

---

## 📦 Resource-Oriented Design

REST focuses on Resources.

Examples:

- User
- Product
- Order
- Employee
- Student

Resources are identified using URLs.

Examples:

/users

/products

/orders

Notice that URLs represent nouns, not actions.

Good:

/products/10

Bad:

/getProductById

---

## 💻 Example

Retrieve all products

GET /products

Retrieve one product

GET /products/5

Create product

POST /products

Update product

PUT /products/5

Delete product

DELETE /products/5

---

## ✅ Benefits

- Simple
- Scalable
- Language Independent
- Platform Independent
- Uses standard HTTP
- Easy to integrate
- Widely adopted

---

## ⚡ Backend Engineer Tips

Think in terms of resources instead of database tables.

Design APIs for consumers (frontend, mobile, external clients), not for your internal implementation.

A good REST API hides implementation details while exposing a clean and consistent interface.

---

## ❌ Common Mistakes

- Using verbs in URLs
- Returning HTML instead of JSON for APIs
- Ignoring HTTP methods
- Treating REST as just CRUD
- Exposing database structure directly

---

## 📝 Quick Revision

- REST is an architectural style.
- APIs expose resources.
- Resources are identified by URLs.
- Clients communicate using HTTP.
- JSON is the most common response format.
- REST encourages loose coupling between client and server.
