# 🧾 types/ (clients domain)

This folder contains **clients TypeScript types and interfaces**, that are specific to clients domain.

These types are **not derived from Zod** and are not responsible for validation.

---

## 📁 Recommended structure

```
types/
├── client.ts          # Client entity type
├── api.ts             # Generic API response types
├── date.ts            # Date formatting / range
├── uuid.ts            # UUID types or utilities
```

---

## ✅ Best practices

| ✅ Do                                      | ❌ Don't                              |
|-------------------------------------------|---------------------------------------|
| Use for shared structural types           | Put Zod schemas here                  |
| Organize by entity or context             | Dump all types in `index.ts`          |
| Use PascalCase + descriptive names        | Use vague names like `Data`, `Item`   |
| Keep purely TS logic                      | Avoid logic or side effects here      |

---

## ✨ Naming conventions

- `Client` – represents full client object
- `ApiResponse<T>` – standard API response wrapper
- `Paginated<T>` – paginated list response
- `SortDirection` – enum type

---

## 🧠 Example

```ts
// types/client.ts

export type Client = {
  id: string;
  name: string;
  email: string;
  createdAt: Date;
};
```