# 🧠 domain/types/ (clients domain)

This folder contains **TypeScript type definitions** and **interfaces** that are part of the `clients` domain model.

Types define the **shape of data** used within the domain layer, improving type safety, readability, and maintainability.
They should reflect **business concepts**, not infrastructure-specific formats (e.g., no raw DB schemas here).

---

## 📁 Example

```
domains/clients/domain/types/
└── clientList.types.ts
```

---

## ✅ Best practices

- Use **type aliases** or **interfaces** to model domain-level data structures.
- Keep types **pure** and independent from frameworks, ORMs, or API response formats.
- Group related types in the same file when they belong to the same concept.
- Use **PascalCase** for type and interface names.
- Do not mix **DTOs** (data transfer objects) — those belong in the `application` layer.

---

## 🧠 Example

```ts
export type ClientList = {
  clients: Client[]
  nextCursor: string | null
  total: number
}
```