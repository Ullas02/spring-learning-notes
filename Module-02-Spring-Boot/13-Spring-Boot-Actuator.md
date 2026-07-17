# Spring Boot Actuator

## 🎯 What is Spring Boot Actuator?

Spring Boot Actuator provides production-ready features for monitoring and managing a running Spring Boot application.

It exposes endpoints that report information about your application's health, configuration, metrics, and runtime state.

---

## ❓ Why do we need it?

Imagine your application is deployed to production.

Instead of asking:

- Is the application running?
- Is the database connected?
- What version is deployed?

Actuator provides endpoints that answer these questions.

This helps developers, DevOps engineers, and monitoring systems quickly understand the application's status.

---

## ⚙️ How does it work?

Add the Actuator starter dependency.

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

Spring Boot automatically configures Actuator endpoints.

This is another example of **Auto Configuration** in action.

---

## 💻 Common Endpoints

| Endpoint | Purpose |
|----------|---------|
| `/actuator` | Lists available endpoints |
| `/actuator/health` | Shows application health |
| `/actuator/info` | Displays application information |
| `/actuator/metrics` | Shows runtime metrics |
| `/actuator/env` | Displays environment properties |
| `/actuator/beans` | Lists Spring Beans |

---

## ⚙️ Exposing Endpoints

By default, only a small number of endpoints are exposed over HTTP.

To expose more:

```properties
management.endpoints.web.exposure.include=health,info
```

Or (for learning only):

```properties
management.endpoints.web.exposure.include=*
```

---

## 🌍 Real-World Example

A monitoring system periodically calls:

```
GET /actuator/health
```

If the response is:

```json
{
  "status": "UP"
}
```

the application is considered healthy.

If the response changes to:

```json
{
  "status": "DOWN"
}
```

an alert can be triggered.

---

## ✅ Benefits

- Production monitoring
- Health checks
- Metrics
- Diagnostics
- Integration with monitoring tools

---

## ⚡ Backend Engineer Tips

Expose only the endpoints you actually need.

Production environments should never expose all Actuator endpoints publicly.

---

## ❌ Common Mistakes

- Exposing every endpoint in production.
- Assuming Actuator replaces logging.
- Ignoring health checks during deployments.
- Exposing sensitive runtime information without security.

---

## 📝 Quick Revision

- Actuator monitors Spring Boot applications.
- It provides production-ready endpoints.
- Add it using `spring-boot-starter-actuator`.
- Expose only the required endpoints.
