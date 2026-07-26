# HTTP Status Codes

## 🎯 What are HTTP Status Codes?

An HTTP status code is a **3-digit number** returned by the server to indicate the result of a client's request.

Think of it as the server answering:

> "I understood your request. Here's what happened."

The response body contains the data, while the status code describes the outcome.

---

## ❓ Why do we need them?

Imagine every API always returned:

```
200 OK
```

Even when:

- A product doesn't exist.
- Invalid data is sent.
- The user isn't authenticated.

The client would have to inspect every response body to determine what happened.

HTTP status codes solve this problem by providing a standard way to communicate success or failure.

---

## ⚙️ Status Code Categories

| Range | Category | Meaning |
|--------|----------|---------|
| 1xx | Informational | Request received, processing continues |
| 2xx | Success | Request completed successfully |
| 3xx | Redirection | Client should take another action |
| 4xx | Client Error | The client sent an invalid request |
| 5xx | Server Error | The server failed to process a valid request |

In REST APIs, you'll primarily work with **2xx**, **4xx**, and **5xx**.

---

# Common Success Status Codes

## 200 OK

Use when:

- Fetching data
- Updating data successfully
- General successful operations

Example:

```http
GET /products/1
```

Response:

```
200 OK
```

---

## 201 Created

Use when a **new resource** is successfully created.

Example:

```http
POST /products
```

Response:

```
201 Created
```

---

## 204 No Content

Use when the operation succeeds but there is no response body.

Common example:

```http
DELETE /products/1
```

Response:

```
204 No Content
```

---

# Common Client Error Status Codes

## 400 Bad Request

The client sent an invalid request.

Examples:

- Invalid JSON
- Missing required fields
- Invalid query parameters

Example:

```json
{
    "price": "abc"
}
```

where `price` should be numeric.

---

## 401 Unauthorized

The client has **not authenticated**.

Example:

- Missing JWT token
- Invalid login credentials

We'll revisit this in **Spring Security**.

---

## 403 Forbidden

The client is authenticated but **doesn't have permission**.

Example:

- A normal user attempts to access an admin endpoint.

---

## 404 Not Found

The requested resource doesn't exist.

Example:

```http
GET /products/999
```

Response:

```
404 Not Found
```

---

## 405 Method Not Allowed

The endpoint exists, but the HTTP method is incorrect.

Example:

If the API supports:

```http
GET /products
```

and the client sends:

```http
PATCH /products
```

the server may respond with:

```
405 Method Not Allowed
```

---

# Common Server Error Status Codes

## 500 Internal Server Error

The server encountered an unexpected problem while processing the request.

Examples:

- Unhandled exception
- Database connection failure
- Programming error

Clients usually cannot fix a `500` error; it indicates a server-side issue.

---

# Quick Decision Guide

| Situation | Status Code |
|-----------|-------------|
| Data retrieved successfully | 200 OK |
| Resource created | 201 Created |
| Resource deleted | 204 No Content |
| Invalid client request | 400 Bad Request |
| Authentication required | 401 Unauthorized |
| Permission denied | 403 Forbidden |
| Resource not found | 404 Not Found |
| Unexpected server error | 500 Internal Server Error |

---

## ✅ Benefits

- Standard communication
- Easier frontend integration
- Better API documentation
- Simpler debugging
- Industry-standard API behavior

---

## ⚡ Backend Engineer Tips

Always choose the status code based on **the outcome**, not the endpoint.

For example:

```
GET /products/1
```

could return:

- 200 OK (found)
- 404 Not Found (doesn't exist)
- 500 Internal Server Error (unexpected server issue)

The same endpoint can legitimately return different status codes depending on the result.

---

## ❌ Common Mistakes

- Returning `200 OK` for every response.
- Returning `500 Internal Server Error` for client mistakes.
- Returning `404 Not Found` for validation errors.
- Ignoring the semantics of HTTP.

---

## 📝 Quick Revision

- Status codes describe the outcome of a request.
- Use the most specific status code possible.
- 2xx = Success.
- 4xx = Client error.
- 5xx = Server error.
