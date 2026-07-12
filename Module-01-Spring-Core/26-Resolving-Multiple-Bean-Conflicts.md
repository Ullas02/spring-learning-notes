# Resolving Multiple Bean Conflicts

## 🎯 What is a Bean Conflict?

A Bean conflict occurs when Spring finds **multiple Beans of the same type** but needs to inject only one.

Since Spring cannot guess which implementation you want, application startup fails.

---

## ❓ Why does it happen?

Suppose an interface has multiple implementations:

- UpiPayment
- CreditCardPayment
- PaypalPayment

When a class requests a `PaymentGateway`, Spring finds three matching Beans.

Without additional instructions, it cannot decide which one to inject.

---

## ⚙️ How can we resolve it?

Spring provides several strategies:

1. `@Qualifier`
2. `@Primary`
3. Inject the implementation class directly (generally not recommended)
4. Inject a collection of Beans (`List`, `Map`, etc.) when all implementations are needed

---

## 💻 Example

```java
@Service
public class PaymentService {

    private final PaymentGateway paymentGateway;

    public PaymentService(
            @Qualifier("upiPayment")
            PaymentGateway paymentGateway) {

        this.paymentGateway = paymentGateway;
    }
}
```

---

## ✅ Best Practices

- Program to interfaces.
- Use `@Primary` for the default implementation.
- Use `@Qualifier` for specific implementations.
- Keep dependencies explicit with Constructor Injection.

---

## ⚡ Backend Engineer Tips

Never inject a concrete implementation unless there is a strong design reason.

Prefer interface-based design to keep your application flexible and testable.

---

## ❌ Common Mistakes

- Injecting implementation classes everywhere.
- Forgetting `@Qualifier` when multiple Beans exist.
- Declaring multiple `@Primary` Beans of the same type.

---

## 📝 Quick Revision

- Multiple Beans can cause dependency conflicts.
- `@Qualifier` selects a specific Bean.
- `@Primary` defines the default Bean.
- Constructor Injection remains the preferred injection style.
