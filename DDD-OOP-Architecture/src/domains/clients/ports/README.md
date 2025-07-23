# 🔌 ports/ (clients domain)

This folder defines **interfaces (ports)** used by the application layer.  
They represent contracts for infrastructure or service dependencies (e.g., repository, mailer).

---

## 📁 Example

```
domains/clients/ports/
└── ClientRepository.ts
```

---

## ✅ Best practices

- Keep one interface per concern
- Let application layer depend only on interfaces
- Infrastructure must implement them

---

## 🧠 Example

```ts
export interface ClientRepository {
  save(client: Client): Promise<Client>;
  findById(id: string): Promise<Client | null>;
}
```