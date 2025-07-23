# 📡 services/clients/

This folder contains **API fetch functions** for the `clients` domain.  
Each function handles a single HTTP operation (GET, POST, PUT, DELETE) and is used by hooks or UI logic.

---

## 📁 Example

```
ui/services/clients/
├── fetchClients.ts
├── createClient.ts
└── updateClient.ts
```

---

## ✅ Best practices

- Export pure async functions using `fetch` or `axios`
- Use typed inputs and outputs
- Do not include UI or state logic
- Co-locate by domain (no global fetcher pool)

---

## 🧠 Example

```ts
import { Client } from '@/types/client';

export async function fetchClients(): Promise<Client[]> {
  const res = await fetch('/api/clients');
  if (!res.ok) throw new Error('Failed to fetch clients');
  return res.json();
}
```