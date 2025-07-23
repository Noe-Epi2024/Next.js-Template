# 🔧 utils/ (clients domain)

This folder contains **clients, pure utility functions** that are specific to clients domain.
They must not depend on a specific layer (UI, API, DB, etc.).

---

## 🎯 Purpose

- Factorize common functions
- Improve code readability and maintainability
- Avoid duplication of logic

---

## 📁 Typical examples

```
utils/
├── formatDate.ts       # Format a date based on locale
├── slugify.ts          # Convert a string into a slug
├── errorHandler.ts     # Centralized error handler
├── cn.ts               # Merge class names (e.g., Tailwind)
└── isValidEmail.ts     # Simple email validation (non-Zod)
```

---

## ✅ Best practices

| ✅ Do                                  | ❌ Don't                                  |
|----------------------------------------|------------------------------------------|
| Write pure, testable functions         | Tie functions to React or Prisma         |
| Avoid side effects                     | Avoid direct DB or DOM access            |
| Stay layer-agnostic (no API/UI logic)  | Avoid fetch, NextResponse, etc.          |
| Use clear names per utility            | Avoid vague files like `misc.ts`         |

---

## 🧠 Example

```ts
// utils/formatDate.ts

export function formatDate(date: Date): string {
  return date.toLocaleDateString('fr-FR', {
    year: 'numeric',
    month: 'long',
    day: 'numeric',
  });
}
```