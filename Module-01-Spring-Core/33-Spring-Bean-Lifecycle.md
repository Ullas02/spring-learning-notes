# Spring Bean Lifecycle

## 🎯 What is the Spring Bean Lifecycle?

The Spring Bean Lifecycle is the sequence of stages that a Bean goes through while it is managed by the Spring IoC Container.

From the moment Spring creates a Bean until it destroys it during application shutdown, the Bean passes through several well-defined phases.

---

## ❓ Why do we need to understand it?

Many resources require setup and cleanup, for example:

- Database connections
- Cache clients
- Message brokers
- File handlers
- Thread pools

Spring provides lifecycle hooks so that these resources can be initialized and released safely.

---

## ⚙️ Bean Lifecycle Stages

1. Bean Definition Loaded
2. Bean Instantiated
3. Dependencies Injected
4. Initialization
5. Bean Ready for Use
6. Bean Destruction

---

## 💻 Simplified Flow

```
Application Starts
        │
        ▼
Spring Scans Configuration
        │
        ▼
Creates Bean
        │
        ▼
Injects Dependencies
        │
        ▼
Initialization
        │
        ▼
Bean Ready
        │
        ▼
Application Runs
        │
        ▼
Application Stops
        │
        ▼
Bean Destroyed
```

---

## ✅ Benefits

- Proper resource initialization
- Safe resource cleanup
- Consistent object lifecycle
- Better application stability

---

## ⚡ Backend Engineer Tips

Keep constructors lightweight. Perform expensive setup (such as opening connections or loading configuration) during the initialization phase instead of inside the constructor.

---

## ❌ Common Mistakes

- Opening resources in the constructor.
- Forgetting to release resources during shutdown.
- Assuming Spring destroys every object you create with `new`.

---

## 📝 Quick Revision

- Spring manages the complete lifecycle of its Beans.
- A Bean is created, initialized, used, and eventually destroyed.
- Lifecycle callbacks let you execute code during initialization and destruction.
