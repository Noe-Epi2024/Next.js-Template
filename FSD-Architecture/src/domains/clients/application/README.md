# 🧠 application/ (clients domain)

This folder contains the **client-side application logic** of the `clients` domain.  
Typically, it includes **custom React hooks**, derived state, and UI-specific logic using libraries like **React Query**.

---

## 📁 Typical structure

```
domains/
└── clients/
    └── application/
        ├── useClients.ts
        ├── useCreateClient.ts
        └── useUpdateClient.ts
```

---

## ✅ Best practices

| ✅ Do                                     | ❌ Don't                                 |
|------------------------------------------|------------------------------------------|
| Use hooks to encapsulate domain logic    | Mix logic in components or pages         |
| Use naming like `useCreateClient`        | Use vague names like `useLogic`          |
| Use `react-query`/`swr` inside hooks     | Call fetch directly in the UI            |
| Co-locate logic with feature usage       | Split logic between global folders       |

---

## 🧠 Example

```ts
// application/useClients.ts

import { useQuery } from '@tanstack/react-query';
import { fetchClients } from '../api/fetchClients';

export function useClients() {
  return useQuery(['clients'], fetchClients);
}
```

---

## ✅ Summary

- React hooks that manage async data, derived state, or trigger logic
- Domain-specific, reusable, and UI-facing