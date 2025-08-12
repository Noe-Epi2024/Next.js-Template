# 🧠 domain/factories/ (clients domain)

This folder contains **factory classes** responsible for creating fully-initialized domain entities or value objects.

Factories encapsulate the construction logic, ensuring that all **invariants** and **business rules** are respected at creation time.
They are especially useful when creating complex objects that require multiple steps, generated values, or defaults.

---

## 📁 Example

```
domains/clients/domain/factories/
└── client.factory.ts
```

---

## ✅ Best practices

- Use factories when entity creation involves **more than trivial assignments** (e.g., generating IDs, setting default statuses).
- Keep them **pure** and free from infrastructure code (no DB calls, no HTTP requests).
- Validate input parameters before creating an entity.
- Apply **domain rules** during object construction (e.g., default status is `ACTIVE`).
- Prefer **static methods** for simplicity, unless stateful configuration is required.

---

## 🧠 Example

```ts
export class ClientFactory {
  static create(params: {
    name: string
    email: string
  }): Client {
    const id = randomUUID()
    const status = ClientStatus.ACTIVE
    const createdAt = new Date()

    return new Client(
      id,
      params.name,
      params.email,
      status,
      createdAt,
    )
  }
}
```