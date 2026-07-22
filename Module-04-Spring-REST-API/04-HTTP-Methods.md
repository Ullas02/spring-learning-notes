# HTTP Methods

## 🎯 What are HTTP Methods?

HTTP methods (also called **HTTP verbs**) tell the server **what action the client wants to perform on a resource**.

Think of a REST API as a restaurant.

The **URL** identifies the table (resource), while the **HTTP method** tells the waiter what action you want.

Example:

GET /employees

means:

"Show me all employees."

POST /employees

means:

"Create a new employee."

The same URL can perform different operations depending on the HTTP method.

---

## ❓ Why do we need different HTTP methods?

Imagine if every request used only POST.

The server would have to inspect the request body to determine whether the client wanted to read, update, or delete data.

Instead, HTTP provides standard methods so that:

- APIs are predictable.
- Clients know what to expect.
- Frameworks (like Spring Boot) can route requests correctly.
- Caching and browser behavior work as intended.

---

# GET

## Purpose

Retrieve data.

GET should **never modify server data**.

### Example

```
GET /employees
```

Returns:

```json
[
  {
    "id":1,
    "name":"Alice"
  },
  {
    "id":2,
    "name":"Bob"
  }
]
```

Retrieve one employee:

```
GET /employees/10
```

---

# POST

## Purpose

Create a new resource.

The client sends data to the server.

Example:

```
POST /employees
```

Request Body

```json
{
    "name":"Alice",
    "department":"IT"
}
```

Server Response

```json
{
    "id":101,
    "name":"Alice",
    "department":"IT"
}
```

---

# PUT

## Purpose

Replace an existing resource.

A PUT request typically sends the complete representation of the resource.

Example

```
PUT /employees/10
```

```json
{
    "name":"Alice",
    "department":"HR"
}
```

The resource is replaced with the supplied representation.

---

# PATCH

## Purpose

Update only specific fields.

Example

```
PATCH /employees/10
```

```json
{
    "department":"Finance"
}
```

Only the department changes.

Everything else remains unchanged.

---

# DELETE

## Purpose

Remove a resource.

Example

```
DELETE /employees/10
```

The employee is deleted.

---

# Safe Methods

A safe method **does not change server data**.

Safe:

- GET

Not Safe:

- POST
- PUT
- PATCH
- DELETE

Reading data should never have side effects.

---

# Idempotent Methods

A method is **idempotent** if making the same request multiple times produces the same final state.

Examples:

DELETE /employees/10

First request:

Employee deleted.

Second request:

Employee is already gone.

Final state:

Employee does not exist.

The final state remains the same.

Therefore DELETE is idempotent.

---

## Idempotency Table

| Method | Safe | Idempotent |
|---------|------|------------|
| GET | ✅ | ✅ |
| POST | ❌ | ❌ |
| PUT | ❌ | ✅ |
| PATCH | ❓ Depends on implementation |
| DELETE | ❌ | ✅ |

---

## Why isn't POST idempotent?

POST creates new resources.

Sending the same request twice may create two employees.

Example:

POST /employees

Request 1

Employee #101 created.

Request 2

Employee #102 created.

Different final state.

Therefore POST is **not idempotent**.

---

## 💻 Spring Boot Example

```java
@RestController
@RequestMapping("/employees")
public class EmployeeController {

    @GetMapping
    public String getEmployees() {
        return "All Employees";
    }

    @PostMapping
    public String createEmployee() {
        return "Employee Created";
    }

    @PutMapping("/{id}")
    public String updateEmployee(@PathVariable Long id) {
        return "Employee Updated : " + id;
    }

    @PatchMapping("/{id}")
    public String patchEmployee(@PathVariable Long id) {
        return "Employee Partially Updated : " + id;
    }

    @DeleteMapping("/{id}")
    public String deleteEmployee(@PathVariable Long id) {
        return "Employee Deleted : " + id;
    }
}
```

---

## ✅ Benefits

- Clear API design
- Predictable behavior
- Better caching
- Easier integration
- Standardized communication

---

## ⚡ Backend Engineer Tips

Choose the HTTP method based on the **operation**, not convenience.

For example:

❌ Don't use POST to delete a user.

✔️ Use DELETE.

Following HTTP semantics makes APIs easier for others to understand and use.

---

## ❌ Common Mistakes

- Using POST for every operation.
- Using GET to modify data.
- Confusing PUT and PATCH.
- Ignoring idempotency.
- Returning success for an operation that failed.

---

## 📝 Quick Revision

- GET → Read
- POST → Create
- PUT → Replace
- PATCH → Partial Update
- DELETE → Remove

GET is safe.

PUT and DELETE are idempotent.

POST is not idempotent.
