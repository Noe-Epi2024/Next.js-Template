# 📡 services/

This folder contains **API client functions** (aka fetchers) used on the client-side.  
Each file is responsible for sending a request to your backend routes (`/api/...`) and returning typed responses.

These services are domain-specific and must be organized accordingly.

---

## 📁 Recommended structure

```
services/
├── clients/
│   ├── fetchClients.ts
│   ├── createClient.ts
│   └── updateClient.ts
├── users/
│   ├── fetchUsers.ts
│   └── createUser.ts
```

---

## ✅ Best practices

| ✅ Do                                   | ❌ Don't                                 |
|----------------------------------------|------------------------------------------|
| Use `fetch` or wrapper (`fetcher.ts`)  | Call logic from inside components        |
| Return typed responses (e.g., `Client[]`) | Return `any`                          |
| Organize by domain                     | Mix all API calls at root level          |
| Keep side-effects here (not in UI)     | Mix with React logic                     |

---

## ✨ Naming conventions

- `fetchClients.ts` – GET all clients
- `createClient.ts` – POST new client
- `updateClient.ts` – PUT/PATCH existing client
- `deleteClient.ts` – DELETE a client

---

## 🧠 Example

```ts
// services/clients/fetchClients.ts

import { Client } from '@/types/client';

export async function fetchClients(): Promise<Client[]> {
  const res = await fetch('/api/clients');
  if (!res.ok) throw new Error('Failed to fetch clients');
  return res.json();
}
```