# 🗃️ store/ (clients domain)

This folder contains all **client-side state management** related to the `clients` domain.  
It’s typically implemented using tools like **Zustand**, **Jotai**, or **Redux**, and is scoped to a specific feature.

---

## 📁 Typical structure

```
domains/
└── clients/
    └── store/
        ├── clientFormStore.ts       # Form state (create/edit)
        ├── clientFilterStore.ts     # Filters, search, sort
        └── clientSelectionStore.ts  # Selection or active row state
```

---

## ✅ Best practices

| ✅ Do                                        | ❌ Don't                                     |
|---------------------------------------------|----------------------------------------------|
| Keep store logic **feature-scoped**         | Use global/globalState for all domains       |
| Export `useXXXStore()` hooks                | Expose internal state objects directly       |
| Initialize state with default values        | Leave undefined/null state                   |
| Use separate stores for separate concerns   | Cram all state into one monolithic store     |

---

## ✨ Naming conventions

- `clientFormStore.ts` – for create/edit form values
- `clientFilterStore.ts` – for search/filter/sort state
- `clientReadStore.ts` – for current entity details
- `clientSelectionStore.ts` – for selected IDs

---

## 🧠 Example

```ts
// store/clientFormStore.ts

import { create } from 'zustand';

type State = {
  name: string;
  email: string;
  setName: (name: string) => void;
  setEmail: (email: string) => void;
};

export const useClientFormStore = create<State>((set) => ({
  name: '',
  email: '',
  setName: (name) => set({ name }),
  setEmail: (email) => set({ email }),
}));
```

---

## ✅ Summary

- Keeps UI state local to the domain
- Promotes composability and testability
- Avoids central/global state complexity