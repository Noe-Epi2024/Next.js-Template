# 📦 application/dto/ (clients domain)

This folder contains **Zod schemas** and **DTO types** for the `clients` domain.

DTOs are used to validate and type data exchanged between layers: controllers → services → repositories.

---

## 📁 Example

```
domains/clients/application/dto/
└── createClient.dto.ts
```

---

## ✅ Best practices

- Use `z.object()` to define input structure
- Export both schema and inferred type

---

## 🧠 Example

```ts
import { z } from 'zod';

export const CreateClientSchemaDto = z.object({
  name: z.string().min(2),
  email: z.string().email(),
});

export type CreateClientDto = z.infer<typeof CreateClientSchemaDto>;
```