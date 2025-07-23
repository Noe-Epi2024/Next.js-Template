# 🧠 hooks/clients/

This folder contains **custom React hooks** related to the `clients` domain.  
They typically wrap logic from `services/clients/` and manage data fetching, mutation, or derived state.

---

## 📁 Example

```
ui/hooks/clients/
├── useClients.ts
├── useCreateClient.ts
└── useUpdateClient.ts
```

---

## ✅ Best practices

- Use `react-query` or `swr` inside hooks
- Use naming like `useCreateClient`, `useClients`
- Keep hooks focused and reusable
- Co-locate hooks by feature

---

## 🧠 Example

```ts
import { useQuery } from '@tanstack/react-query';
import { fetchClients } from '@/ui/services/clients/fetchClients';

export function useClients() {
  return useQuery(['clients'], fetchClients);
}
```