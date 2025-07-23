# 🏗️ infrastructure/ (clients domain)

This folder contains **concrete implementations** of ports (interfaces), such as repository classes using Prisma.

These classes should match the interfaces defined in `ports/` and encapsulate all DB or external service access.

---

## 📁 Example

```
domains/clients/infrastructure/
└── ClientRepositoryPrisma.ts
```

---

## ✅ Best practices

- Implements a port (e.g., `ClientRepository`)
- Uses Prisma or any adapter internally
- No business logic here — only technical implementation

---

## 🧠 Example

```ts
export class ClientRepositoryPrisma implements ClientRepository {
  async save(client: Client): Promise<Client> {
    return prisma.client.create({ data: client });
  }
}
```