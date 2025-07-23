# 🎯 controllers/

This folder contains **controller functions** that orchestrate application logic:
- Validate inputs (typically using Zod)
- Call database access functions from `repositories/`
- Return typed responses (or errors)

Controllers are the glue between your API routes and your business logic.

---

## 📁 Recommended structure

```
controllers/
├── clients/
│   ├── createClientController.ts
│   ├── getClientsController.ts
│   └── updateClientController.ts
├── users/
│   ├── createUserController.ts
│   └── getUsersController.ts
```

---

## ✅ Best practices

| ✅ Do                                          | ❌ Don't                                |
|-----------------------------------------------|-----------------------------------------|
| Validate data using Zod schemas               | Skip input validation                   |
| Keep controllers thin and focused             | Add DB logic directly                   |
| Handle errors gracefully                      | Rely on implicit try/catch everywhere   |
| Organize controllers by domain                | Mix all use cases in a single file      |

---

## ✨ Naming conventions

- `createClientController.ts` – handles creation of a client
- `getClientsController.ts` – returns list of clients
- `updateClientController.ts` – updates a client entry

---

## 🧠 Example

```ts
// controllers/clients/createClientController.ts

import { parseOrThrow } from '@/validators/parseOrThrow';
import { CreateClientSchema } from '@/validators/clientValidator';
import { createClientInDb } from '@/repositories/clients/createClient';

export async function createClientController(body: unknown) {
  const data = parseOrThrow(body, CreateClientSchema);
  return await createClientInDb(data);
}
```