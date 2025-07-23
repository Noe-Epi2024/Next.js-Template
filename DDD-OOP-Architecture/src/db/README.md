# 🗃️ db/

This folder contains **your database configuration and connection instance** (e.g., Prisma client, Drizzle instance, or raw DB config).

It serves as the single entry point for any database access across your application.

---

## 📁 Recommended structure

```
db/
├── db.ts               # Main Prisma client or DB instance
├── schema.prisma       # (Optional) Prisma schema file
├── seed.ts             # (Optional) Seed script
```

---

## ✅ Best practices

| ✅ Do                                     | ❌ Don't                                  |
|------------------------------------------|-------------------------------------------|
| Use a single shared DB instance          | Create new DB clients in every function   |
| Keep this layer minimal and isolated     | Mix queries or logic into this folder     |
| Export a properly configured client      | Leak config details outside this folder   |
| Use `.env` for connection strings        | Hardcode credentials                      |

---

## ✨ Naming conventions

- `db.ts` – main Prisma or DB client export
- `schema.prisma` – Prisma schema definition
- `seed.ts` – initial data population script (optional)
