# 🧩 Feature-Sliced Design (FSD) Architecture (Next.js Template)

This template follows the **Feature-Sliced Design (FSD)** approach to structure your Next.js full-stack application.  
It organizes your codebase by **features (domains)** instead of technical layers, allowing strong encapsulation and modularity.

---

## 📁 Project Structure

```
src/
├── app/                           # Next.js routing (App Router + API)
├── controllers/                   # Request orchestration per domain
├── domains/
│   │── clients/
│   │   ├── api/                   # Fetchers to call backend
│   │   ├── application/           # Custom hooks (e.g. React Query)
│   │   ├── components/            # UI for this domain only
│   │   ├── infrastructure/        # DB access (e.g. Prisma)
│   │   ├── store/                 # Zustand stores for this feature
│   │   ├── types/                 # DTOs and shared types
│   │   ├── utils/                 # Local helpers
│   │   └── validators/            # Zod schemas
│   └── shared/
│       ├── components/            # Global UI
│       ├── hooks/                 #Global hooks
│       ├── types/                 #Global types
│       └── utils/                 #Global helpers
├── db/                            # DB instance
├── middlewares/                   # Middlewares (e.g. auth)
├── errors/                        # Custom errors
└── validators/                    # Global Zod parsing helpers
```

---

## ✅ Key Principles

| ✅ Principle                    | 💬 Description                                 |
|--------------------------------|------------------------------------------------|
| Feature-first structure        | Group code by feature/domain                   |
| Locality and encapsulation     | Each domain owns its logic/UI/state            |
| Zod for validation             | Safe DTOs across layers                        |
| Stateless reusable UI          | Presentational components + hooks              |
| Minimal boilerplate            | No unnecessary abstractions                    |

---

## 🧠 Data Flow

```
[components] 
   ↓
[application hooks] → [api/fetchers]
   ↓
[Next.js route handler (app/api)]
   ↓
[controller] → [validator] → [infrastructure] → [DB]
```

---

## 🧩 Example (Client Feature)

```
domains/clients/
├── api/
│   └── fetchClients.ts
├── application/
│   └── useClients.ts
├── components/
│   └── ClientList.tsx
├── infrastructure/
│   └── getClients.ts
├── store/
│   └── clientFilterStore.ts
├── types/
│   └── client.ts
├── utils/
│   └── formatClient.ts
└── validators/
    └── clientValidator.ts
```

---

## ⚙️ Tech Stack

- ✅ Next.js (App Router)
- ✅ TypeScript
- ✅ Tailwind CSS
- ✅ Zod
- ✅ Prisma
- ✅ Zustand (store)
- ✅ React Query

---

## ✅ Summary

This template is ideal for:
- Mid-to-large projects needing scalability
- Multi-feature applications (dashboard, SaaS, CRM)
- Developer teams working in parallel
- Clean modular separation by business features

Fork it and adapt per domain. Built to grow.