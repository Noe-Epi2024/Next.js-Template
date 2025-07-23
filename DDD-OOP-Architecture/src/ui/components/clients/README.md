# 🧩 components/clients/

This folder contains all **React UI components** related to the `clients` domain.  
These components are presentational and reused throughout the client UI (cards, lists, forms, dialogs…).

---

## 📁 Example

```
ui/components/clients/
├── ClientCard.tsx
├── ClientList.tsx
└── ClientForm.tsx
```

---

## ✅ Best practices

- Keep components **UI-only**
- Use typed `props`
- Avoid direct fetch or business logic
- Use domain-specific naming (`ClientForm`, not `Form`)

---

## 🧠 Example

```tsx
type Props = {
  name: string;
  email: string;
};

export function ClientCard({ name, email }: Props) {
  return (
    <div className="p-4 border rounded">
      <h2>{name}</h2>
      <p>{email}</p>
    </div>
  );
}
```