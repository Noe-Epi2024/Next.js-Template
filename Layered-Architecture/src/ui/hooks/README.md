# 🪝 hooks/

This folder contains **custom React hooks** used across the UI.  
Each hook encapsulates reusable logic related to UI state, effects, or data fetching.

Hooks are organized by **functional domain** (e.g., `clients`, `users`) to keep the code modular and scalable.

---

## 📁 Recommended structure

```
hooks/
├── clients/
│   ├── useGetClients.ts
│   └── useCreateClient.ts
├── users/
│   ├── useGetUsers.ts
│   └── useCreateUser.ts
```

---

## ✅ Best practices

| ✅ Do                                    | ❌ Don't                                 |
|-----------------------------------------|------------------------------------------|
| Group hooks by domain                   | Mix all hooks at the root                |
| Use `use` prefix (React convention)     | Break naming convention                  |
| Keep logic modular and testable         | Include business logic or validations    |
| Use composition of hooks if necessary   | Create massive hooks with too many roles |

---

## ✨ Naming conventions

- `useGetClients.ts` – fetch or manage client list
- `useCreateClient.ts` – logic for form state
- `useDebouncedValue.ts` – generic utility hook
- `useIsMobile.ts` – responsive logic

---

## 🧠 Example

```ts
// hooks/clients/useClients.ts

import { useQuery } from '@tanstack/react-query';
import { fetchClients } from '@/ui/services/clients/fetchClients';

export function useClients() {
  const { data, isLoading, error } = useQuery({
    queryKey: ['clients'],
    queryFn: fetchClients,
  });

  return { clients: data ?? [], isLoading, error };
}
```