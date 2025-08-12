# 🧠 domain/repositories/ (clients domain)

This folder contains **repository interfaces** for the `clients` domain.  

A repository acts as an **abstraction over the persistence layer**, providing a collection-like interface for accessing and managing domain entities.  
It hides the details of data storage (e.g., database, cache, API) from the domain layer, ensuring that **business logic is persistence-agnostic**.

---

## 📁 Example

```
domains/clients/domain/repositories/
└── client.repository.ts
```

---

## ✅ Best practices

- Define repositories as **interfaces** (TypeScript `interface` or `abstract class`).
- Keep them **focused on domain entities**, not database schemas or DTOs.
- Methods should **return and accept domain models**, not raw data.
- Avoid adding framework or ORM-specific logic in the interface definition.
- Let **infrastructure layer** provide the actual implementation (`infrastructure/repositories/`).
- Follow **single responsibility** — one repository per aggregate root.

---

## 🧠 Example

```ts
export interface ClientRepository {
  save(client: Client): Promise<void>
  update(client: Client): Promise<void>
  findById(id: string): Promise<Client | null>
  findByEmail(email: string): Promise<Client | null>
  findAll(query: QueryDto): Promise<ClientList>
  delete(id: string): Promise<void>
}
```