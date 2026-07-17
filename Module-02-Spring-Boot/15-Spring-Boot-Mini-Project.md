# Spring Boot Mini Project

## 🎯 Objective

Build a simple Spring Boot application that combines the core concepts learned in Module 2.

This project focuses on Spring Boot features, not business logic.

---

## Features

- Spring Boot application
- REST endpoints
- External configuration
- Logging
- Actuator
- DevTools

---

## Endpoints

GET /

Returns a welcome message.

GET /about

Returns application information.

GET /config

Returns values loaded from `application.properties`.

---

## Configuration

Example:

```properties
server.port=8080

app.name=Spring Boot Mini Project
app.version=1.0
```

---

## Logging

Log every request received by the controller.

---

## Actuator

Expose:

- health
- info

---

## Skills Practiced

- Spring Boot setup
- Auto Configuration
- Starter Dependencies
- Configuration
- Logging
- Monitoring

---

## Learning Outcome

After completing this project you should be comfortable creating a basic Spring Boot application from scratch.
