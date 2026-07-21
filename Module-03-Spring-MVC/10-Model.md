# Model

## 🎯 What is it?

The **Model** is an object used to transfer data from a controller to a view.

Think of it as a **container** that holds the data the view needs to display.

Example:

```
Controller

↓

Model

↓

View (Thymeleaf)

↓

Browser
```

The Model does **not** store data permanently.

It exists only for the current request.

---

## ❓ Why do we need the Model?

Suppose you want to display this page:

```
Student Profile

Name : Darvin

Age : 22

Department : CSE
```

The HTML page doesn't know these values by itself.

The controller must provide them.

That's where the Model comes in.

The controller places data into the Model, and the view reads it.

---

## ⚙️ How does it work?

Spring injects a `Model` object into your controller method.

Example:

```java
@GetMapping("/profile")
public String profile(Model model) {

}
```

You add values using:

```java
model.addAttribute("name", "Darvin");
```

The first argument is the **attribute name**.

The second argument is the **value**.

Spring makes this data available to the view.

---

## 💻 Example

```java
@GetMapping("/profile")
public String profile(Model model) {

    model.addAttribute("name", "Darvin");

    return "profile";
}
```

Flow:

```
Browser

↓

GET /profile

↓

Controller

↓

Model

↓

name = Darvin

↓

profile.html

↓

Browser
```

---

## 📌 Multiple Attributes

A Model can contain multiple pieces of data.

```java
@GetMapping("/profile")
public String profile(Model model) {

    model.addAttribute("name", "Darvin");
    model.addAttribute("age", 22);
    model.addAttribute("department", "CSE");

    return "profile";
}
```

The view can access all three values.

---

## 📌 What Can We Store?

The Model can store almost any Java object.

Examples:

```java
String

Integer

Boolean

Student

List<Student>

Map<String, Student>
```

Later in this module, you'll commonly pass lists of objects to display tables and collections.

---

## 🌍 Real-World Examples

An e-commerce application:

```java
model.addAttribute("products", productList);
```

An employee portal:

```java
model.addAttribute("employee", employee);
```

A banking application:

```java
model.addAttribute("account", account);
```

The Model carries the data needed to render the page.

---

## ✅ Benefits

- Separates data from presentation.
- Keeps controllers organized.
- Makes views reusable.
- Supports dynamic pages.
- Fits naturally into the MVC architecture.

---

## ⚡ Backend Engineer Tips

The Model should only transport data.

It should **not** contain business logic.

Controllers prepare the data.

Views display the data.

Services calculate the data.

Keeping these responsibilities separate leads to clean, maintainable applications.

---

## ❌ Common Mistakes

- Thinking the Model is a database.
- Using the Model to store application state.
- Placing business logic in the Model.
- Forgetting to add required attributes before returning the view.

---

## 📝 Quick Revision

- The Model transfers data from the controller to the view.
- Use `model.addAttribute()` to add data.
- The Model exists only for one request.
- It can hold simple values or complex Java objects.
- Views read data from the Model.
