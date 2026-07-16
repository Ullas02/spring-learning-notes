# Spring Profiles

## 🎯 What are Spring Profiles?

Spring Profiles allow a single Spring Boot application to run with different configurations for different environments.

Common environments include:

- Development (dev)
- Testing (test)
- Production (prod)

Instead of changing Java code, Spring Boot loads the configuration that matches the active profile.

---

## ❓ Why do we need Profiles?

Imagine your application in three environments.

### Development

- Local database
- Debug logging
- Port 8081

### Testing

- Test database
- Moderate logging
- Port 8082

### Production

- Production database
- Minimal logging
- Port 80 or 443

Without profiles, you'd constantly edit configuration files before every deployment.

Profiles eliminate that problem.

---

## ⚙️ How does it work?

Suppose you have these files:

```
src/main/resources/

application.properties
application-dev.properties
application-prod.properties
```

`application.properties` contains common configuration.

`application-dev.properties` contains development-specific settings.

`application-prod.properties` contains production-specific settings.

Spring Boot loads the common configuration first, then overrides it with the active profile's configuration.

---

## 💻 Example

### application.properties

```properties
spring.application.name=learning-demo
spring.profiles.active=dev
```

### application-dev.properties

```properties
server.port=8081
logging.level.root=DEBUG
```

### application-prod.properties

```properties
server.port=8080
logging.level.root=WARN
```

When the active profile is `dev`, the application starts on port `8081`.

When the active profile is `prod`, it starts on port `8080`.

---

## 🌍 Real-World Example

A company deploys the same application:

- Developers → `dev`
- QA Team → `test`
- Production Servers → `prod`

The application code is identical.

Only the configuration changes.

---

## ✅ Benefits

- One codebase
- Multiple environments
- Easier deployments
- Cleaner configuration
- Reduced deployment mistakes

---

## ⚡ Backend Engineer Tips

Avoid creating separate code branches for development and production behavior.

Keep one codebase and let Profiles control environment-specific configuration.

---

## ❌ Common Mistakes

- Committing production secrets to Git.
- Forgetting which profile is active.
- Putting all configuration into one large file.
- Using profiles to change business logic instead of environment settings.

---

## 📝 Quick Revision

- Profiles separate environment-specific configuration.
- `application.properties` holds common settings.
- `application-{profile}.properties` overrides common settings.
- The active profile determines which configuration Spring Boot loads.
