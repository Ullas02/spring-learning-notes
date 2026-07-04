# Problems Before Spring

## 🎯 What is it?

Before frameworks like Spring, developers manually managed object creation, configuration, transactions, and resources.

---

## ❓ Why do we need to understand this?

Knowing the problems helps us appreciate why Spring's features exist.

---

## ⚙️ Common Problems

### Tight Coupling

Classes created their own dependencies.

### Difficult Testing

Replacing real implementations with mocks was hard.

### Boilerplate Code

Developers repeatedly wrote setup code.

### Configuration Chaos

Large XML files or hardcoded settings became difficult to manage.

### Poor Maintainability

A small change often affected many classes.

---

## 💻 Example

```java
public class OrderService {

    private PaymentService paymentService = new PaymentService();

}
```

The dependency is fixed.

Changing it requires modifying the source code.

---

## ✅ Benefits of Solving These Problems

- Easier maintenance
- Better testing
- More flexible architecture
- Improved scalability

---

## ⚡ Backend Engineer Tips

Whenever you see `new` inside business logic, ask:

"Should this object be created here, or managed by Spring?"

---

## ❌ Common Mistakes

- Overusing object creation.
- Ignoring coupling.
- Mixing business logic with infrastructure code.

---

## 📝 Quick Revision

Spring reduces:

- Tight coupling
- Boilerplate
- Manual configuration
- Testing difficulties
