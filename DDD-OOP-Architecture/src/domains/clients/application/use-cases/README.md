# 🎯 application/use-cases/ (clients domain)

This folder contains **application services** (use cases) for the `clients` domain.
These services coordinate the execution of business rules using domain entities and infrastructure via interfaces.

They act as the entry point for the domain logic, receiving parsed DTOs and calling domain methods or repositories.

---

## 📁 Example

```
domains/clients/application/use-cases/
├── create-client.use-case.ts
├── update-client.use-case.ts
└── delete-client.use-case.ts
```

---

## ✅ Best practices

- Use cases are **classes** (OOP)
- Use constructor injection for `ClientRepository` (via interface)
- Keep orchestration logic here — not in controllers

---

## 🧠 Example

```ts
export class CreateClientUseCase {
  constructor(private readonly clientRepository: ClientRepository) {}

  async execute(dto: CreateClientDto) {
    const client = new Client(dto.name, dto.email);
    return this.clientRepository.save(client);
  }
}
```