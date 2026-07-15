# Spring Profiles and Environment

## 🎯 What are Spring Profiles?

Spring Profiles allow you to register different Beans or configurations depending on the environment in which the application is running.

Typical environments include:

- Development (dev)
- Testing (test)
- Production (prod)

Only the Beans that match the active profile are loaded into the Spring IoC Container.

---

## ❓ Why do we need Profiles?

Applications rarely use the same configuration everywhere.

For example:

| Environment | Database |
|-------------|----------|
| Development | Local PostgreSQL |
| Testing | Test Database |
| Production | Cloud PostgreSQL |

Instead of changing Java code before deployment, Spring activates the appropriate configuration automatically.

---

## ⚙️ How it Works

```
Application Starts
        │
        ▼
Active Profile = dev
        │
        ▼
Load Dev Beans
```

or

```
Application Starts
        │
        ▼
Active Profile = prod
        │
        ▼
Load Production Beans
```

---

## 💻 Example

```java
@Service
@Profile("dev")
public class DevEmailService {

}
```

```java
@Service
@Profile("prod")
public class ProdEmailService {

}
```

If the active profile is `dev`, only `DevEmailService` becomes a Spring Bean.

---

## ✅ Benefits

- Environment-specific configuration
- Safer deployments
- Cleaner code
- Easier testing

---

## ⚡ Backend Engineer Tips

Avoid writing code like:

```java
if(environment.equals("prod")) {
    ...
}
```

Instead, let Spring load the correct Bean using profiles.

---

## ❌ Common Mistakes

- Forgetting to activate a profile.
- Using profiles for business logic instead of environment configuration.
- Creating too many unnecessary profiles.

---

## 📝 Quick Revision

- Profiles separate environment-specific configuration.
- Only Beans matching the active profile are loaded.
- Common profiles are `dev`, `test`, and `prod`.
