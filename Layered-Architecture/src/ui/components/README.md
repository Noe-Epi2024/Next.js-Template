# 🧩 components/

This folder contains all **React UI components** used across the application.

They are organized by **functional domain** (e.g., clients, users, dashboard) to ensure clarity, modularity, and scalability.

---

## 📁 Recommended structure

```
components/
├── clients/
│   ├── ClientCard.tsx
│   └── ClientList.tsx
├── users/
│   ├── UserBadge.tsx
│   └── UserList.tsx
```

---

## ✅ Best practices

| ✅ Do                                      | ❌ Don't                                |
|-------------------------------------------|-----------------------------------------|
| Organize components **by domain**         | Put everything at the root              |
| Keep components **UI-only and stateless** | Fetch data inside components            |
| Split by purpose: `Card`, `List`, `Form`  | Create bloated single-file components   |
| Use typed `props` interfaces              | Mix logic and rendering responsibilities|

---

## ✨ Naming conventions

- `ClientCard.tsx` – displays a single entity
- `ClientList.tsx` – renders a list of entities
- `ClientForm.tsx` – create or edit form
- `ClientDetails.tsx` – detailed view
- `ClientCreateDialog.tsx` – modal dialog for creation

---

## 🧠 Example

```tsx
// components/clients/ClientCard.tsx

type Props = {
  name: string;
  email: string;
};

export function ClientCard({ name, email }: Props) {
  return (
    <div className="p-4 border rounded">
      <h2 className="font-semibold">{name}</h2>
      <p>{email}</p>
    </div>
  );
}
```