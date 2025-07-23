# 🧱 DDD + OOP Architecture (Next.js Template)

This template applies **Domain-Driven Design (DDD)** combined with **Object-Oriented Programming (OOP)** to a full-stack Next.js application.

It separates responsibilities by **business context** and **layer**, ensuring high modularity, reusability, and testability.

---

## 📁 Project Structure

```
src/
├── app/                         # Next.js routes (App Router)
├── controllers/                 # Bridge between API and Application
├── domains/
│   └── clients/
│       ├── application/         # Use cases (services, commands)
│       ├── domain/              # Entities, value objects, aggregates
│       ├── dto/                 # Input schemas (Zod) + DTO types
│       ├── infrastructure/      # Database and adapter implementations
│       └── ports/               # Repository and service interfaces
├── ui/
│   ├── components/              # React UI components
│   ├── hooks/                   # Custom UI hooks
│   └── services/                # Client-side API fetchers
├── db/                          # Prisma client or DB layer
├── middlewares/                # Request middlewares
├── errors/                      # Custom errors
├── types/                       # Shared TypeScript types
├── utils/                       # Pure utility functions
└── validators/                  # Reusable Zod parsers/helpers
```

---

## 🧠 Core Principles

| ✅ Principle                    | 💬 Description                                            |
|--------------------------------|-----------------------------------------------------------|
| Domain-Driven Design (DDD)     | Organize code by bounded contexts                         |
| Object-Oriented Programming    | Use classes to model business logic and behavior          |
| Layered Architecture           | Separate domain, app, infra, and UI layers cleanly        |
| Dependency Inversion           | Domain depends on interfaces, not implementations         |
| Strict encapsulation           | Each domain is isolated, self-contained, and scalable     |

---

## 🎯 Ideal For

- Large-scale backend/frontend projects
- Complex business logic and flows
- Systems requiring extensibility, testing, and reuse
- Apps with API + UI layers (Next.js full-stack)

---

## 🧩 Example (Client Feature)

```
domains/clients/
├── application/
│   └── CreateClientService.ts
├── domain/
│   └── Client.ts
├── dto/
│   └── CreateClientDto.ts
├── infrastructure/
│   └── PrismaClientRepository.ts
└── ports/
    └── ClientRepository.ts
```

---

## ✅ Flow Overview

```
[Request] → Controller
          → Zod Schema (DTO)
          → Application Service (Use Case)
          → Domain (Entity Logic)
          → Repository (Interface → Implementation)
          → DB
```

---

## 🚀 Technologies Used

- **Next.js App Router**
- **TypeScript**
- **Zod** for schema validation
- **Prisma** for database access
- **OOP** patterns with DDD layers

---

## 📌 Notes

- Each domain is completely isolated
- Class-based services and entities
- Interfaces (ports) enable testability and clean dependency injection
- UI is kept decoupled from business logic

---

Feel free to fork and scale this template for production-grade SaaS, B2B platforms, or enterprise projects.