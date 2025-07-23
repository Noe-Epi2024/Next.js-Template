# 🌐 api/ (clients domain)

This folder contains **client-side fetch functions** that communicate with your `/api/clients` backend routes.

It acts as a thin layer between the client logic (`application/`) and your API routes (`app/api/clients/`).

---

## 📁 Typical structure

```
domains/
└── clients/
    └── api/
        ├── fetchClients.ts
        ├── createClient.ts
        └── updateClient.ts
```

---

## ✅ Best practices

| ✅ Do                                       | ❌ Don't                                   |
|--------------------------------------------|--------------------------------------------|
| Use typed request/response payloads        | Use `any`                                  |
| Call these functions from `application/`   | Call them directly in React components     |
| Co-locate by domain                        | Dump all fetch logic globally              |
| Separate mutation vs. query logic          | Combine everything in a single util        |

---

## 🧠 Example

```ts
// api/fetchClients.ts

import { Client } from '@/types/client';

export async function fetchClients(): Promise<Client[]> {
  const res = await fetch('/api/clients');
  if (!res.ok) throw new Error('Failed to fetch clients');
  return res.json();
}
```

---

## ✅ Summary

- Only responsible for sending/receiving HTTP requests
- Consumed by domain-specific `application/` hooks