# 🧩 components/ (clients domain)

This folder contains all **React UI components** that belong to the `clients` domain.

They are responsible for rendering client-related UIs (forms, lists, cards, dialogs...) and are kept close to the logic and styles that use them.

---

## 📁 Typical structure

```
domains/
└── clients/
    └── components/
        ├── ClientCard.tsx
        ├── ClientList.tsx
        ├── ClientForm.tsx
        ├── ClientDetails.tsx
        └── ClientCreateDialog.tsx
```

---

## ✅ Best practices

| ✅ Do                                       | ❌ Don't                                 |
|--------------------------------------------|------------------------------------------|
| Keep components presentational (UI only)   | Fetch data inside components             |
| Use typed props                            | Use implicit or `any`                    |
| Structure components by purpose            | Mix all UI into one large component      |
| Co-locate with domain logic and hooks      | Scatter components in a global folder    |

---

## ✨ Naming conventions

- `ClientCard.tsx` – renders a single client
- `ClientList.tsx` – renders a list of clients
- `ClientForm.tsx` – for create/edit forms
- `ClientDetails.tsx` – detailed view of a client
- `ClientCreateDialog.tsx` – modal dialog for client creation

---

## 🧠 Example

```tsx
// components/ClientCard.tsx

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

---

## ✅ Summary

- Scoped UI components per feature
- Simple, focused, and reusable
- Follows domain encapsulation principles