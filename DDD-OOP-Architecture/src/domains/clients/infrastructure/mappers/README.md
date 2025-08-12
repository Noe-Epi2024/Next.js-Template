# 🏗️ infrastructure/mappers/ (clients domain)

This folder contains **mapper classes** responsible for converting data between different representations:
- **Domain models** ↔ **Database entities** (e.g., Prisma, Drizzle models)
- **Domain models** ↔ **DTOs** (Data Transfer Objects) for the application or API layers

Mappers help maintain a **clear separation** between the domain layer and infrastructure or presentation concerns.

---

## 📁 Example

```
domains/clients/infrastructure/mappers/
└── client.mapper.ts
```

---

## ✅ Best practices

- Always map **to and from** the domain model — the domain should never handle raw DB records or DTOs directly.
- Keep mapping logic **stateless** and encapsulated in dedicated classes or static methods.
- Do not add business logic here — mappers should only transform data formats.
- Use clear, explicit method names: `toDomain`, `toDto`, `toCreatePrisma`, `toUpdatePrisma`, etc.
- Ensure all fields are mapped consistently to avoid data loss or mismatches.
- Keep mappers close to their related domain (e.g., `clients` domain mappers stay in `clients/infrastructure/mappers`).

---

## 🧠 Example

```ts
export class ClientMapper {
  static toDomain(raw: PrismaClient): Client {
    return new Client(
      raw.id,
      raw.name,
      raw.email,
      raw.status as ClientStatus,
      raw.createdAt,
    )
  }

  static toCreatePrisma(client: Client) {
    return {
      id: client.id,
      name: client.name,
      email: client.email,
      status: client.status,
    }
  }

  static toUpdatePrisma(client: Client): Partial<PrismaClient> {
    return {
      name: client.name,
      status: client.status,
    }
  }

  static toDto(client: Client): ClientDto {
    return {
      id: client.id,
      name: client.name,
      email: client.email,
      status: client.status,
      createdAt: client.createdAt,
    }
  }
}
```