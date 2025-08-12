# 🧠 domain/enums/ (clients domain)

This folder defines the **enumerations** used in the `clients` domain.

Enums represent a fixed set of possible values for a concept, ensuring type safety and improving code readability.
They are part of the **ubiquitous language** of the domain and should be descriptive, business-focused, and immutable.

---

## 📁 Example

```
domains/clients/domain/enums/
└── client-status.enum.ts
```

---

## ✅ Best practices

- Define **only** values that are part of the domain's business rules (avoid UI-specific enums here).
- Use `PascalCase` for enum names and `SCREAMING_SNAKE_CASE` for members.
- Group related enums into a single file only if they are strongly linked; otherwise, create separate files.
- Keep enums **pure** — no logic, no functions, no external imports.
- Use enums in **entities, value objects, and services** to enforce business constraints.

---

## 🧠 Example

```ts
export enum ClientStatus {
  ACTIVE = 'ACTIVE',
  INACTIVE = 'INACTIVE',
  SUSPENDED = 'SUSPENDED',
}
```