# Module 03 - Spring MVC

## 📖 Module Overview

This module introduces Spring MVC, the web framework within the Spring ecosystem responsible for handling HTTP requests, processing user input, and rendering dynamic HTML views.

By the end of this module, we will be able to build traditional server-side web applications using Spring MVC and Thymeleaf while following clean architectural practices.

---

## 📚 Topics Covered

1. Introduction to Spring MVC
2. MVC Architecture
3. Spring MVC Request Lifecycle
4. Controllers (`@Controller`)
5. Request Mapping
6. `@GetMapping`
7. `@PostMapping`
8. `@PathVariable`
9. `@RequestParam`
10. `Model`
11. Passing Data from Controller to View
12. Displaying Dynamic Data using Thymeleaf
13. Forms & Data Binding
14. `@ModelAttribute`
15. Validation
16. Spring MVC Mini Project

---

## 📂 Repository Structure

Module-03-Spring-MVC/

```
README.md

01-Introduction-to-Spring-MVC.md
02-MVC-Architecture.md
03-Spring-MVC-Request-Lifecycle.md
04-Controllers.md
05-Request-Mapping.md
06-GetMapping-vs-PostMapping.md
07-Multiple-Request-Handlers.md
08-PathVariable.md
09-RequestParam.md
10-Model.md
11-Passing-Data-from-Controller-to-View.md
12-Displaying-Dynamic-Data-Using-Thymeleaf.md
13-Forms-and-Data-Binding.md
14-ModelAttribute.md
15-Validation.md
16-Spring-MVC-Mini-Project.md
```

---

## 💻 Mini Project

**Student Registration Portal**

Features:

- Registration form
- Thymeleaf templates
- Form binding
- Validation
- Success page

Technologies:

- Spring Boot
- Spring MVC
- Thymeleaf
- Jakarta Bean Validation

---

## 🎯 Skills Learned

After completing this module, we can:

- Build Spring MVC web applications.
- Handle HTTP GET and POST requests.
- Design controllers using Spring MVC annotations.
- Pass data between controllers and views using `Model`.
- Render dynamic HTML with Thymeleaf.
- Bind HTML forms to Java objects.
- Use `@ModelAttribute` for form submissions.
- Validate user input using Bean Validation.
- Display validation errors in Thymeleaf templates.
- Understand the complete MVC request lifecycle.

---

## ⚡ Backend Best Practices

- Keep controllers thin.
- Move business logic to the service layer.
- Validate all incoming user input.
- Keep presentation logic inside the view.
- Use meaningful request mappings.
- Follow the Single Responsibility Principle.
- Separate the web, business, and persistence layers.

---
