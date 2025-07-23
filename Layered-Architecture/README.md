# 🧱 Layered Architecture (Next.js Template)

This template implements a clean and functional **Layered Architecture** with Next.js, organized by **technical responsibility**:  
UI → Controller → Repository → DB.

It provides a simple yet scalable structure that separates **data flow**, **UI concerns**, and **business rules** cleanly.

---

## 📁 Project Structure

```
src/
├── app/                     # Next.js routing (App Router + API)
│   └── api/clients/         # Route handlers (e.g. route.ts)
├── controllers/             # Orchestrates flow: validation + repo call
├── repositories/            # DB logic (Prisma, SQL, etc.)
├── db/                      # Prisma client or DB layer
├── services/ (optional)     # Complex composition logic (if needed)
├── middlewares/             # Middleware utils (e.g. withAuth)
├── errors/                  # Custom error types
├── types/                   # Global types and interfaces
├── ui/                      # UI layer: components, hooks, fetchers
│   ├── components/
│   ├── hooks/
│   └── services/
├── utils/                   # Generic helper functions
├── validators/              # Zod schemas + DTOs
└── styles/                  # Tailwind global styles
```

---

## ✅ Key Characteristics

| ✅ Feature                        | 💬 Description                            |
|----------------------------------|-------------------------------------------|
| Clear layer separation           | UI, controller, data access               |
| No OOP overhead                  | Functional, testable code                 |
| Validation in controllers        | Uses Zod for safe input parsing           |
| Lightweight and pragmatic        | Easy to onboard, ideal for solo/dev teams|
| Full SSR/CSR support             | Built for Next.js App Router              |

---

## 🧠 Data Flow

```
[Client UI] 
   ↓
[useCreateClient] → [createClient service (ui)] 
   ↓
[app/api/clients/route.ts] → [controller] 
   ↓
[validator] → [repository] 
   ↓
[DB]
```

---

## 🧩 Example (Client Feature)

```
controllers/
└── createClientController.ts

repositories/
└── clients/
    └── createClient.ts

validators/
└── clientValidator.ts

ui/
├── hooks/
│   └── useCreateClient.ts
├── services/
│   └── createClient.ts
└── components/
    └── ClientForm.tsx
```

---

## ⚙️ Tech Stack

- ✅ Next.js (App Router)
- ✅ TypeScript
- ✅ Tailwind CSS
- ✅ Zod
- ✅ Prisma
- ✅ React Query (optional in UI hooks)

---

## ✅ Summary

This template is perfect for:
- Small to medium full-stack applications
- Teams who prefer simplicity over abstraction
- Projects with evolving business logic that may later grow into DDD

You can easily scale this into a domain-driven system later by isolating folders per domain.