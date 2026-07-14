# @Value Annotation

## 🎯 What is `@Value`?

`@Value` is a Spring annotation used to inject values into Spring-managed Beans.

These values can come from:

- Hardcoded strings
- Numbers
- Boolean values
- Properties files
- Environment variables
- Expressions (SpEL)

---

## ❓ Why do we need it?

Applications often contain configuration values such as:

- Application name
- Database URL
- API keys
- Email addresses
- Timeout values
- File locations

Instead of hardcoding these values in Java code, Spring allows them to be externalized.

---

## ⚙️ Syntax

```java
@Value("${application.name}")
private String applicationName;
```

Spring looks up the key `application.name` and injects its value.

---

## 💻 Example

```java
@Service
public class AppInfoService {

    @Value("${application.name}")
    private String applicationName;

    public void print() {
        System.out.println(applicationName);
    }
}
```

---

## ✅ Benefits

- Externalized configuration
- Easier maintenance
- Environment-specific configuration
- Cleaner code

---

## ⚡ Backend Engineer Tips

Never hardcode values such as database URLs, passwords, or API keys.

Keep them in configuration files or environment variables.

---

## ❌ Common Mistakes

- Misspelling property names.
- Forgetting to create the property.
- Hardcoding configuration values in Java classes.

---

## 📝 Quick Revision

- `@Value` injects configuration values.
- Values can come from properties files.
- External configuration is preferred over hardcoding.
