# @Primary Annotation

## 🎯 What is `@Primary`?

`@Primary` tells Spring which Bean should be chosen by default when multiple Beans of the same type exist.

If no `@Qualifier` is specified, Spring injects the Bean marked with `@Primary`.

---

## ❓ Why do we need it?

Applications often have multiple implementations of the same interface.

Sometimes one implementation is used most of the time.

Instead of writing `@Qualifier` everywhere, we can mark that implementation as the default.

---

## ⚙️ How does it work?

When Spring finds multiple matching Beans:

1. It looks for a Bean marked with `@Primary`.
2. If exactly one exists, Spring injects it.
3. If no primary Bean exists, Spring throws a `NoUniqueBeanDefinitionException`.
4. If `@Qualifier` is present, it overrides `@Primary`.

---

## 💻 Example

```java
@Component
@Primary
public class UpiPayment implements PaymentGateway {

    @Override
    public void pay() {
        System.out.println("Payment using UPI");
    }
}
```

Now this works without `@Qualifier`:

```java
@Service
public class PaymentService {

    private final PaymentGateway paymentGateway;

    public PaymentService(PaymentGateway paymentGateway) {
        this.paymentGateway = paymentGateway;
    }
}
```

---

## ✅ Benefits

- Defines a default implementation.
- Reduces repeated use of `@Qualifier`.
- Keeps dependency injection clean.

---

## ⚡ Backend Engineer Tips

Use `@Primary` when one implementation is the default for most of the application.

Use `@Qualifier` only when a specific implementation is needed.

---

## ❌ Common Mistakes

- Marking multiple Beans as `@Primary`.
- Assuming `@Primary` overrides `@Qualifier`.
- Using `@Primary` when different implementations are needed in many places.

---

## 📝 Quick Revision

- `@Primary` defines the default Bean.
- `@Qualifier` selects a specific Bean.
- `@Qualifier` has higher priority than `@Primary`.
