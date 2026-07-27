# REST API Versioning

## 🎯 What is API Versioning?

API Versioning is the practice of maintaining multiple versions of an API so existing clients continue working while newer clients can use updated functionality.

Instead of replacing an existing API, we create a new version.

Example:

```
Version 1

GET /api/v1/products
```

```
Version 2

GET /api/v2/products
```

Both APIs can exist at the same time.

---

## ❓ Why do we need Versioning?

Imagine Version 1 returns:

```json
{
    "id":1,
    "name":"Laptop"
}
```

Months later, the business requires:

```json
{
    "id":1,
    "productName":"Laptop",
    "category":"Electronics"
}
```

If we simply change the response, every existing client expecting `"name"` will break.

Versioning allows us to introduce the new format without affecting older clients.

---

## Real-World Example

Suppose:

- Mobile App v1.0 is installed on thousands of devices.
- You release Backend API v2 tomorrow.
- Not every user updates the mobile app immediately.

If Backend v1 disappears, older mobile apps stop functioning.

Maintaining API versions ensures backward compatibility.

---

# Common Versioning Strategies

## 1. URI Versioning

Example:

```
/api/v1/products

/api/v2/products
```

### Advantages

- Easy to understand
- Easy to test
- Most common in Spring Boot
- Clearly visible

### Disadvantages

- Version appears in the URL

---

## 2. Query Parameter Versioning

Example:

```
/products?version=1

/products?version=2
```

### Advantages

- Same endpoint

### Disadvantages

- Less common
- Easy to overlook

---

## 3. Header Versioning

Example:

```
API-Version: 1
```

### Advantages

- Clean URLs

### Disadvantages

- Harder to test manually
- Less obvious

---

## 4. Media Type Versioning

Example:

```
Accept:
application/vnd.company.v1+json
```

### Advantages

- Very flexible

### Disadvantages

- More complex
- Usually adopted in larger systems

---

# Which Strategy Should You Learn First?

For most Spring Boot applications:

✅ URI Versioning

is the simplest and most widely used approach.

---

## Example

Version 1

```
GET /api/v1/products
```

returns

```json
{
    "id":1,
    "name":"Laptop"
}
```

Version 2

```
GET /api/v2/products
```

returns

```json
{
    "id":1,
    "productName":"Laptop",
    "category":"Electronics"
}
```

Both versions remain available.

---

## When Should You Create a New Version?

Create a new version when introducing a **breaking change**, such as:

- Renaming fields
- Removing fields
- Changing response formats
- Changing request formats
- Changing endpoint behavior in an incompatible way

Adding a new optional field usually does **not** require a new version.

---

## ✅ Benefits

- Backward compatibility
- Safer deployments
- Easier client migration
- Reduced production risk

---

## ⚡ Backend Engineer Tips

Version your API only when necessary.

Too many versions increase maintenance costs.

A good API design minimizes breaking changes, reducing the need for frequent versioning.

---

## ❌ Common Mistakes

- Changing an existing API without versioning.
- Maintaining too many obsolete versions.
- Versioning for every small enhancement.
- Removing old versions without notifying API consumers.

---

## 📝 Quick Revision

- API versioning prevents breaking existing clients.
- URI versioning is the most common approach in Spring Boot.
- Introduce a new version only for breaking changes.
- Multiple API versions can run simultaneously.
