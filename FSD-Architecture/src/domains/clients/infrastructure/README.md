# 🏗️ infrastructure/ (clients domain)

This folder contains the **data access and side-effect logic** for the `clients` domain.  
It is where you implement any **calls to external systems**, like databases (Prisma), file storage, or third-party APIs.

---

## 📁 Typical structure

```
domains/
└── clients/
    └── infrastructure/
        ├── createClient.ts
        ├── getClients.ts
        ├── updateClient.ts
        └── deleteClient.ts
```

---

## ✅ Best practices

| ✅ Do                                           | ❌ Don't                                 |
|------------------------------------------------|------------------------------------------|
| Isolate side-effects from business logic       | Mix Prisma/DB calls inside application   |
| Keep infrastructure per domain                 | Share database functions globally        |
| Export named pure functions                    | Couple to specific framework components  |
| Let `application/` layer call this layer       | Skip layers and use infra directly in UI |

---

## ✨ Naming conventions

- `getClients.ts` – reads all clients from DB
- `createClient.ts` – inserts new client into DB
- `updateClient.ts` – updates client data
- `deleteClient.ts` – removes client

---

## 🧠 Example

```ts
// infrastructure/createClient.ts

import { prisma } from '@/db';
import { CreateClientDto } from '../types/clientDto';

export async function createClient(data: CreateClientDto) {
  return prisma.client.create({ data });
}
```

---

## ✅ Summary

- Owns all technical implementation (DB, external services)
- Keeps `application/` and `api/` layers clean
- Ensures domain encapsulation