# Designing RESTful URLs

## 🎯 What is it?

A RESTful URL identifies a **resource**, not an action.

Think of a URL as the **address of a resource**.

The **HTTP method** tells the server what action to perform on that resource.

For example:

GET /employees

means:

"Retrieve the employees resource."

The URL identifies **what**, while the HTTP method identifies **how**.

---

## ❓ Why do we need good URL design?

Imagine two APIs.

API 1

GET /getEmployees

POST /createEmployee

POST /deleteEmployee

POST /updateEmployee

API 2

GET /employees

POST /employees

PUT /employees/{id}

DELETE /employees/{id}

Which one is easier to understand?

Almost every backend engineer would choose API 2 because it follows standard REST conventions.

Good URL design:

- Improves readability
- Makes APIs predictable
- Reduces documentation needs
- Encourages consistency
- Simplifies frontend integration

---

## ⚙️ Resource-Based Design

REST focuses on **resources**, not operations.

Examples of resources:

- User
- Employee
- Product
- Book
- Order
- Student

URLs should therefore use **nouns**, not verbs.

Good:

/users

/orders

/products

Bad:

/getUsers

/createOrder

/deleteProduct

---

## 📚 Naming Conventions

### Use plural nouns

Good

/users

/products

/orders

Why plural?

Because each URL represents a **collection** of resources.

A single resource is identified by its ID.

GET /users

↓

Collection

GET /users/10

↓

Single user

---

### Use lowercase letters

Good

/products

Bad

/Products

/ProductList

Lowercase URLs avoid inconsistencies across operating systems and servers.

---

### Use hyphens for multiple words

Good

/customer-orders

Bad

/customerOrders

/customer_orders

Hyphens improve readability.

---

### Avoid file extensions

Bad

/products.json

/products.xml

Instead, let the HTTP headers determine the response format.

---

## 💻 Common CRUD URL Patterns

Retrieve all employees

GET /employees

Retrieve employee by ID

GET /employees/15

Create employee

POST /employees

Replace employee

PUT /employees/15

Partially update employee

PATCH /employees/15

Delete employee

DELETE /employees/15

Notice that only the HTTP method changes.

The URL remains consistent.

---

## 🌍 Nested Resources

Sometimes resources belong to other resources.

Example:

A customer has multiple orders.

GET /customers/10/orders

Retrieve all orders for customer 10.

Retrieve one order

GET /customers/10/orders/5

This clearly expresses the relationship.

---

## ⚠️ URI vs URL (Brief)

A **URI (Uniform Resource Identifier)** identifies a resource.

A **URL (Uniform Resource Locator)** identifies both the resource and how to locate it.

In everyday backend development, developers often use "URL" and "URI" interchangeably, especially when discussing REST endpoints.

---

## ❌ Common Mistakes

### Using verbs

Bad

GET /getEmployees

POST /deleteEmployee

Good

GET /employees

DELETE /employees/{id}

---

### Exposing implementation details

Bad

/usersFromMysql

/usersTable

Clients should not know or care how data is stored.

---

### Inconsistent naming

Bad

/users

/product

/ordersList

Good

/users

/products

/orders

Consistency is more important than personal preference.

---

### Encoding actions in URLs

Bad

POST /approveLoan

Better

PATCH /loans/{id}

Request Body

{
  "status": "APPROVED"
}

The resource is being updated rather than performing an action.

---

## ✅ Benefits

- Predictable APIs
- Easier maintenance
- Better developer experience
- Improved readability
- Cleaner documentation
- Standardized design

---

## ⚡ Backend Engineer Tips

When designing an endpoint, ask:

"What is the resource?"

If your answer is a verb, you're probably designing it incorrectly.

Instead of:

/sendEmail

Think:

/emails

POST /emails

The action comes from the HTTP method.

---

## ❌ Common Mistakes

- Mixing singular and plural resources.
- Using verbs in URLs.
- Encoding business actions into endpoint names.
- Exposing database or technology details.
- Using inconsistent naming conventions.

---

## 📝 Quick Revision

- URLs identify resources.
- Use nouns, not verbs.
- Prefer plural resource names.
- Use lowercase letters.
- Use hyphens for multiple words.
- Keep URLs consistent.
- Let HTTP methods describe the action.
