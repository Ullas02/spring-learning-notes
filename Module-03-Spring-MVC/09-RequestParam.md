# Request Parameters (`@RequestParam`)

## 🎯 What is it?

`@RequestParam` is used to extract **query parameters** from the URL.

A query parameter appears **after the `?` symbol** in a URL.

Example:

```
/students/search?name=Darvin
```

Here:

- URL Path → `/students/search`
- Query Parameter → `name=Darvin`

Spring automatically reads the parameter value and passes it to your controller method.

---

## ❓ Why do we need Request Parameters?

Not every request is asking for one specific resource.

Sometimes users want to:

- Search
- Filter
- Sort
- Paginate
- Customize results

For example:

```
/students/search?name=John
```

```
/products?category=Laptop
```

```
/orders?status=Pending
```

```
/employees?page=2
```

These values don't identify a specific resource—they modify how the server processes the request.

---

## ⚙️ How does it work?

Spring looks at the query string after the `?`.

Example:

```text
/students/search?name=Darvin
```

The controller:

```java
@GetMapping("/search")
@ResponseBody
public String searchStudent(
        @RequestParam String name) {

    return "Searching for: " + name;

}
```

Spring automatically extracts:

```
name = Darvin
```

and passes it to the method.

---

## 💻 Example

```java
@Controller
@RequestMapping("/students")
public class StudentController {

    @GetMapping("/search")
    @ResponseBody
    public String searchStudent(
            @RequestParam String name) {

        return "Searching for: " + name;

    }

}
```

Request:

```
GET /students/search?name=Alice
```

Response:

```
Searching for: Alice
```

---

## 📌 Multiple Request Parameters

A request can contain multiple query parameters.

Example URL:

```
/students/search?name=John&department=CSE
```

Controller:

```java
@GetMapping("/search")
@ResponseBody
public String search(
        @RequestParam String name,
        @RequestParam String department) {

    return name + " - " + department;

}
```

Extracted values:

```
name = John

department = CSE
```

---

## 📌 Optional Parameters

By default, `@RequestParam` is **required**.

If the parameter is missing:

```
/students/search
```

Spring throws an error because `name` was expected.

To make it optional:

```java
@GetMapping("/search")
@ResponseBody
public String search(
        @RequestParam(required = false)
        String name) {

    return "Name = " + name;

}
```

Now both requests are valid:

```
/students/search
```

```
/students/search?name=John
```

---

## 📌 Default Values

You can also provide a default value.

```java
@GetMapping("/search")
@ResponseBody
public String search(

    @RequestParam(defaultValue = "All")
    String department

) {

    return department;

}
```

Request:

```
/students/search
```

Response:

```
All
```

---

## 🌍 Real-World Examples

Search:

```
GET /products?keyword=laptop
```

Pagination:

```
GET /students?page=2
```

Sorting:

```
GET /employees?sort=name
```

Filtering:

```
GET /orders?status=Delivered
```

---

## ✅ Benefits

- Supports searching
- Supports filtering
- Supports pagination
- Supports sorting
- Flexible request handling

---

## ⚡ Backend Engineer Tips

Ask yourself:

"Is this value identifying a resource?"

If **Yes** → use `@PathVariable`

If **No**, and it modifies the request (search, filter, page, sort) → use `@RequestParam`.

---

## ❌ Common Mistakes

- Using query parameters for resource IDs.
- Forgetting that parameters are required by default.
- Confusing query parameters with path variables.
- Using unclear parameter names.

---

## 📝 Quick Revision

- Query parameters appear after `?`.
- `@RequestParam` extracts them.
- Parameters are required by default.
- `required = false` makes them optional.
- `defaultValue` provides a fallback value.
