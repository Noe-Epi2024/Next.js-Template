# 🗄️ repositories/

This folder contains all **data access functions**, responsible for interacting with the database layer (e.g., Prisma, PostgreSQL, etc.).

Repositories are organized by domain and expose pure, reusable functions to be used by your controllers.

---

## 📁 Recommended structure

```
repositories/
├── clients/
│   ├── createClient.ts
│   ├── getClients.ts
│   └── updateClient.ts
├── users/
│   ├── createUser.ts
│   └── getUsers.ts
```

Or grouped:

```
repositories/
├── clients.ts
├── users.ts
```

---

## ✅ Best practices

| ✅ Do                                        | ❌ Don't                                 |
|---------------------------------------------|------------------------------------------|
| Write one function per data access concern  | Include business logic here              |
| Keep repository functions pure              | Call validators or services inside       |
| Reuse these functions across controllers    | Duplicate DB logic across files          |
| Use meaningful names                        | Use vague names like `handler.ts`        |

---

## ✨ Naming conventions

- `createClient.ts` – inserts a new record
- `getClients.ts` – fetches multiple records
- `getClientById.ts` – fetches one record
- `updateClient.ts` – updates an entity
- `deleteClient.ts` – deletes an entity

---

## 🧠 Example

```ts
// repositories/clients/createClient.ts

import { prisma } from '@/db';
import { CreateClientDto } from '@/validators/clientValidator';

export async function createClientInDb(data: CreateClientDto) {
  return prisma.client.create({ data });
}
```