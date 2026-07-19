# Introduction to Spring MVC

## 🎯 What is it?

Spring MVC is the web framework inside the Spring ecosystem that helps us build web applications by separating application logic from presentation logic.

MVC stands for:

- Model
- View
- Controller

It follows the Front Controller design pattern using the DispatcherServlet.

---

## ❓ Why do we need it?

Imagine building a website without any framework.

For every URL you would have to:

- Read the HTTP request
- Parse parameters
- Execute business logic
- Build HTML manually
- Send the HTTP response

As the application grows:

- Code becomes difficult to maintain.
- Business logic mixes with UI.
- Testing becomes harder.
- Developers work on the same files.

Spring MVC solves these problems by organizing responsibilities.

---

## ⚙️ How does it work?

A browser sends an HTTP request.

↓

DispatcherServlet receives it.

↓

The correct Controller is selected.

↓

Controller performs the required work.

↓

Data is placed inside the Model.

↓

A View renders the response.

↓

Browser receives the final output.

---

## 💻 Example

```java
@Controller
public class HomeController {

    @GetMapping("/")
    public String home() {
        return "home";
    }
}
```

Spring MVC automatically maps `/` to the `home()` method.

---

## ✅ Benefits

- Clean separation of concerns
- Easier testing
- Scalable architecture
- Reusable components
- Better maintainability
- Industry standard for Java web applications

---

## ⚡ Backend Engineer Tips

Do not think of Spring MVC as "a way to create web pages."

Think of it as the request-processing engine of your backend.

Every REST API in Spring Boot is built on top of Spring MVC.

Understanding Spring MVC deeply makes learning REST APIs much easier.

---

## ❌ Common Mistakes

- Confusing Spring MVC with Spring Boot
- Mixing business logic inside Controllers
- Treating Controllers as service classes
- Ignoring the request lifecycle

---

## 📝 Quick Revision

- MVC = Model + View + Controller
- DispatcherServlet is the Front Controller
- Controllers receive requests
- Models carry data
- Views display data
- Spring MVC organizes web applications cleanly
