# 🧠 domain/ (clients domain)

This folder defines the **core business logic** of the `clients` domain.  
It includes **entities**, **value objects**, and **aggregates** that encapsulate domain rules.

These are pure classes, decoupled from any framework or infrastructure.

---

## 📁 Example

```
domains/clients/domain/
└── Client.ts
```

---

## ✅ Best practices

- Use **constructors**, **methods**, and **invariants**
- Keep logic encapsulated in the entity
- Do **not** access DB or APIs directly here

---

## 🧠 Example

```ts
export class Client {
  constructor(
    public readonly id: string,
    public name: string,
    public email: string
  ) {}

  rename(newName: string) {
    if (newName.length < 2) throw new Error("Name too short");
    this.name = newName;
  }
}
```