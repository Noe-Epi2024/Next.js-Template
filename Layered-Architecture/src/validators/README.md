# ✅ validators/

This folder contains all **data validation schemas**, primarily using **Zod**.

## 🎯 Purpose

To validate user input, HTTP request data (query, body, params), or any data entering the application.

Each file typically contains:
- One or more **Zod schemas** (`z.object(...)`)
- The corresponding **DTOs** derived via `z.infer<typeof ...>` to enable type-safe data flow between layers

---

## 📁 Recommended structure

```
validators/
└── clientValidator.ts  # Zod schema + DTOs
```

---

## ✅ Best practices

| ✅ Do                                        | ❌ Don't                                     |
|---------------------------------------------|----------------------------------------------|
| Use one file per domain (`clientValidator`) | Dump all schemas in one file                 |
| Use descriptive schema names                | Use generic names like `schema.ts`           |
| Infer DTOs directly from Zod schemas        | Manually duplicate types                     |
| Export both schema and DTO in one place     | Split schema and type into different folders |

---

## ✨ Naming conventions

- `CreateClientSchema` – schema to validate a create form
- `UpdateClientSchema` – partial schema for updates
- `ClientQuerySchema` – schema for filters, search, or pagination

---

## 🧠 Example

```ts
// clientValidator.ts
import { z } from 'zod';

export const CreateClientSchema = z.object({
  name: z.string().min(2),
  email: z.string().email(),
});

export type CreateClientDto = z.infer<typeof CreateClientSchema>;
```