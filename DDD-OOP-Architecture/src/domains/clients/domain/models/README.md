# 🧠 domain/models/ (clients domain)

This folder contains **domain models** — the core business objects of the `clients` domain.  

A **model** represents a real-world entity or concept in your business and encapsulates both **data** and **behavior**.  
Models enforce **business rules**, **invariants**, and **state transitions** directly within the domain layer.

---

## 📁 Example

```
domains/clients/domain/models/
└── client.ts
```

---

## ✅ Best practices

- Represent **real business concepts** from the ubiquitous language of the domain.
- Keep models **pure**: no database calls, HTTP requests, or framework-specific logic.
- Use **private properties** with getters/setters or methods to enforce invariants.
- Encapsulate **state changes** inside model methods (e.g., `activate()`, `suspend()`).
- Favor **immutability** where possible, but allow controlled mutations when required by business rules.
- Unit test models in isolation — they should work without any infrastructure dependencies.

---

## 🧠 Example

```ts
export class Client {
  constructor(
    private readonly _id: string,
    private _name: string,
    private readonly _email: string,
    private _status: ClientStatus,
    private readonly _createdAt: Date,
  ) {}

  // Getters
  get id(): string {
    return this._id
  }

  get name(): string {
    return this._name
  }

  get email(): string {
    return this._email
  }

  get status(): ClientStatus {
    return this._status
  }

  get createdAt(): Date {
    return this._createdAt
  }

  // Methods
  isActive(): boolean {
    return this._status === ClientStatus.ACTIVE
  }

  isInactive(): boolean {
    return this._status === ClientStatus.INACTIVE
  }

  isSuspended(): boolean {
    return this._status === ClientStatus.SUSPENDED
  }

  // Actions
  suspend(): void {
    this._status = ClientStatus.SUSPENDED
  }

  activate(): void {
    this._status = ClientStatus.ACTIVE
  }

  deactivate(): void {
    this._status = ClientStatus.INACTIVE
  }
}
```