# ✅ validators/ (clients domain)

This folder contains all **Zod validation schemas** related specifically to the `clients` domain.

These schemas define how client-related data should be validated when:
- Sending API requests
- Handling form submissions
- Calling backend controllers

---

## 📁 Typical structure

```
domains/
└── clients/
    └── validators/
        ├── createClientSchema.ts
        ├── updateClientSchema.ts
        └── filterClientSchema.ts
```

---

## ✅ Best practices

| ✅ Do                                        | ❌ Don't                                |
|---------------------------------------------|------------------------------------------|
| Use `z.object()` to validate inputs         | Skip validation in API calls             |
| Export `ZodSchema` + inferred DTO           | Manually write duplicate types           |
| Keep one schema per use case                | Merge unrelated logic into one file      |
| Co-locate with the domain, not globally     | Put all schemas in a global validators/  |

---

## ✨ Naming conventions

- `createClientSchema.ts` → for POST payloads
- `updateClientSchema.ts` → for PATCH payloads
- `filterClientSchema.ts` → for query params

---

## 🧠 Example

```ts
// domains/clients/validators/createClientSchema.ts
import { z } from 'zod';

export const CreateClientSchema = z.object({
  name: z.string().min(2),
  email: z.string().email(),
});

export type CreateClientDto = z.infer<typeof CreateClientSchema>;
```

---

## ✅ Summary

- This folder scopes validation to a single domain
- Encourages reusable, typed, and secure data handling
- Keeps validation logic close to the feature that uses it