# @Qualifier Annotation

## 🎯 What is `@Qualifier`?

`@Qualifier` is a Spring annotation used to specify **which Bean should be injected** when multiple Beans of the same type exist.

It removes ambiguity during dependency injection.

---

## ❓ Why do we need it?

Suppose an application has multiple implementations of the same interface.

Example:

- Credit Card Payment
- UPI Payment
- PayPal Payment

Spring knows all of them implement the same interface.

Without additional information, Spring cannot determine which one to inject.

---

## ⚙️ How does it work?

When Spring finds multiple matching Beans:

1. It detects ambiguity.
2. Throws an exception.
3. `@Qualifier` tells Spring exactly which Bean to inject.

---

## 💻 Example

```java
@Component
public class PaymentService {

    private final PaymentGateway paymentGateway;

    public PaymentService(
            @Qualifier("upiPayment")
            PaymentGateway paymentGateway) {

        this.paymentGateway = paymentGateway;
    }
}
```

Spring injects only the Bean named `upiPayment`.

---

## ✅ Benefits

- Removes dependency ambiguity.
- Makes dependency selection explicit.
- Supports multiple implementations cleanly.
- Commonly used in production applications.

---

## ⚡ Backend Engineer Tips

Use interfaces with multiple implementations and inject the required implementation using `@Qualifier`.

---

## ❌ Common Mistakes

- Forgetting to add `@Qualifier` when multiple Beans exist.
- Using incorrect Bean names.
- Depending directly on implementation classes instead of interfaces.

---

## 📝 Quick Revision

- `@Qualifier` selects a specific Bean.
- Used only when multiple matching Beans exist.
- Commonly combined with Constructor Injection.
