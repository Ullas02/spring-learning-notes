# REST Architectural Constraints

## 🎯 What are they?

REST is defined by **six architectural constraints** proposed by Roy Fielding.

These constraints are what distinguish a true RESTful API from an API that merely uses HTTP.

The six constraints are:

1. Client-Server
2. Stateless
3. Cacheable
4. Uniform Interface
5. Layered System
6. Code on Demand (Optional)

---

## ❓ Why do we need them?

As applications grow, they face challenges such as:

- Millions of users
- Multiple client applications
- Frequent deployments
- High scalability requirements
- Distributed systems

The REST constraints provide a standardized way to build APIs that remain scalable, maintainable, and loosely coupled.

---

# 1. Client-Server

## What is it?

The client and server have separate responsibilities.

- **Client**: Handles the user interface and user interaction.
- **Server**: Handles business logic, validation, and data storage.

The client should not know how the server works internally, and the server should not depend on how the client is implemented.

### Example

A React web app and an Android app both call:

GET /products/15

Both receive the same JSON response, even though their user interfaces are completely different.

### Benefits

- Independent development
- Easier maintenance
- Multiple clients can use the same API

---

# 2. Stateless

## What is it?

Every request must contain **all the information** needed to process it.

The server should **not store client session state** between requests.

### Example

Correct:

GET /orders/25

Authorization: Bearer <JWT>

The server can process this request without needing information from previous requests.

Incorrect:

The server remembers that the user logged in earlier and depends on server-side session state to understand the current request.

### Benefits

- Easier horizontal scaling
- Better reliability
- Simpler load balancing

---

# 3. Cacheable

## What is it?

Responses should indicate whether they can be cached.

If data doesn't change often, clients or intermediaries can reuse the response instead of making another request.

### Example

Product categories change infrequently.

The server can include cache headers so clients reuse the response for a period of time.

### Benefits

- Faster responses
- Reduced server load
- Lower network usage

---

# 4. Uniform Interface

## What is it?

The API should follow consistent rules.

For example:

```
GET    /products
POST   /products
GET    /products/5
PUT    /products/5
DELETE /products/5
```

Developers can understand new APIs more quickly because the patterns are predictable.

### Benefits

- Easier to learn
- Consistent design
- Better developer experience

---

# 5. Layered System

## What is it?

A client should not know whether it is communicating directly with the application server or through intermediaries.

Examples of intermediaries include:

- API Gateway
- Reverse Proxy
- Load Balancer
- Cache Server

### Example

Client

↓

Load Balancer

↓

API Gateway

↓

Application Server

↓

Database

The client simply sends requests to the API endpoint without knowing the internal routing.

### Benefits

- Improved scalability
- Better security
- Easier infrastructure management

---

# 6. Code on Demand (Optional)

## What is it?

The server may send executable code to the client.

This is the only optional REST constraint.

### Example

A web server sends JavaScript that runs in the user's browser.

Modern REST APIs rarely rely on this constraint.

---

## 💻 Real-World Example

When you use a food delivery app:

- Mobile app → Client
- Backend service → Server
- JWT token → Stateless request
- Product catalog → Cacheable
- REST endpoints → Uniform Interface
- API Gateway → Layered System

Even though you don't see these components, they work together to provide a fast and scalable experience.

---

## ✅ Benefits

- Scalability
- Loose coupling
- Maintainability
- Better performance
- Independent client and server evolution
- Easier deployment

---

## ⚡ Backend Engineer Tips

When designing an API, ask yourself:

- Can any client consume this API?
- Does each request contain everything the server needs?
- Are my URLs consistent?
- Can frequently requested data be cached?
- Can this API scale behind a load balancer?

These questions naturally guide you toward RESTful design.

---

## ❌ Common Mistakes

- Treating REST as just CRUD over HTTP
- Storing client-specific state on the server unnecessarily
- Using inconsistent URL patterns
- Ignoring caching opportunities
- Designing APIs tightly coupled to a single frontend

---

## 📝 Quick Revision

- REST is defined by six constraints.
- Client and server have separate responsibilities.
- Every request should be self-contained.
- Cache responses when appropriate.
- Keep the API interface consistent.
- Clients shouldn't know about backend infrastructure.
- Code on Demand is optional and rarely used today.
